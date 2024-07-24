# age-calculator-in-java
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Age Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            margin: 0;
            background-color: #f4f4f4;
        }
        h1 {
            color: #333;
        }
        form {
            background: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
            max-width: 400px;
            width: 100%;
        }
        label {
            display: block;
            margin-top: 10px;
            color: #555;
        }
        input[type="number"] {
            width: calc(100% - 12px);
            padding: 8px;
            margin-top: 5px;
            margin-bottom: 15px;
            border: 1px solid #ddd;
            border-radius: 4px;
        }
        input[type="button"] {
            background-color: #007BFF;
            color: #fff;
            padding: 10px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            width: 100%;
        }
        input[type="button"]:hover {
            background-color: #0056b3;
        }
        #result {
            margin-top: 20px;
            font-size: 1.2em;
            color: #333;
        }
    </style>
</head>
<body>
    <h1>Age Calculator</h1>
    <form id="ageForm">
        <label for="day">Day:</label>
        <input type="number" id="day" name="day" min="1" max="31" required>

        <label for="month">Month:</label>
        <input type="number" id="month" name="month" min="1" max="12" required>

        <label for="year">Year:</label>
        <input type="number" id="year" name="year" min="1900" required>

        <input type="button" value="Calculate Age" onclick="calculateAge()">
    </form>
    <h2 id="result"></h2>

    <script>
        function calculateAge() {
            // Get the input values
            const day = document.getElementById('day').value;
            const month = document.getElementById('month').value;
            const year = document.getElementById('year').value;

            // Validate the inputs
            if (!day || !month || !year) {
                document.getElementById('result').innerText = "Please enter a valid date of birth.";
                return;
            }

            // Create a date object from the input values
            const dob = new Date(year, month - 1, day);

            // Get the current date
            const currentDate = new Date();

            // Calculate the age
            let age = currentDate.getFullYear() - dob.getFullYear();
            const monthDifference = currentDate.getMonth() - dob.getMonth();

            if (monthDifference < 0 || (monthDifference === 0 && currentDate.getDate() < dob.getDate())) {
                age--;
            }

            // Display the result
            document.getElementById('result').innerText = `You are ${age} years old.`;
        }
    </script>
</body>
</html>
