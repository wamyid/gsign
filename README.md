# login
Halaman Login wamyid

## Google Sign In
Embedding Google Sign-In into your vanilla JavaScript GitHub Pages site involves a few steps, including setting up a Google API Console project, including the necessary scripts, and writing the JavaScript code to handle the sign-in process. Here's a step-by-step guide to help you get started:

### 1. Set Up Google API Console Project

1. **Create a Project**:
   - Go to the [Google API Console](https://console.developers.google.com/).
   - Create a new project by clicking on the project dropdown and selecting "New Project".

2. **Enable the Google Sign-In API**:
   - In your project dashboard, click on "Enable APIs and Services".
   - Search for "Google Sign-In API" and enable it.

3. **Configure OAuth Consent Screen**:
   - Go to the "OAuth consent screen" tab.
   - Fill out the necessary information and save.

4. **Create OAuth 2.0 Credentials**:
   - Go to the "Credentials" tab.
   - Click on "Create Credentials" and select "OAuth 2.0 Client IDs".
   - Choose "Web application" as the application type.
   - Set the "Authorized JavaScript origins" to `https://your-github-username.github.io`.
   - Set the "Authorized redirect URIs" to `https://your-github-username.github.io`.
   - Save and note down the Client ID.

### 2. Include Google Platform Library

Add the following script in the `<head>` section of your HTML file to load the Google Platform Library:

```html
<head>
  <script src="https://apis.google.com/js/platform.js" async defer></script>
  <meta name="google-signin-client_id" content="YOUR_CLIENT_ID.apps.googleusercontent.com">
</head>
```

Replace `YOUR_CLIENT_ID` with the Client ID you obtained from the Google API Console.

### 3. Add the Google Sign-In Button

Add the following HTML code where you want the sign-in button to appear:

```html
<div class="g-signin2" data-onsuccess="onSignIn"></div>
```

### 4. Handle Sign-In Success

Add the following JavaScript code to handle the sign-in process:

```html
<script>
  function onSignIn(googleUser) {
    // Get the user's profile information
    var profile = googleUser.getBasicProfile();
    console.log('ID: ' + profile.getId());
    console.log('Name: ' + profile.getName());
    console.log('Image URL: ' + profile.getImageUrl());
    console.log('Email: ' + profile.getEmail());

    // Example: Update your page content or call your backend with the user's information
    document.getElementById('user-name').textContent = profile.getName();
    document.getElementById('user-email').textContent = profile.getEmail();
    document.getElementById('user-image').src = profile.getImageUrl();
  }
</script>
```

### 5. Display User Information

Include elements in your HTML to display the user's information:

```html
<p id="user-name"></p>
<p id="user-email"></p>
<img id="user-image" src="" alt="User Image">
```

### Full Example

Here’s how the complete `index.html` file might look:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Google Sign-In Demo</title>
  <script src="https://apis.google.com/js/platform.js" async defer></script>
  <meta name="google-signin-client_id" content="YOUR_CLIENT_ID.apps.googleusercontent.com">
</head>
<body>
  <h1>Google Sign-In Demo</h1>
  <div class="g-signin2" data-onsuccess="onSignIn"></div>

  <h2>User Information</h2>
  <p id="user-name"></p>
  <p id="user-email"></p>
  <img id="user-image" src="" alt="User Image">

  <script>
    function onSignIn(googleUser) {
      var profile = googleUser.getBasicProfile();
      console.log('ID: ' + profile.getId());
      console.log('Name: ' + profile.getName());
      console.log('Image URL: ' + profile.getImageUrl());
      console.log('Email: ' + profile.getEmail());

      document.getElementById('user-name').textContent = profile.getName();
      document.getElementById('user-email').textContent = profile.getEmail();
      document.getElementById('user-image').src = profile.getImageUrl();
    }
  </script>
</body>
</html>
```

### Deploy to GitHub Pages

1. Push your `index.html` and other necessary files to a GitHub repository.
2. Go to the repository settings.
3. Scroll down to the "GitHub Pages" section.
4. Select the branch you want to deploy from (usually `main` or `master`) and the root directory.
5. Save and visit `https://your-github-username.github.io/your-repo-name/` to see your Google Sign-In in action.

By following these steps, you should have a working Google Sign-In integrated into your GitHub Pages site using vanilla JavaScript.
