# Travel plans

เว็บแผนเที่ยวส่วนตัว เปิดดูบนมือถือได้ ใช้ GitHub Pages เป็นโฮสต์ ไม่มี build step

## ทริปที่มี

| ทริป | วันที่ | ลิงก์ |
|------|--------|-------|
| Rayong | 30 ธ.ค. 2026 – 1 ม.ค. 2027 | https://st-nann.github.io/travel/2026/Rayong/ |

## โครงสร้าง

```
travel/
├── README.md
├── .claude/
│   └── skill/
│       └── plan.md          # วิธีสร้าง/อัปเดตหน้าแผนทริปจาก Google Sheet (ใช้กับ Claude)
└── 2026/
    └── Rayong/
        └── index.html       # หน้าเว็บไฟล์เดียว (HTML + CSS ในไฟล์)
```

URL ของแต่ละทริปคือ `https://st-nann.github.io/travel/<ปี>/<ชื่อโฟลเดอร์>/` (ตัวพิมพ์เล็กใหญ่ต้องตรงกับชื่อโฟลเดอร์)

## หน้าเว็บมีอะไร

- ข้อมูลจากแท็บ `Plan (new) - dd.mm.yyyy` ของชีต
- ไทม์ไลน์ Day 1 / Day 2 / Day 3 พร้อมปุ่มสลับวันค้างด้านบน
- เวลาเปิด-ปิด เมนูแนะนำ เบอร์โทร (กดโทรได้)
- ลิงก์ **Reference / Review** (TikTok, Instagram, Facebook, Lemon8)
- ฟอนต์ Prompt (ไทยไม่มีหัว) จาก Google Fonts รองรับโหมดมืด

## อัปเดตแผนหลังแก้ชีต

### วิธีที่ 1: ให้ Claude Code ทำ
1. เปิด `claude` ในโฟลเดอร์ `travel`
2. วางไฟล์ชีตล่าสุด (ส่งออกเป็น CSV/ข้อความ) ไว้ในโฟลเดอร์ (ใช้แท็บ `Plan (new) - dd.mm.yyyy` ที่วันที่ใหม่สุด)
3. สั่ง: `ทำตาม .claude/skill/plan.md สร้าง index.html จากชีตล่าสุด แล้ว commit และ push`
4. ตรวจสิ่งที่เปลี่ยนแล้วกดยืนยัน

### วิธีที่ 2: ทำเอง
```bash
cp ~/Downloads/index.html 2026/Rayong/index.html
git add 2026/Rayong/index.html
git commit -m "update Rayong plan"
git push origin main
```
หรืออัปโหลดผ่านเว็บ GitHub: เปิดโฟลเดอร์ทริป → **Add file → Upload files** → **Commit changes**

รอ 1-2 นาทีหลัง push แล้วรีเฟรชหน้าเว็บแบบแรงๆ

## เปิด GitHub Pages (ทำครั้งเดียว)

วิธีนี้ทำผ่านเว็บ GitHub ได้เลย ไม่ต้องใช้คำสั่งหรือโปรแกรมเพิ่ม

1. เปิดหน้า repository ที่ https://github.com/st-nann/travel แล้วเช็กว่าตั้งเป็น **Public** (บัญชีฟรีต้องเป็น Public ถึงเปิดเว็บได้)
2. กดแท็บ **Settings** ของ repository แล้วเลือกเมนู **Pages** ทางซ้ายมือ
3. ตรง **Source** เลือก **Deploy from a branch**
4. ตรง **Branch** เลือก **main** โฟลเดอร์ **/ (root)** แล้วกด **Save**
5. รอประมาณ 1-2 นาที แล้วรีเฟรชหน้า Pages จะขึ้นลิงก์ `https://st-nann.github.io/travel/`

ลิงก์ของแต่ละทริปคือ `https://st-nann.github.io/travel/<ปี>/<ชื่อโฟลเดอร์>/` เช่น https://st-nann.github.io/travel/2026/Rayong/ ส่งเข้า LINE ได้เลย ใครก็เปิดได้ ไม่ต้องมีบัญชีอะไร

**ข้อควรรู้**
- repository ต้องเป็น Public หน้าเว็บจึงเปิดได้ คนที่รู้ลิงก์เข้าดูได้ และชื่อบัญชี GitHub ของคุณจะอยู่ในลิงก์
- ชื่อโฟลเดอร์ในลิงก์ต้องตรงตัวพิมพ์เล็กใหญ่ เช่น `Rayong` ขึ้นต้นด้วย R ใหญ่
- เมนูใน GitHub อาจต่างจากที่เขียนไว้เล็กน้อย ถ้าไม่เจอเมนู Pages ให้เช็กว่าเข้าแท็บ **Settings** ของ repository ถูกตัว
- ถ้าเปิดลิงก์แล้วขึ้น 404 ให้รอสักครู่แล้วรีเฟรช และดูที่แท็บ **Actions** ว่างาน "pages build and deployment" ขึ้นเครื่องหมายถูกสีเขียวหรือยัง
- ถ้าแก้แผนทีหลัง ให้อัปโหลดหรือ push ไฟล์ `index.html` ใหม่ทับ ลิงก์เดิมจะอัปเดตเอง

## เพิ่มทริปใหม่

สร้างโฟลเดอร์ `<ปี>/<ชื่อทริป>/` ใส่ `index.html` แล้วเพิ่มแถวในตารางด้านบน
