---
title: "Problem booting when upgrading graphic card..."
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by salva84 on 2009-10-20
Hi. I had a ATI 4350 with the open source drivers in Karmic, and it worked very well. Today I bought a new ATI 5850, but the problem is when I tried to boot, a message appears "no screen found", maybe I've have to reconfigure Xorg, but I have tried a lot of commands without results. 

I have tried:

dpkg -reconfigure xserver-xorg

but does not work. Can you help me? Thanks!

---

### Post by bumanie on 2009-10-20
I had that experience once during alpha testing. To solve I had to reinstall gpu driver, but I have a nvidia card and don't know the commands for ati cards. However, [this]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") may help. Good luck.

---

### Post by salva84 on 2009-10-20
ok thank you, but the thread you mention is for install the propietary driver, and I want the open source driver. Thanks anyway.

---

### Post by portentum on 2009-10-20
Could you post the contents of your xorg.conf (/etc/X11/xorg.conf) and Xorg.0.log (/var/log/Xorg.0.log) files?

---

### Post by salva84 on 2009-10-20
If you want to know if my xorg is wrong or empty, ok, I say yes, is almost empty. I know that I can configure manually, but I want to configure automatic, like in a fresh install, you know. Thank you

---

### Post by portentum on 2009-10-20
Ok, the reason I asked though is that I would like to understand the problem it's having with your current configuration.

If you want to jump in and try something, I would suggest removing your current xorg.conf file and running without one. If you do X will use the default settings for your card.

---

### Post by salva84 on 2009-10-20
ok, i will try it now

---

### Post by salva84 on 2009-10-20
ok, almost solved, but the resolution is incorrect with the open driver, and with the propietary too, with a panel showing "unsupported hardware". I will use windows until this get fixed :-(

---

### Post by portentum on 2009-10-20
Hopefully someone else can contribute a better fix for the resolution, but if you're planning to continue using the proprietary driver you can use amdcccle to change it. (I say this because, in my experience, the resolution is not saved when changing it this way)

I'm glad to know that removing the old xorg.conf worked out and allowed X to start though.

---

### Post by salva84 on 2009-10-20
Ok, I have tried the amdcce, I have changed the resolution, now my dual monitors are showed correctly, but the UNSUPPORTED HARDWARE is still here, and the closed driver problems (tearing, slow responsiveness). I hope the open source will work with my 5850 soon. Thank you again.

---

### Post by portentum on 2009-10-20
I see the problem now - AMD hasn't yet released a Linux driver for the card, hence the UNSUPPORTED HARDWARE watermark. Sorry I can't be of further help here, and I hope the drivers are released soon.

---

