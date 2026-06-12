---
title: "Help!!! Ubuntu on USB HDD Messed my booting"
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by justanothermilo on 2009-08-27
hello everyone, i'm kinda new on linux, so i tried to install Ubuntu 8.10 on USB HDD.

Believe it or not all works fine, but i can't boot windows without my USB HDD. 

I believe that i messed it by installing some boot file or somthing on hdd and my bios put it as priority. sorry for bad english and help!!! what should i do to get to run windows without external hard drive?:confused::confused::confused::confused: btw> it's on my Hp compaq 6720s laptop

---

### Post by utnubuuser on 2009-08-27
I think when Ubuntu installs, it changes the XP's MBR.  You'll probably have to use  an XP disk to fix it. 
It might help if you had grub on the internal hdd too.
There should be plenty of threads related to fixing MBR with XP.  ..such as this one -> [http://ubuntuforums.org/archive/index.php/t-1054472.html]("http://ubuntuforums.org/archive/index.php/t-1054472.html")

ps if you follow that thread and fix the issue,  You can probably set up your hdds so you can boot from either by having grub on the usb-hdd, then selecting it through the boot device list with F12 at startup.  You might want to have a look for threads related to setting up a persistent usb install, so it would be like a portable OS.

---

### Post by presence1960 on 2009-08-27
You installed GRUB to MBR of internal drive. Now when you boot it looks for the menu.lst file on the external disk. If the external isn't plugged in when you boot it can't find menu.lst thus the GRUB error. if you are only going to use the external when you want Ubuntu I would restore Windows bootloader to MBR of internal disk (see [here]("http://ubuntuforums.org/showthread.php?t=1014708")) and put GRUB on MBR of external disk. This way when you boot without the external disk windows boots. When you plug in the external GRUB will take over & you can boot into Ubuntu. Of course your machine must be capable of booting from USB for this to work, if you need more detailed instructions post back.

---

### Post by justanothermilo on 2009-08-27
Problem is that my windows is media center, and for repair it require floppy disk. First thing is that i dont have that floppy and second my laptop doesnt got floppy reader

---

