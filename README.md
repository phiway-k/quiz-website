<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MGT120(preparation By Phiwa Khoza )</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background: #f4f4f4;
            padding: 20px;
        }
        .quiz-container {
            max-width: 600px;
            background: white;
            padding: 20px;
            margin: auto;
            border-radius: 10px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
        }
        h2 {
            color: #333;
        }
        .question {
            font-size: 18px;
            margin-bottom: 10px;
        }
        .options button {
            display: block;
            width: 100%;
            padding: 10px;
            margin: 5px 0;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            background: #007BFF;
            color: white;
            font-size: 16px;
        }
        .options button:hover {
            background: #0056b3;
        }
        .correct {
            background: #28a745 !important;
        }
        .incorrect {
            background: #dc3545 !important;
        }
        #score {
            font-size: 20px;
            margin-top: 20px;
            font-weight: bold;
        }
    </style>
</head>
<body>

<div class="quiz-container">
    <h2>Business & Management Quiz</h2>
    <p class="question" id="question-text">Loading question...</p>
    <div class="options" id="options-container"></div>
    <p id="score"></p>
</div>

<script>
    const quizData = [
        {
            question: "Organisations that help other organisations sell their goods to customers are known as:",
            options: ["A) Competitors", "B) Potential Competitors", "C) Distributors", "D) Customers", "E) None of the above"],
            answer: "C"
        },
        {
            question: "When the top management of American Airlines requires law firms to report diversity statistics, this is an example of:",
            options: ["A) Managing diversity", "B) Quid pro quo", "C) The ombudsman effect", "D) Bias", "E) Stereotyping"],
            answer: "A"
        },
        {
            question: "To Dell Computer, the educational institutions that train future Dell employees are:",
            options: ["A) Competitors", "B) Distributors", "C) Customers", "D) Suppliers"],
            answer: "D"
        },
        {
            question: "The process that managers use to design a structure of working relationships is called:",
            options: ["A) Planning", "B) Leading", "C) Demonstrating", "D) Controlling", "E) Organising"],
            answer: "E"
        },
        {
            question: "When entrepreneurs score high on a personality trait for risk-taking, they have scored high on:",
            options: ["A) Openness to experience", "B) Internal locus of control", "C) External locus of control", "D) Need for achievement", "E) Self-esteem"],
            answer: "A"
        },
        {
            question: "An autonomous part of an organisation given all resources to develop and market a product is called:",
            options: ["A) Skunkworks", "B) New venture division", "C) Cross-functional team", "D) Product champion team", "E) Learning organisation"],
            answer: "B"
        }
    ];

    let currentQuestionIndex = 0;
    let score = 0;

    function loadQuestion() {
        if (currentQuestionIndex >= quizData.length) {
            document.getElementById("question-text").innerText = "Quiz Completed!";
            document.getElementById("options-container").innerHTML = "";
            document.getElementById("score").innerText = `Your Final Score: ${score} / ${quizData.length}`;
            return;
        }

        let questionData = quizData[currentQuestionIndex];
        document.getElementById("question-text").innerText = questionData.question;
        let optionsContainer = document.getElementById("options-container");
        optionsContainer.innerHTML = "";

        questionData.options.forEach(option => {
            let button = document.createElement("button");
            button.innerText = option;
            button.onclick = () => checkAnswer(option);
            optionsContainer.appendChild(button);
        });
    }

    function checkAnswer(selectedOption) {
        let correctAnswer = quizData[currentQuestionIndex].answer;
        let buttons = document.querySelectorAll(".options button");

        buttons.forEach(button => {
            if (button.innerText.startsWith(correctAnswer)) {
                button.classList.add("correct");
            } else if (button.innerText === selectedOption) {
                button.classList.add("incorrect");
            }
            button.disabled = true;
        });

        if (selectedOption.startsWith(correctAnswer)) {
            score++;
        }

        setTimeout(() => {
            currentQuestionIndex++;
            loadQuestion();
        }, 1500);
    }

    loadQuestion();
</script>

</body>
</html>
