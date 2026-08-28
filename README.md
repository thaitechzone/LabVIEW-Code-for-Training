# LabVIEW Code for Training

รวมโค้ดตัวอย่างและเทมเพลต LabVIEW สำหรับใช้สอน/ฝึกฝนการเขียนโปรแกรมด้วย LabVIEW ครอบคลุมทั้งสถาปัตยกรรม State Machine พื้นฐาน และงานด้าน Machine Vision (NI Vision Development Module / Vision Assistant) สำหรับงานตรวจสอบชิ้นงานด้วยกล้อง (Inspection)

## โครงสร้างโปรเจกต์

```
LabVIEW Code for Training/
├── Project Inspection Clamp/              # ตัวอย่างงาน Machine Vision วัดขนาดด้วย Clamp
├── Project01 LabVIEW Template  StateMachine Basic/   # เทมเพลต State Machine แบบพื้นฐาน
├── Project02 LabVIEW Template EVENT StateMachine/    # เทมเพลต State Machine แบบ Event-Driven
├── Shared File (SubVI)/                   # SubVI ที่ใช้ร่วมกันระหว่างโปรเจกต์เทมเพลต
├── QueuePresentation1.pptx                # สไลด์ประกอบการสอนเรื่อง Queue
└── TempateEvent State Machine .pptx       # สไลด์ประกอบการสอนเรื่อง Event State Machine
```

## รายละเอียดแต่ละโปรเจกต์

### 1. Project Inspection Clamp

ตัวอย่างงาน Machine Vision สำหรับตรวจวัดขนาด/ตำแหน่งชิ้นงาน (กรณีศึกษา: แบตเตอรี่) ด้วยฟังก์ชัน **Clamp** ของ NI Vision Development Module

- `Inspection Clamp Project1.lvproj` — LabVIEW Project (พัฒนาด้วย **LabVIEW 2021 (21.0)**)
- `main-inspection-project1.vi` — VI หลักของการตรวจวัด
- `StateVariable.ctl` — Type Def สำหรับตัวแปรสถานะ
- `Images/Battery/` — ชุดภาพตัวอย่างแบตเตอรี่ (Image00–Image16.jpg) สำหรับทดสอบอัลกอริทึม
- `Images/template/` — ภาพเทมเพลตสำหรับ Pattern Matching
- `myFileInspection.txt` — ไฟล์ log ผลการตรวจวัด (PartNo, DateTime, Clamp, Main, Top, Bottom, Pass/Fail)

**Vision function ที่ใช้:** IMAQ Create/ReadFile/Copy, IMAQ Pattern Match, Clamp (Overlay Results, Separate ROI), Edge Detection เป็นหลัก — ต้องติดตั้ง **NI Vision Development Module** จึงจะเปิดโปรเจกต์และรันได้ครบ

### 2. Project01 LabVIEW Template — StateMachine Basic

เทมเพลตโครงสร้าง **State Machine พื้นฐาน** (ใช้ While Loop + Case Structure + Shift Register) พัฒนาด้วย **LabVIEW 2025 (25.0)**

- `main.vi` — VI หลักของ State Machine
- `StateVariable.ctl` — Enum กำหนดรายการ State
- `AcuiredDataRandom_SubVI.vi` — จำลองการอ่านค่าข้อมูล (Random)
- `DisableEnable.vi` — ตัวอย่างการ enable/disable ควบคุม UI
- `LV_SQL_DataLogger.lvlps` — ตัวอย่างการบันทึกข้อมูลลงฐานข้อมูล SQL

### 3. Project02 LabVIEW Template — EVENT StateMachine

ต่อยอดจาก Project01 โดยปรับให้เป็น **Event-Driven State Machine** (เพิ่ม Event Structure เพื่อจัดการ User Interface Event) พัฒนาด้วย **LabVIEW 2025 (25.0)** มีไฟล์ประกอบเช่นเดียวกับ Project01

### 4. Shared File (SubVI)

SubVI ตัวอย่างที่ใช้ประกอบการสอนและถูกเรียกใช้ร่วมกันในหลายโปรเจกต์:

| ไฟล์ | หน้าที่ |
|---|---|
| `AcuiredDataRandom_SubVI.vi` | จำลองการรับข้อมูลแบบสุ่ม |
| `Convert C to F.vi` | แปลงหน่วยอุณหภูมิ องศาเซลเซียส → ฟาเรนไฮต์ |
| `DisableEnable.vi` | ตัวอย่างการควบคุมสถานะ enable/disable ของ Control |
| `Read Voltage.vi` | จำลอง/อ่านค่าแรงดันไฟฟ้า |
| `Thermometer.vi`, `Thermometer (Demo).vi` | ตัวอย่างการอ่านและแสดงผลอุณหภูมิ |

### 5. ไฟล์ประกอบการสอน (Slides)

- `QueuePresentation1.pptx` — สไลด์อธิบายแนวคิด Queue ใน LabVIEW
- `TempateEvent State Machine .pptx` — สไลด์อธิบายแนวคิด Event State Machine

## ความต้องการของระบบ (Requirements)

- **LabVIEW 2025 (25.0)** — สำหรับเปิดโปรเจกต์เทมเพลต State Machine (Project01, Project02)
- **LabVIEW 2021 (21.0)** ขึ้นไป พร้อม **NI Vision Development Module** และ **Vision Assistant** — สำหรับเปิดโปรเจกต์ `Project Inspection Clamp`
- ระบบปฏิบัติการ Windows (แนะนำให้ตรงกับเวอร์ชัน LabVIEW ที่ใช้พัฒนาไฟล์)

> หมายเหตุ: หากเปิดไฟล์ด้วย LabVIEW เวอร์ชันที่ต่ำกว่าที่ระบุไว้ โปรแกรมจะไม่สามารถเปิดไฟล์ได้ หรือหากเปิดด้วยเวอร์ชันที่สูงกว่า LabVIEW จะทำการแปลง (convert) ไฟล์ให้อัตโนมัติ

## วิธีเริ่มต้นใช้งาน

1. Clone หรือดาวน์โหลดโปรเจกต์นี้มาไว้ในเครื่อง
2. เปิดไฟล์ `.lvproj` ของโปรเจกต์ที่ต้องการศึกษาด้วย LabVIEW
3. สำหรับ `Project Inspection Clamp` ให้ตรวจสอบว่าติดตั้ง Vision Development Module แล้ว มิฉะนั้น dependency ของ VI ที่เรียกใช้ฟังก์ชัน IMAQ/Clamp จะขึ้นสถานะ broken (ไอคอนกากบาท)
4. รัน VI หลัก (`main.vi` หรือ `main-inspection-project1.vi`) เพื่อดูการทำงาน

## วัตถุประสงค์

รีโพนี้จัดทำขึ้นเพื่อใช้เป็นสื่อการสอน/แบบฝึกหัดสำหรับผู้เริ่มต้นและผู้ที่ต้องการฝึกฝนแนวทางการออกแบบโปรแกรมด้วย LabVIEW ทั้งในแง่สถาปัตยกรรมซอฟต์แวร์ (State Machine, Event-Driven) และการประยุกต์ใช้งานด้าน Machine Vision ในอุตสาหกรรม (Inspection/Measurement)
