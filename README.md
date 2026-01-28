# Sports.web
New 
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Cricket Stats Q&A</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <style>
    * {
      box-sizing: border-box;
      font-family: system-ui, -apple-system, BlinkMacSystemFont, sans-serif;
    }

    body {
      margin: 0;
      background: #f6f7f9;
      color: #222;
    }

    header {
      background: #0b3d2e;
      color: white;
      padding: 18px;
      text-align: center;
    }

    header h1 {
      margin: 0;
      font-size: 1.6rem;
    }

    .container {
      max-width: 900px;
      margin: auto;
      padding: 16px;
    }

    .ask-box {
      background: white;
      padding: 16px;
      border-radius: 10px;
      box-shadow: 0 5px 15px rgba(0,0,0,0.05);
      margin-bottom: 20px;
    }

    .ask-box h2 {
      margin-top: 0;
    }

    textarea, select, button {
      width: 100%;
      margin-top: 10px;
      padding: 10px;
      border-radius: 6px;
      border: 1px solid #ccc;
      font-size: 0.95rem;
    }

    button {
      background: #0b3d2e;
      color: white;
      cursor: pointer;
      border: none;
    }

    button:hover {
      background: #095c44;
    }

    .question {
      background: white;
      padding: 14px;
      border-radius: 10px;
      margin-bottom: 16px;
      box-shadow: 0 5px 15px rgba(0,0,0,0.05);
    }

    .question small {
      color: #666;
    }

    .answers {
      margin-top: 10px;
      padding-left: 10px;
    }

    .answer {
      background: #f1f3f5;
      padding: 8px;
      border-radius: 6px;
      margin-top: 6px;
      font-size: 0.9rem;
    }

    .reply-box {
      margin-top: 8px;
    }

    footer {
      text-align: center;
      padding: 15px;
      color: #666;
      font-size: 0.85rem;
    }
  </style>
</head>
<body>

<header>
  <h1>Cricket Stats – Q&A Hub</h1>
  <p>Ask. Analyze. Argue with stats.</p>
</header>

<div class="container">

  <div class="ask-box">
    <h2>Ask a Question</h2>

    <select id="role">
      <option value="">Select Player Type</option>
      <option value="Batsman">Batsman</option>
      <option value="Bowler">Bowler</option>
      <option value="Wicketkeeper">Wicketkeeper</option>
    </select>

    <select id="era">
      <option value="">Select Era</option>
      <option value="1990-2000">1990–2000</option>
      <option value="2000-2010">2000–2010</option>
      <option value="2010-2020">2010–2020</option>
      <option value="2020-Present">2020–Present</option>
    </select>

    <textarea id="questionText" rows="3" placeholder="Ask your cricket stats question..."></textarea>
    <button onclick="addQuestion()">Post Question</button>
  </div>

  <div id="questions"></div>

</div>

<footer>
  Cricket Stats Q&A • Clean • Simple • Opinionated
</footer>

<script>
  const questionsDiv = document.getElementById("questions");

  function addQuestion() {
    const role = document.getElementById("role").value;
    const era = document.getElementById("era").value;
    const text = document.getElementById("questionText").value;

    if (!role || !era || !text) {
      alert("Please fill all fields");
      return;
    }

    const questionEl = document.createElement("div");
    questionEl.className = "question";

    questionEl.innerHTML = `
      <strong>${text}</strong><br>
      <small>${role} • Era: ${era}</small>

      <div class="answers"></div>

      <div class="reply-box">
        <textarea rows="2" placeholder="Write a reply..."></textarea>
        <button onclick="addAnswer(this)">Reply</button>
      </div>
    `;

    questionsDiv.prepend(questionEl);

    document.getElementById("questionText").value = "";
    document.getElementById("role").value = "";
    document.getElementById("era").value = "";
  }

  function addAnswer(btn) {
    const replyBox = btn.previousElementSibling;
    const text = replyBox.value;

    if (!text) return;

    const answersDiv = btn.parentElement.previousElementSibling;
    const answerEl = document.createElement("div");
    answerEl.className = "answer";
    answerEl.innerText = text;

    answersDiv.appendChild(answerEl);
    replyBox.value = "";
  }
</script>

</body>
</html>
