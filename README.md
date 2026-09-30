# fall-risk-assessment-
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <title>ประเมินความเสี่ยง Fall Risk</title>
    <style>
        body { font-family: sans-serif; padding: 20px; max-width: 600px; margin: auto; background-color: #f4f7f6; }
        .card { background: white; padding: 20px; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.1); }
        h2 { color: #2c3e50; text-align: center; }
        .question { margin-bottom: 15px; }
        label { display: block; font-weight: bold; margin-bottom: 5px; }
        select { width: 100%; padding: 8px; border-radius: 4px; border: 1px solid #ccc; }
        button { width: 100%; padding: 10px; background-color: #27ae60; color: white; border: none; border-radius: 4px; font-size: 16px; cursor: pointer; margin-top: 15px; }
        button:hover { background-color: #219150; }
        #result { margin-top: 20px; padding: 15px; border-radius: 5px; display: none; text-align: center; font-size: 18px; font-weight: bold; }
    </style>
</head>
<body>

<div class="card">
    <h2>แบบประเมินความเสี่ยงต่อการตกหกล้ม (MFS)</h2>
    
    <div class="question">
        <label>1. ประวัติการตกหกล้ม (ในช่วง 3 เดือน):</label>
        <select id="q1">
            <option value="0">ไม่มี (0 คะแนน)</option>
            <option value="25">มี (25 คะแนน)</option>
        </select>
    </div>

    <div class="question">
        <label>2. การวินิจฉัยโรคมากกว่า 1 โรค:</label>
        <select id="q2">
            <option value="0">ไม่มี (0 คะแนน)</option>
            <option value="15">มี (15 คะแนน)</option>
        </select>
    </div>

    <div class="question">
        <label>3. การใช้อุปกรณ์ช่วยเดิน:</label>
        <select id="q3">
            <option value="0">ไม่ใช้ / นอนเตียง / ใช้รถเข็น (0 คะแนน)</option>
            <option value="15">ใช้ไม้เท้า / วอล์คเกอร์ / ไม้ค้ำยัน (15 คะแนน)</option>
            <option value="30">เกาะเฟอร์นิเจอร์เดิน (30 คะแนน)</option>
        </select>
    </div>

    <div class="question">
        <label>4. มีการให้สารน้ำทางหลอดเลือดดำ (IV/Heparin Lock):</label>
        <select id="q4">
            <option value="0">ไม่มี (0 คะแนน)</option>
            <option value="20">มี (20 คะแนน)</option>
        </select>
    </div>

    <div class="question">
        <label>5. ลักษณะการเดินและการทรงตัว:</label>
        <select id="q5">
            <option value="0">ปกติ / นอนเตียง (0 คะแนน)</option>
            <option value="10">อ่อนแรง (10 คะแนน)</option>
            <option value="20">บกพร่องอย่างมาก/ทรงตัวยาก (20 คะแนน)</option>
        </select>
    </div>

    <div class="question">
        <label>6. สภาพจิตใจ / การรับรู้:</label>
        <select id="q6">
            <option value="0">รู้ข้อจำกัดของตนเอง (0 คะแนน)</option>
            <option value="15">สับสน / ประเมินความสามารถสูงเกินจริง (15 คะแนน)</option>
        </select>
    </div>

    <button onclick="calculateRisk()">คำนวณระดับความเสี่ยง</button>

    <div id="result"></div>
</div>

<script>
function calculateRisk() {
    let score = Number(document.getElementById('q1').value) +
                Number(document.getElementById('q2').value) +
                Number(document.getElementById('q3').value) +
                Number(document.getElementById('q4').value) +
                Number(document.getElementById('q5').value) +
                Number(document.getElementById('q6').value);

    let resultDiv = document.getElementById('result');
    resultDiv.style.display = 'block';

    if (score >= 45) {
        resultDiv.style.backgroundColor = '#f8d7da';
        resultDiv.style.color = '#721c24';
        resultDiv.innerHTML = `คะแนนรวม: ${score}<br>ระดับความเสี่ยง: เสี่ยงสูงมาก (High Risk)`;
    } else if (score >= 25) {
        resultDiv.style.backgroundColor = '#fff3cd';
        resultDiv.style.color = '#856404';
        resultDiv.innerHTML = `คะแนนรวม: ${score}<br>ระดับความเสี่ยง: เสี่ยงปานกลาง (Moderate Risk)`;
    } else {
        resultDiv.style.backgroundColor = '#d4edda';
        resultDiv.style.color = '#155724';
        resultDiv.innerHTML = `คะแนนรวม: ${score}<br>ระดับความเสี่ยง: เสี่ยงต่ำ / ปกติ (Low Risk)`;
    }
}
</script>

</body>
</html>
