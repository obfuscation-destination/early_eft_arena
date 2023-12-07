# EFT Arena Early Download
Wanting to risk your account? BSG has a ton of analytics in the launcher, such as which screen you're on, and what actions are being taken. Your "gameState" might be set to "availableSoon", yet you're downloading the game as if it's "installRequired".

Don't be an idiot about it.
If BSG catches you, and they likely will, your account may be permabanned. Do not follow this guide unless you feel like risking a download for a currently unplayable game.

### Modifying the launcher
- In your BattleState Games folder, find the path `BsgLauncher\Content\app\games\stateHandler.js`
- Locate the `availableSoon` case on line 292.
- Comment out everything in this case except the `break` statement.
- Locate the `installRequired` case on line 248.
- Copy everything inside of this case except the `break` statement.
- Go back to the `availableSoon` case, and paste in the `installRequired` case's code. Restart the launcher.

Congrats! You can now install Arena. Generally, doing this wouldn't allow you to install Arena. However, BSG has listed a package for download for this application. 
As this package is listed... the launcher grabs it. When testing this a few days prior, it would fail to grab a package and not be downloaded. As BSG has listed a package, it's downloadable now.

### Launching the Game
- You'll notice when you attempt to launch the game, you get hit with an error stating:
```
Game launch error

ERROR: 103003

Wait for the start of testing!

ERROR: 401004
```
- You cannot boot the game yet. If you want to go further, you will need to download Burp Suite Community Edition.
- I will not provide instructions for how to use Burp Suite, that's on you.
- After importing the root CA cert and setting your local Windows to use Burp Suite as a Proxy server, prepare to launch the game.
- Enable your Proxy intercept.
- Initially you'll want to launch the main EFT game. Find the request to the EFT gateway for authenticating, and they'll send you back a zlib deflated string.
- This string contains your session information. Arena currently replies with an error code instead of a session.
- Attempt to launch Arena now, intercepting the request and response. You'll want to "Copy to file" on the response.
- Open this file in your favorite hex editor, and overwrite what BSG sent you with your zlib string from earlier. You'll have better success doing this with the raw bytes.
- If you're fast enough in overwriting the response and sending it to the launcher, your game will boot.
- Quickly disable your System Proxy in Windows.
- Congrats you've booted Arena! Oh wait. You didn't.
- Your major version is out of sync from server. There was no reason to do any of this.

The version YOU installed is 0.3.1.27711. The version BSG just used in the tournament was 0.3.1.27750. You cannot play even if you wanted to. Bit of a waste of time and a waste of an account to get banned eh? Rip my accounts, gonna get HWID banned now lol.
