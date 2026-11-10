# n8n Sales Record

Workflow สำหรับบันทึกยอดขายจาก LINE ลง Google Sheets และส่งรายงานยอดขายกลับทาง LINE คำนวณยอดรายรายการและยอดรายงานใน n8n

1. Import `Daily Sales Report.json` เข้า n8n
2. สร้างชีต `เมนู` (รหัสเมนู, ชื่อเมนู, ราคา), `พนักงาน` (LINE User ID, ชื่อพนักงาน, สถานะ) และ `รายการขาย` (ใช้ชื่อคอลัมน์ตามการตั้งค่าใน node Append row in sheet)
3. เลือก Spreadsheet และแท็บที่ตรงกันใน Google Sheets nodes แล้วเชื่อม Google Sheets OAuth2 credential ใน n8n
4. ตั้ง Crypto credential ด้วย LINE Channel Secret เพื่อยืนยันลายเซ็น webhook และ Header Auth credential ด้วย LINE Channel Access Token สำหรับ HTTP Request nodes
5. แทน `YOUR_LINE_REPORT_RECIPIENT_ID` ใน Code in JavaScript ด้วย LINE User ID ของผู้รับรายงานตามเวลา จากนั้นตั้ง Production Webhook URL ใน LINE Developers และ publish เมื่อพร้อม

ตัวอย่างคำสั่ง LINE: `ชาไทย 2 เงินสด` และ `ยอดขายวันนี้`
