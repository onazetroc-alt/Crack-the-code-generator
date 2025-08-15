# Crack-the-code-generator
Puzzle
<!DOCTYPE html>

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Crack the Code Puzzle Generator</title>
    <style>
        body {
            margin: 0;
            padding: 20px;
            font-family: 'Arial', sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
        }

```
    .puzzle-container {
        background: white;
        border-radius: 15px;
        padding: 30px;
        box-shadow: 0 20px 40px rgba(0,0,0,0.1);
        max-width: 500px;
        width: 90%;
        text-align: center;
        position: relative;
        overflow: hidden;
    }
    
    .puzzle-container::before {
        content: '';
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        height: 5px;
        background: linear-gradient(90deg, #4facfe 0%, #00f2fe 100%);
    }
    
    .title {
        font-size: 24px;
        font-weight: bold;
        color: #2c3e50;
        margin-bottom: 10px;
        text-shadow: 1px 1px 2px rgba(0,0,0,0.1);
    }
    
    .stats {
        background: #ecf0f1;
        padding: 10px;
        border-radius: 8px;
        margin-bottom: 20px;
        font-weight: bold;
        color: #2c3e50;
    }
    
    .lock-icon {
        font-size: 40px;
        color: #3498db;
        margin-bottom: 15px;
        text-shadow: 2px 2px 4px rgba(0,0,0,0.1);
    }
    
    .code-input {
        display: flex;
        justify-content: center;
        gap: 10px;
        margin: 20px 0;
    }
    
    .digit-input {
        width: 50px;
        height: 50px;
        border: 3px solid #3498db;
        border-radius: 8px;
        font-size: 24px;
        font-weight: bold;
        color: #2c3e50;
        text-align: center;
        background: #f8f9fa;
        box-shadow: inset 0 2px 4px rgba(0,0,0,0.1);
    }
    
    .digit-input:focus {
        outline: none;
        border-color: #e74c3c;
        box-shadow: 0 0 0 2px rgba(231, 76, 60, 0.2);
    }
    
    .description {
        font-size: 16px;
        color: #34495e;
        margin: 20px 0;
        font-weight: 500;
    }
    
    .hint-label {
        background: #3498db;
        color: white;
        padding: 8px 16px;
        border-radius: 20px;
        font-weight: bold;
        display: inline-block;
        margin: 20px 0;
        box-shadow: 0 4px 8px rgba(52, 152, 219, 0.3);
    }
    
    .clues {
        display: grid;
        grid-template-columns: 1fr;
        gap: 15px;
        margin-top: 20px;
    }
    
    .clue {
        background: #f8f9fa;
        padding: 15px;
        border-radius: 10px;
        border-left: 4px solid #3498db;
        box-shadow: 0 2px 4px rgba(0,0,0,0.1);
    }
    
    .clue-numbers {
        font-size: 24px;
        font-weight: bold;
        color: #2c3e50;
        margin-bottom: 5px;
        letter-spacing: 8px;
    }
    
    .clue-text {
        font-size: 14px;
        color: #7f8c8d;
        font-weight: 500;
    }
    
    .button-group {
        display: flex;
        gap: 10px;
        justify-content: center;
        margin-top: 20px;
        flex-wrap: wrap;
    }
    
    .button {
        padding: 12px 20px;
        border: none;
        border-radius: 25px;
        font-weight: bold;
        cursor: pointer;
        font-size: 14px;
        transition: all 0.3s ease;
    }
    
    .check-button {
        background: linear-gradient(45deg, #2ecc71, #27ae60);
        color: white;
        box-shadow: 0 4px 15px rgba(46, 204, 113, 0.3);
    }
    
    .check-button:hover {
        transform: translateY(-2px);
        box-shadow: 0 6px 20px rgba(46, 204, 113, 0.4);
    }
    
    .new-puzzle-button {
        background: linear-gradient(45deg, #3498db, #2980b9);
        color: white;
        box-shadow: 0 4px 15px rgba(52, 152, 219, 0.3);
    }
    
    .new-puzzle-button:hover {
        transform: translateY(-2px);
        box-shadow: 0 6px 20px rgba(52, 152, 219, 0.4);
    }
    
    .reveal-button {
        background: linear-gradient(45deg, #ff6b6b, #ee5a24);
        color: white;
        box-shadow: 0 4px 15px rgba(255, 107, 107, 0.3);
    }
    
    .reveal-button:hover {
        transform: translateY(-2px);
        box-shadow: 0 6px 20px rgba(255, 107, 107, 0.4);
    }
    
    .result {
        margin-top: 15px;
        padding: 15px;
        border-radius: 10px;
        font-weight: bold;
        font-size: 18px;
        animation: fadeIn 0.5s ease;
    }
    
    .result.correct {
        background: #2ecc71;
        color: white;
        box-shadow: 0 4px 15px rgba(46, 204, 113, 0.3);
    }
    
    .result.incorrect {
        background: #e74c3c;
        color: white;
        box-shadow: 0 4px 15px rgba(231, 76, 60, 0.3);
    }
    
    .result.revealed {
        background: #f39c12;
        color: white;
        box-shadow: 0 4px 15px rgba(243, 156, 18, 0.3);
    }
    
    @keyframes fadeIn {
        from { opacity: 0; transform: translateY(-10px); }
        to { opacity: 1; transform: translateY(0); }
    }
    
    .celebration {
        font-size: 24px;
        margin-bottom: 10px;
    }
</style>
```

