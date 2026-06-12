---
title: "[SOLVED] Making a Custom Launcher"
date: 2008-10-17
forum: General Help
---

### Post by birddog165 on 2008-10-17
Hello, I want to add to my desktop panel a "custom application launcher." The launcher needs to be able to open and run Starcraft which I run through Wine. So if anyone could help me out that'd be great.

---

### Post by Yellow Pasque on 2008-10-17
If the shortcut is already under Applications -> Wine, you can just right-click it and add it to the panel.

If you're creating the Launcher manually use a command like this:
```
env WINEPREFIX="/home/<YOUR_USERNAME_HERE>/.wine" wine "C:\<PATHTOFILE_HERE>"
```

---

### Post by birddog165 on 2008-10-18
Hey, thank you so much Temüjin. That works flawlessly.

---

### Post by TCSnyder on 2008-10-18
you can try to click on Applications > Wine > Programs  and right click your program and click "add to Desktop" and it will make a link

---

