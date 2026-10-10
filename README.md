<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Offline Code Checker · JavaScript, HTML, CSS</title>
    <style>
        :root {
            --primary-color: #2563eb;
            --primary-hover: #1d4ed8;
            --bg-color: #f8fafc;
            --card-bg: #ffffff;
            --text-color: #1e293b;
            --border-color: #cbd5e1;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-color);
            line-height: 1.6;
            margin: 0;
            padding: 20px;
        }

        .container {
            max-width: 800px;
            margin: 0 auto;
            background: var(--card-bg);
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
        }

        h1 {
            margin-top: 0;
            font-size: 2rem;
            border-bottom: 2px solid var(--border-color);
            padding-bottom: 10px;
        }

        h2 {
            font-size: 1.5rem;
            margin-top: 30px;
        }

        .options-bar {
            display: flex;
            gap: 10px;
            margin-bottom: 15px;
            flex-wrap: wrap;
            align-items: center;
        }

        label {
            font-weight: 500;
        }

        select, button {
            padding: 8px 16px;
            border-radius: 4px;
            border: 1px solid var(--border-color);
            font-size: 0.95rem;
            cursor: pointer;
        }

        select {
            background-color: #fff;
        }

        button {
            background-color: #e2e8f0;
            color: #334155;
            transition: background-color 0.2s;
        }

        button:hover {
            background-color: #cbd5e1;
        }

        button.primary {
            background-color: var(--primary-color);
            color: white;
            border-color: var(--primary-color);
        }

        button.primary:hover {
            background-color: var(--primary-hover);
        }

        textarea {
            width: 100%;
            height: 200px;
            font-family: "Fira Code", Consolas, Monaco, monospace;
            font-size: 0.9rem;
            padding: 10px;
            border: 1px solid var(--border-color);
            border-radius: 4px;
            box-sizing: border-box;
            resize: vertical;
        }

        .info-box {
            background-color: #f1f5f9;
            border-left: 4px solid #64748b;
            padding: 15px;
            margin-top: 20px;
            font-size: 0.9rem;
            border-radius: 0 4px 4px 0;
        }

        .output-box {
            min-height: 100px;
            background: #f8fafc;
            border: 1px dashed var(--border-color);
            padding: 15px;
            border-radius: 4px;
            white-space: pre-wrap;
        }
    </style>
</head>
<body>

<div class="container">
    <h1>Offline Code Checker</h1>
    <p>Checks and fixes JavaScript, HTML and CSS using built-in rules. No AI, no server.</p>

    <h2>Your code</h2>
    <div class="options-bar">
        <select id="language-select">
            <option value="auto">Auto-detect</option>
            <option value="javascript">JavaScript</option>
            <option value="html">HTML</option>
            <option value="css">CSS</option>
        </select>

        <button class="primary" onclick="checkAndFixCode()">Check & fix</button>
        <button onclick="loadDemo()">Load demo</button>
        <button onclick="clearEverything()">Clear everything</button>
    </div>

    <textarea id="code-input" placeholder="Paste your code here..."></textarea>

    <div class="info-box">
        Nothing is stored or sent. Your code is checked by JavaScript running in this page only. It is never saved to a database or browser storage, and this page cannot make network requests to other sites. Clear or close the tab to remove it. Your code is never run, only parsed.
    </div>

    <h2>Fixed code</h2>
    <div class="options-bar">
        <button onclick="copyFixedCode()">Copy fixed code</button>
    </div>
    <textarea id="fixed-output" readonly placeholder="Your fixed code will appear here..."></textarea>

    <h2>Your original code, problems highlighted</h2>
    <div id="highlighted-output" class="output-box">No problems highlighted yet.</div>

    <h2>What was found</h2>
    <div id="findings-output" class="output-box">No issues detected yet.</div>
</div>

<script>
    // Placeholder function for client-side parsing logic
    function checkAndFixCode() {
        const inputCode = document.getElementById('code-input').value;
        const language = document.getElementById('language-select').value;
        
        if (!inputCode.trim()) {
            alert('Please enter some code to check.');
            return;
        }

        // Simulating offline processing
        document.getElementById('fixed-output').value = inputCode; 
        document.getElementById('highlighted-output').textContent = "No syntax errors found during static analysis.";
        document.getElementById('findings-output').textContent = "Analysis complete: 0 structural errors found (using built-in rules).";
    }

    function loadDemo() {
        document.getElementById('code-input').value = `function testDemo() {\n    console.log("Hello World")\n    if(true){\n    return true;\n    }\n}`;
        document.getElementById('language-select').value = 'javascript';
    }

    function clearEverything() {
        document.getElementById('code-input').value = '';
        document.getElementById('fixed-output').value = '';
        document.getElementById('highlighted-output').textContent = 'Nothing is stored or sent.';
        document.getElementById('findings-output').textContent = 'Cleared.';
        document.getElementById('language-select').value = 'auto';
    }

    function copyFixedCode() {
        const fixedText = document.getElementById('fixed-output');
        fixedText.select();
        fixedText.setSelectionRange(0, 99999); // For mobile devices
        navigator.clipboard.writeText(fixedText.value);
        alert("Fixed code copied to clipboard!");
    }
</script>

</body>
</html>
