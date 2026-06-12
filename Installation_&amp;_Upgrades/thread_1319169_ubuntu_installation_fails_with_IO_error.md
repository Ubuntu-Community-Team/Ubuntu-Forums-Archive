---
title: "ubuntu installation fails with I/O error"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by Lajo on 2009-11-08
I'm trying to install 9.10 from the Live CD but it keeps failing with the same error each time. I get to the part where it copies files to the HD but the installer crashes at 26% with an I/O error (errorno 5 if I remember correctly).

The ISO file is correct, I verified the MD5 hash. I tried to burn it on another CD from another PC at 8x writing speed, it didn't help.

The strangest of all is that I decided to go back to 9.04 so I grabbed the 9.04 Live CD I had originally installed it from but it crashed at the same point with the same error!

Any idea what's going on? How can I get more info about the problem, like a log of the installation process?

Any input is greatly appreciated.

---

### Post by Togezo on 2009-11-08
I/O Erno5 can be caused by a number of things. If your sure your disk is fine it might be a problem to do with RAM modules. Have you added any new modules?

I cite this case. It's in rgards to 8.10, but describes similar problems to what you're reporting:

[http://www.linuxquestions.org/questions/linux-newbie-8/errno-5-inputoutput-error-639355/](http://www.linuxquestions.org/questions/linux-newbie-8/errno-5-inputoutput-error-639355/)

---

### Post by Lajo on 2009-11-09
Thanks for you post.

It looks like the problem was with the optical drive, I kept getting SQUASHFS errors.

This makes the whole Live CD quite unstable, but I finally managed to create a startup USB drive with usb-creator-gtk and install karmic from there.

So the problem was solved but I still have no idea why I'm getting the errors with the Live CD but not on an installed system

---

