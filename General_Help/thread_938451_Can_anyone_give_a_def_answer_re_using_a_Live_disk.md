---
title: "Can anyone give a def answer re using a Live disk?"
date: 2008-10-04
forum: General Help
---

### Post by Steve Riley on 2008-10-04
Hi Guys,
I'm trying to convince myself to make the swap from Windows to Linux but I'm having problems getting answers to a question.
Let me explain. On  the Ubuntu page dealing with "Trying-out Ubuntu", it says in part..... "It is possible to test whether Ubuntu works on your computer, without altering or affecting your files in any way, before installing it permanently. You can do this using the Ubuntu Desktop CD, which is able to start a cut-down version of Ubuntu on your computer without installing it."

OK, the question I need answering is this, IF, when using a Live CD to test Ubuntu on my system and to check that things like my Wi-Fi dongle, scanner, printer, camera dock etc, everything seems to work as it should, is this because the Live disk has the drivers needed or is it because the Ubuntu disk is actually accessing my "C" drive to locate the drivers for these accessories?
The thing is that if Ubuntu gets the drivers from the "C" drive, how is that helping me make the choice to switch?
Cheers,
Steve

---

### Post by Locutus_of_Borg on 2008-10-04
the live cd will not have access to you hard drive unless you specifically mount it

you can run the live cd without a hard drive even available

---

### Post by FAJALOU on 2008-10-04
It is not looking into your C: drive at all.  Therefore... your wifi dongle may not work due to the fact that it _may_ but unsupported.  However, it may be supported, and if it is not out of the box, the people here know how to get it to work.  So in short, no it will not access your C: drive.  It may mount it; for the purposes of seeing your C: drive from the CD, but other than that, it will not affect your HDD, or look into it.

---

### Post by 3rdalbum on 2008-10-04
Windows drivers are made for Windows only. They don't work with Linux. The same goes for Windows programs. Ubuntu is using its own built-in drivers.

---

### Post by taladan on 2008-10-04
ndiswrappers aside, Linux has the drivers just built into it to run most hardware.  There is the ocassional oddity (I have an EZ Cam that Linux makes the image invert and I have no idea why) and wireless can /sometimes/ be a pain, but for the most part if it runs on the CD, it'll run on the install.

Tal

---

### Post by ad_267 on 2008-10-04
The live CD can't get drivers off your C drive. Those drivers are Windows drivers and wouldn't work with Ubuntu.

---

