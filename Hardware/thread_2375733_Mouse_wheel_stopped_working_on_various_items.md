---
title: "Mouse wheel stopped working on various items"
date: 2017-10-27
forum: Hardware
---

### Post by accounts0 on 2017-10-27
Mouse wheel used to scroll in Kate, used to change volume when hovering over volume system tray icon. Now it's not working on anything but Google Chrome Stable & Thunderbird, as far as I can tell.

Don't know what might have changed. Need help.

---

### Post by accounts0 on 2017-10-27
Here's how it got fixed:

Open "'System Settings' > 'Input Devices' > 'Mouse' > 'General'" & check the 'Reverse scroll direction' box, followed by 'Apply'.
Then uncheck the 'Reverse scroll direction' box, followed by 'Apply' again, & that did it.

---

### Post by accounts0 on 2017-10-27
EDIT:
Marking as "Unsolved" because the solution posted above didn't survive a reboot. Now I have to check & uncheck that box every time I log on. Looking into scripting next...

---

### Post by accounts0 on 2017-10-27
Ok, I discovered it's possible to get scroll functionality back by unplugging & re-inserting the USB dongle. Apparently this is a common issue for my specific mouse model, & there's an app to fix it on SourceForge [1].

It just resets the USB connection like I found out worked earlier.  


[1]
[https://sourceforge.net/projects/resetmsmice/](https://sourceforge.net/projects/resetmsmice/)

---

### Post by accounts0 on 2017-10-28
> **accounts0 said:**
> there's an app to fix it on SourceForge [1].

It just resets the USB connection


[1]
[https://sourceforge.net/projects/resetmsmice/](https://sourceforge.net/projects/resetmsmice/)


This is nice, I've got it scripted to run at logon- all it does is 'echo <your-sudo-password> | sudo -S service resetmsmice restart' so I have that on a launcher icon too in case it goes wonky after it runs initially at the start of my session. I've only had to use it once, & it was a relief there's a quick one-button solution for when this darn MS product decides to hate on 'nix. hehehe

---