</head>
<body>
    <div class="puzzle-container">
        <div class="title">🔓 Crack the Code Generator!</div>

```
    <div class="stats">
        Puzzles Solved: <span id="solved-count">0</span> | 
        Current Puzzle: #<span id="puzzle-number">1</span>
    </div>
    
    <div class="lock-icon">🔒</div>
    
    <div class="code-input">
        <input type="number" class="digit-input" id="digit1" min="0" max="9" placeholder="?">
        <input type="number" class="digit-input" id="digit2" min="0" max="9" placeholder="?">
        <input type="number" class="digit-input" id="digit3" min="0" max="9" placeholder="?">
    </div>
    
    <div class="description">A Numeric Lock has a 3 Digit Key</div>
    
    <div class="hint-label">HINTS</div>
    
    <div class="clues" id="clues">
        <!-- Clues will be generated here -->
    </div>
    
    <div class="button-group">
        <button class="button check-button" onclick="checkAnswer()">Check Answer</button>
        <button class="button reveal-button" onclick="revealAnswer()">Show Answer</button>
        <button class="button new-puzzle-button" onclick="generateNewPuzzle()">New Puzzle</button>
    </div>
    
    <div id="result"></div>
</div>

<script>
    let currentCode = [];
    let currentClues = [];
    let puzzlesSolved = 0;
    let puzzleNumber = 1;
    
    function generateRandomCode() {
        return [
            Math.floor(Math.random() * 10),
            Math.floor(Math.random() * 10),
            Math.floor(Math.random() * 10)
        ];
    }
    
    function generateRandomGuess(excludeDigits = []) {
        let guess = [];
        for (let i = 0; i < 3; i++) {
            let digit;
            do {
                digit = Math.floor(Math.random() * 10);
            } while (excludeDigits.includes(digit) && Math.random() < 0.7); // 70% chance to avoid excluded digits
            guess.push(digit);
        }
        return guess;
    }
    
    function analyzeGuess(code, guess) {
        let correctAndWellPlaced = 0;
        let correctButWrongPlace = 0;
        
        // Check for correct and well placed
        for (let i = 0; i < 3; i++) {
            if (code[i] === guess[i]) {
                correctAndWellPlaced++;
            }
        }
        
        // Check for correct but wrong place
        for (let i = 0; i < 3; i++) {
            if (code[i] !== guess[i] && code.includes(guess[i])) {
                correctButWrongPlace++;
            }
        }
        
        return { correctAndWellPlaced, correctButWrongPlace };
    }
    
    function generateClueText(analysis) {
        if (analysis.correctAndWellPlaced === 0 && analysis.correctButWrongPlace === 0) {
            return "Nothing is correct";
        } else if (analysis.correctAndWellPlaced === 1 && analysis.correctButWrongPlace === 0) {
            return "One number is correct and well placed";
        } else if (analysis.correctAndWellPlaced === 0 && analysis.correctButWrongPlace === 1) {
            return "One number is correct but wrongly placed";
        } else if (analysis.correctAndWellPlaced === 0 && analysis.correctButWrongPlace === 2) {
            return "Two numbers are correct but wrongly placed";
        } else if (analysis.correctAndWellPlaced === 1 && analysis.correctButWrongPlace === 1) {
            return "One number is correct and well placed, one is correct but wrongly placed";
        } else if (analysis.correctAndWellPlaced === 2 && analysis.correctButWrongPlace === 0) {
            return "Two numbers are correct and well placed";
        } else if (analysis.correctAndWellPlaced === 0 && analysis.correctButWrongPlace === 3) {
            return "Three numbers are correct but all wrongly placed";
        } else {
            return "Multiple numbers have issues"; // fallback
        }
    }
    
    function generateClues(code) {
        let clues = [];
        let usedDigits = [...code];
        let excludedDigits = [];
        
        // Generate 5 different clue types
        let clueTypes = [
            'nothing_correct',
            'one_correct_well_placed', 
            'one_correct_wrong_place',
            'two_correct_wrong_place',
            'mixed'
        ];
        
        for (let i = 0; i < 5; i++) {
            let guess;
            let analysis;
            let attempts = 0;
            
            do {
                if (i === 0) { // First clue - try to make "nothing correct"
                    let availableDigits = [0,1,2,3,4,5,6,7,8,9].filter(d => !code.includes(d));
                    if (availableDigits.length >= 3) {
                        guess = [];
                        for (let j = 0; j < 3; j++) {
                            let randomIndex = Math.floor(Math.random() * availableDigits.length);
                            guess.push(availableDigits[randomIndex]);
                            excludedDigits.push(availableDigits[randomIndex]);
                        }
                    } else {
                        guess = generateRandomGuess(excludedDigits);
                    }
                } else {
                    guess = generateRandomGuess(excludedDigits);
                }
                
                analysis = analyzeGuess(code, guess);
                attempts++;
            } while (attempts < 20 && clues.some(clue => 
                clue.guess[0] === guess[0] && clue.guess[1] === guess[1] && clue.guess[2] === guess[2]
            ));
            
            let clueText = generateClueText(analysis);
            clues.push({
                guess: guess,
                text: clueText,
                analysis: analysis
            });
        }
        
        return clues;
    }
    
    function displayClues(clues) {
        const cluesContainer = document.getElementById('clues');
        cluesContainer.innerHTML = '';
        
        clues.forEach(clue => {
            const clueDiv = document.createElement('div');
            clueDiv.className = 'clue';
            clueDiv.innerHTML = `
                <div class="clue-numbers">${clue.guess.join(' ')}</div>
                <div class="clue-text">${clue.text}</div>
            `;
            cluesContainer.appendChild(clueDiv);
        });
    }
    
    function generateNewPuzzle() {
        currentCode = generateRandomCode();
        currentClues = generateClues(currentCode);
        displayClues(currentClues);
        
        // Clear inputs and result
        document.getElementById('digit1').value = '';
        document.getElementById('digit2').value = '';
        document.getElementById('digit3').value = '';
        document.getElementById('result').innerHTML = '';
        
        // Update puzzle number
        document.getElementById('puzzle-number').textContent = puzzleNumber;
    }
    
    function checkAnswer() {
        const digit1 = parseInt(document.getElementById('digit1').value);
        const digit2 = parseInt(document.getElementById('digit2').value);
        const digit3 = parseInt(document.getElementById('digit3').value);
        
        if (isNaN(digit1) || isNaN(digit2) || isNaN(digit3)) {
            document.getElementById('result').innerHTML = '<div class="result incorrect">Please enter all three digits!</div>';
            return;
        }
        
        const userGuess = [digit1, digit2, digit3];
        const resultDiv = document.getElementById('result');
        
        if (userGuess[0] === currentCode[0] && userGuess[1] === currentCode[1] && userGuess[2] === currentCode[2]) {
            puzzlesSolved++;
            document.getElementById('solved-count').textContent = puzzlesSolved;
            resultDiv.innerHTML = `
                <div class="result correct">
                    <div class="celebration">🎉 Correct! 🎉</div>
                    The code was indeed ${currentCode.join('')}!
                </div>
            `;
            setTimeout(() => {
                puzzleNumber++;
                generateNewPuzzle();
            }, 2000);
        } else {
            resultDiv.innerHTML = `
                <div class="result incorrect">
                    ❌ Not quite right! Try again or reveal the answer.
                </div>
            `;
        }
    }
    
    function revealAnswer() {
        document.getElementById('result').innerHTML = `
            <div class="result revealed">
                💡 The answer is: <strong>${currentCode.join('')}</strong><br>
                <small>Try the next puzzle!</small>
            </div>
        `;
    }
    
    // Auto-focus next input
    document.getElementById('digit1').addEventListener('input', function() {
        if (this.value) document.getElementById('digit2').focus();
    });
    
    document.getElementById('digit2').addEventListener('input', function() {
        if (this.value) document.getElementById('digit3').focus();
    });
    
    document.getElementById('digit3').addEventListener('input', function() {
        if (this.value) checkAnswer();
    });
    
    // Allow Enter key to check answer
    document.addEventListener('keypress', function(e) {
        if (e.key === 'Enter') {
            checkAnswer();
        }
    });
    
    // Generate first puzzle on load
    generateNewPuzzle();
</script>
```

</body>
</html>
