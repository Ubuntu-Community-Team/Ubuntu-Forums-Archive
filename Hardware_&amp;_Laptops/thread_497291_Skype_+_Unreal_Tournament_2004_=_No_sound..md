---
title: "Skype + Unreal Tournament 2004 = No sound."
date: 2007-07-10
forum: Hardware &amp; Laptops
---

### Post by renatoc8 on 2007-07-10
Hello, I currently have Unreal Tournament 2004 and Skype installed. If I try to play UT while Skype is running, I get no sound in UT. I understand that skype might be trying to take control of OSS, however I set Skype to ALSA, but it continues blocking the game's sound. If Skype is not running however it works PERFECT!

Is there any way to allow the two applications to "share" the driver?

 -Renato

---

### Post by renatoc8 on 2007-07-10
Hi again, I looked around and found the "sudo killall esd" command, this fixes some audio problems, but does not solve mine because skype is still using the sound driver (obviously).

 -Renato

---

