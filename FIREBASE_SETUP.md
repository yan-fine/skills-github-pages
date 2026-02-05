# Firebase Setup Instructions

To make the calendar work, you need to set up a free Firebase project:

## Step 1: Create Firebase Project

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Click "Add project"
3. Enter a project name (e.g., "meeting-calendar")
4. Disable Google Analytics (optional for this project)
5. Click "Create project"

## Step 2: Set up Realtime Database

1. In your Firebase project, click "Realtime Database" in the left menu
2. Click "Create Database"
3. Select a location close to you
4. Start in **Test mode** (allows read/write without authentication)
5. Click "Enable"

## Step 3: Get Firebase Configuration

1. Click the gear icon (⚙️) next to "Project Overview"
2. Select "Project settings"
3. Scroll down to "Your apps" section
4. Click the web icon `</>`
5. Register your app with a nickname (e.g., "calendar-app")
6. Copy the `firebaseConfig` object

## Step 4: Update calendar.html

1. Open `calendar.html`
2. Find this section around line 375:

```javascript
const firebaseConfig = {
    apiKey: "YOUR_API_KEY",
    authDomain: "YOUR_PROJECT.firebaseapp.com",
    databaseURL: "https://YOUR_PROJECT.firebaseio.com",
    projectId: "YOUR_PROJECT_ID",
    storageBucket: "YOUR_PROJECT.appspot.com",
    messagingSenderId: "YOUR_SENDER_ID",
    appId: "YOUR_APP_ID"
};
```

3. Replace it with your actual Firebase config values
4. Save the file

## Step 5: Deploy

1. Commit and push your changes to GitHub:
   ```bash
   git add .
   git commit -m "Add meeting calendar"
   git push
   ```

2. Your calendar will be available at:
   `https://[your-username].github.io/[repo-name]/calendar.html`

## Security Note

The calendar is currently in test mode (no authentication). For a private group:

1. Go to Firebase Console → Realtime Database → Rules
2. Replace with:
```json
{
  "rules": {
    ".read": true,
    ".write": true
  }
}
```

For production use, consider adding Firebase Authentication.

## Features

- ✅ Real-time updates (everyone sees changes instantly)
- ✅ Color-coded availability (more green = more people available)
- ✅ Works on mobile and desktop
- ✅ No login required (just enter your name)
- ✅ Shows who's available on each date
- ✅ Free for small groups (Firebase free tier: 1GB storage, 10GB/month downloads)
