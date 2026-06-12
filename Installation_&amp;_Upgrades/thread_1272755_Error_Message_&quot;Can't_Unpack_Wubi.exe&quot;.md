---
title: "Error Message: &quot;Can't Unpack Wubi.exe&quot;"
date: 2009-09-22
forum: Installation &amp; Upgrades
---

### Post by Norm158 on 2009-09-22
Just got my ubuntu cd in the mail. Tried to boot it by putting it in my PC's disk drive and restarting, but the computer just booted to my os (win98SE). I navigated to my disk drive, opened the Ubuntu distribution CD and clicked on wubi.exe. Got a window saying "can't unpack Wubi.exe.

What should I do now? :confused: This is my first experience with ubuntu. Please be gentle.

---

### Post by raymondh on 2009-09-24
> **Norm158 said:**
> Just got my ubuntu cd in the mail. Tried to boot it by putting it in my PC's disk drive and restarting, but the computer just booted to my os (win98SE). I navigated to my disk drive, opened the Ubuntu distribution CD and clicked on wubi.exe. Got a window saying "can't unpack Wubi.exe.

What should I do now? :confused: This is my first experience with ubuntu. Please be gentle.

Welcome to ubuntu and the forums.

Is this the canonical DVD?  See this link:

[https://wiki.ubuntu.com/WubiGuide#DVD%20and%20Alternate%20ISO](https://wiki.ubuntu.com/WubiGuide#DVD%20and%20Alternate%20ISO)

An option for you is to install Ubuntu in its' own partition ... also giving you the option to choose an OS at start-up.

Some steps/tips (if you decide to)

1.  Back-up your files
2.  Defrag windows (if you are using windows as the current OS)
3.  Boot into the CD (load the CD, power on, access the BIOS, change the order of boot so that the CD drive boots first)
4.  Check the CD for defects (one of the options)
5.  Try Ubuntu without changes (another option presented) to give you an idea of how your system plays with the ubuntu version (wifi, sound, keyboard, Fkeys, etc)
6.  When OK, install
7.  In step 4, choose SIDE-BY-SIDE
8.  When you choose side-by-side, there is a slider presented below.  You have to grab it with your mouse and move it accordingly to set partition sizes between both OS (see attached).  If not, you will default to a 2.5GB install which is not enough for the first update
9.  Continue with the install.  Once done, eject the CD, reboot, access Ubuntu and update.

[http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874](http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874)

Another option is to create the partition beforehand and manually install.  This allows you the flexibility such as separating your /home from root (/) .... something of value just in case you need to re-install later on.

Post back if you need a brief guide.  Good luck.

---

