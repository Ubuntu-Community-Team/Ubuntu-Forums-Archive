---
title: "Ubuntu 9.10UNR Flashdisc install failure on Toshiba NB100"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by Henzin on 2009-11-02
Hello everyone.
 
 
I've encountered a problem while attempting to install the 9.10 Ubuntu netbook remix on my Toshiba NB100 netbook. I've carefully created the boot flashdisc according to the description here:
 
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
 
I used the Windows method, (the ISO image was mounted and opened by Daemon Tools Lite 4.20 and the usb-creator.exe was run this way).
 
After creating the USB boot flashdisc, I changed the boot priority in BIOS and re-booted. Now the first selection screen of Ubuntu appeared correctly (Menu: Install, Try, Check Discs for errors etc.)
 
Both Try Ubuntu... and Install Ubuntu don't work. After choosing those options, the splashscreen appears for a couple of seconds and then the screen gets dark and so it stays. Now I have installed Linux and Ubuntu in particular several times before (on my desktop), so I know I've got to give it some time, but when there was the black screen for 1/2 hour I was sure there's something wrong. I tried to check the disk for errors and no error was detected.
 
Please help. Thank you
 
H.
 
 
 
My netbook:
Toshiba NB100 (WinXP-32 Pre-Installed)
Partitions resized in Windows with EASEUS.

---

### Post by Henzin on 2009-11-10
:(  As I got no help or advice at all, I decided to solve it myself and write it down for those who face the same problem.

 The reason is in the boot flashdisc creator. The default one that could be found within the ubuntu image doesn't work properly. I found UNetbootin through Easy Peasy wiki that's up to the task.

 Could be found here:
 p, li { white-space: pre-wrap; }  [http://sourceforge.net/projects/unetbootin/files/UNetbootin/Custom/unetbootin-eeeubuntu-windows-276.exe/download](http://sourceforge.net/projects/unetbootin/files/UNetbootin/Custom/unetbootin-eeeubuntu-windows-276.exe/download)

---

