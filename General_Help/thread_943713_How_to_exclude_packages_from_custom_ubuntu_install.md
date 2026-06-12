---
title: "How to exclude packages from custom ubuntu installer"
date: 2008-10-10
forum: General Help
---

### Post by the real omni on 2008-10-10
Hi, in brief, I'm looking for a way to omit packages from being installed in a custom ubuntu install cd.

I'm trying to create a custom Ubuntu install disc using the guide posted here:

[https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)

The problem is that when I try to install from the custom ISO i've built, I get the error that "No network concentrators found" after scanning for PPPoE.

In this thread: [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=693731](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=693731) it states that all I have to do is remove the ppp .udeb files and I'm good to go, but when I do that the installer errors out and says it can't copy files from the CD (it does this when trying to copy pppoe).

Is there any way to tell the installer to just outright omit the PPPoE package?

---

### Post by PieterN on 2008-10-23
I have followed the exact same guide and am encoutering the same problem (when using the Ubuntu 8.04.1 alternate (i386) iso). Apparently the guide is outdated or something, because I've followed the stated steps minutely.

Please reply if you read this and have a (possible) solution.

---

### Post by the real omni on 2008-10-23
I ended up just starting from scratch with the Ubuntu Server 8.04 install disc. Lo and behold, no PPPoE concentrator issues!

---

### Post by PieterN on 2008-10-27
I've tried using the server disc as well but had the concentrator problems again. After some more researching I ended up simply removing the PPP udeb from the disk (in pool/main/p/ppp). This causes the installer not to load PPP and therefore not whine about the concentrators.

---

