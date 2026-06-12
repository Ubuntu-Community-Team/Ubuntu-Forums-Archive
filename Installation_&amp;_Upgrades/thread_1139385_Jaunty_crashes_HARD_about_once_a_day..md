---
title: "Jaunty crashes HARD about once a day."
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by Xavier Oddmon on 2009-04-27
Hello all. I've been using Ubuntu since Feisty Fawn, and think that it is awesome. Needless to say, I downloaded the Jaunty Jackalope .iso on thursday, and promptly installed it. Although now I wish I hadn't. My system is dual boot, windows XP 32 bit, and Jaunty Jackalope 64 bit. When it works, Jaunty works great. It's super fast, all kinds of good stuff. But about once daily, when trying to open a file, delete a file, view a web page, or something, I'll get an error message that says "Error: file system is read only." I can't do anything else after this message occurs. After rebooting, grub doesn't load. (I believe it gets error 16, and once error 2.) To fix it, I reboot with the live CD, or live USB drive, run sudo fsck /dev/sda5. There are tons of errors, which it fixes. Then, everything works normally. The iso I downloaded has the correct MD5 checksum, and both the CD I burned and the boot USB drive I created say no errors when checking disk for errors. I have installed jaunty a total of four times now, twice in ext4, once in reiserFS, and once in ext3. Please help!

---

### Post by Xavier Oddmon on 2009-05-04
I figure i should provide some information about the computer in question. It's an iBuyPower, battalion lx750, basically a rebranded msi mx700. 2.5 ghz core two duo, 4 gigs of ram, nvidia gforce 8600. It has some toshiba wireless n and bluetooth card (internal). 250 gig hard drive. It never had a problem with ubuntu before jaunty.

---

