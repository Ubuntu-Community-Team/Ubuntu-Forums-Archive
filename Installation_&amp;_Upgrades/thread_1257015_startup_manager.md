---
title: "startup manager"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by jayanramesh on 2009-09-03
Dear buddies,
I recently installed grub 2 and kernel 2.6.30 .After installing these ,startup manager has disappeared from SPM and now I am not able to install even through terminal" sudo apt-get install startupmanager" and giving the error message as"Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package startupmanager is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package startupmanager has no installation candidate".
It will be very much appreciated if anyone direct me to solve this prob.
Thank you

---

### Post by drs305 on 2009-09-03
StartUp-Manager has limited capabilities in  Grub 2. The boot files are vastly different and use a different method of updating the menu.lst  You can change the default OS/kernel and a few other settings.

I am running Karmic and startupmanager is still in the repositories. Make sure you have the "universe" repository enabled.

The creator of StartUp-Manager has indicated that he might make a version for Grub 2, so it may become available or he may simply incorporate the changes into the original app in some way.

In the meantime, here are couple of links explaining Grub 2. As it matures you will find that Grub 2 is a highly flexible and robust boot manager. While it currently is command-line driven, eventually someone will create a GUI interface. The Grub 2 scripts should make this goal fairly easy to achieve.
[Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275")

[https://wiki.ubuntu.com/Grub2]("https://wiki.ubuntu.com/Grub2")

---

### Post by jayanramesh on 2009-09-03
Dear drs305,
Thank you so much for your prompt reply.

---

