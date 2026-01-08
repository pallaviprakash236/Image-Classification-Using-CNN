<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Farmer Login & Signup</title>

  <style>
    * { box-sizing: border-box; font-family: 'Segoe UI', sans-serif; }

    body {
      margin: 0;
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      background: linear-gradient(rgba(0,0,0,0.6), rgba(0,0,0,0.6)),
        url('https://eos.com/wp-content/uploads/2023/11/components-of-different-types-of-fertilizers.jpg.webp');
      background-size: cover;
      background-position: center;
      animation: zoom 16s infinite alternate;
    }

    @keyframes zoom {
      from { background-size: 100%; }
      to { background-size: 115%; }
    }

    .card {
      width: 400px;
      padding: 35px;
      border-radius: 20px;
      background: rgba(255,255,255,0.18);
      backdrop-filter: blur(14px);
      box-shadow: 0 25px 50px rgba(0,0,0,0.35);
      color: white;
      animation: fadeUp 1s ease;
    }

    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(30px); }
      to { opacity: 1; transform: translateY(0); }
    }

    h2 { text-align: center; margin-bottom: 25px; }

    .input-group { margin-bottom: 16px; }

    label { display: block; margin-bottom: 6px; font-size: 14px; }

    input {
      width: 100%;
      padding: 12px;
      border-radius: 10px;
      border: none;
      outline: none;
      font-size: 14px;
    }

    input:focus { box-shadow: 0 0 0 3px #66bb6a; }

    .error {
      font-size: 12px;
      color: #ffcdd2;
      margin-top: 4px;
    }

    button {
      width: 100%;
      padding: 12px;
      margin-top: 10px;
      border: none;
      border-radius: 12px;
      background: linear-gradient(135deg, #1b5e20, #66bb6a);
      color: white;
      font-size: 16px;
      cursor: pointer;
    }

    button:hover { opacity: 0.9; }

    .toggle {
      text-align: center;
      margin-top: 18px;
      cursor: pointer;
      font-size: 14px;
    }
  </style>
</head>
<body>

  <div class="card">
    <h2 id="title">Far Care Login</h2>

    <form id="form">
      <div class="input-group" id="nameGroup" style="display:none;">
        <label>Farmer Name</label>
        <input type="text" id="name">
        <div class="error" id="nameError"></div>
      </div>

      <div class="input-group">
        <label>Email</label>
        <input type="email" id="email">
        <div class="error" id="emailError"></div>
      </div>

      <div class="input-group">
        <label>Password</label>
        <input type="password" id="password">
        <div class="error" id="passwordError"></div>
      </div>

      <button type="submit">Submit</button>
    </form>

    <div class="toggle" onclick="toggleForm()">New Farmer? Signup</div>
  </div>

  <script>
    let isLogin = true;

    function toggleForm() {
      isLogin = !isLogin;
      document.getElementById('title').innerText = isLogin ? 'Farmer Login' : 'Farmer Signup';
      document.getElementById('nameGroup').style.display = isLogin ? 'none' : 'block';
      document.querySelector('.toggle').innerText = isLogin
        ? 'New Farmer? Signup'
        : 'Already registered? Login';
      clearErrors();
    }

    function clearErrors() {
      ['nameError','emailError','passwordError'].forEach(id =>
        document.getElementById(id).innerText = ''
      );
    }

    document.getElementById('form').addEventListener('submit', function(e) {
      e.preventDefault();
      clearErrors();

      const name = document.getElementById('name').value.trim();
      const email = document.getElementById('email').value.trim();
      const password = document.getElementById('password').value.trim();

      let valid = true;

      if (!isLogin && name.length < 3) {
        document.getElementById('nameError').innerText = 'Name must be at least 3 characters';
        valid = false;
      }

      const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      if (!emailRegex.test(email)) {
        document.getElementById('emailError').innerText = 'Enter a valid email';
        valid = false;
      }

      if (password.length < 6) {
        document.getElementById('passwordError').innerText = 'Password must be at least 6 characters';
        valid = false;
      }

      if (valid) {
        alert(isLogin ? 'Login Successful 🌾' : 'Signup Successful 🌱');
      }
    });
  </script>

</body>
</html>
# Image-Classification-Using-CNN
classification involves assigning labels to images from a set of predefined categories. A typical CNN includes convolutional layers, pooling layers, and fully connected layers, and is highly effective in tasks like object recognition and medical image analysis.
