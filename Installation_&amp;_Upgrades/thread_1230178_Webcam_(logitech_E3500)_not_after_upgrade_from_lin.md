---
title: "Webcam (logitech E3500) not after upgrade from linux kernel 2.6.28 to 2.6.31 rc5"
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by Radhavictory on 2009-08-03
Hi,

I attempted an install of linux kernel 2.6.31rc to try improving graphic performance and things seem to be working fine excepting for my webcam. Previously it worked with no problem, now it isn't even detected! I presume that a downgrade back to the default kernel on jaunty will fix the prob. I tired re-installing kernel 2.6.28 (default one) but the problem persists. Any suggestions of what I could do?

Thanks in advance.

---

### Post by Radhavictory on 2009-08-03
Correction,

lsusb in terminal shows this

Bus 002 Device 005: ID 046d:09a4 Logitech, Inc. 
Bus 002 Device 002: ID 0d49:7310 Maxtor 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 0f62:1001 Acrox Technologies Co., Ltd Targus Mini Trackball Optical Mouse
Bus 006 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

so cam is detected but not by any software not even by cheese, Help!

---

### Post by sau99ms on 2009-08-03
> **Radhavictory said:**
> Correction,

lsusb in terminal shows this

Bus 002 Device 005: ID 046d:09a4 Logitech, Inc. 
Bus 002 Device 002: ID 0d49:7310 Maxtor 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 0f62:1001 Acrox Technologies Co., Ltd Targus Mini Trackball Optical Mouse
Bus 006 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

so cam is detected but not by any software not even by cheese, Help!

Hi,

I'm a complete newbie here but you may need to change one of the preferences in the Cheese tool bar menu (Edit -> Preferences) as it may be set to default. Might be worth checking out the preferences in Cheese and seeing if your camera is already selected as a default or if you have to choose it from the drop down list? 

I'll be interested to know if this works as I'm currently running Kernel 2.6.28 and thinking of upgrading to .31 rc5 - and I also happen to have a logitech E3500 webcam which 'touch wood' is working fine atm!

Keep me posted and hope I've been of some help (?)

All the best,

Mark

---

### Post by Radhavictory on 2009-08-04
Hello Mark,

There weren't any settings to configure in cheese......although, I did sort out the problem. After having having installed and tried out various kernels, I have settled with the 2.6.30. My system is stable since, window effects work beautifully along with Cairo dock in openGL mode.....also the cam is working just fine!

Thanks for trying to give a hand....I hope I have been of help too!

Ciao!
Victory

P.S- if you want to switch between kernels, at startup when you see Grub loading.....3,2,1.....press esc and you can choose between the various kernels that are installed on your system.

---

### Post by noblow91 on 2009-08-21
I just upgraded to the 2.6.28-15-generic and my webcam has stopped showing video. Camera Monitor does detect it for once, but cheese shows me the video test instead of my camera feed. I am unable to reinstall Ubuntu not because I dont have a disk, but because I have no way of backing up my stuff...


edit: turns out that a recent installation of gnump3d had required me to restart my computer...something that I dont do very often...

---

### Post by Radhavictory on 2009-08-21
noblow91
I installed the 2.6.30 generic kernels instead of the 2.6.28-15-generic ones and things worked out great. Camera works and everything is in order. I suggest you try that out.

---

### Post by sau99ms on 2010-03-15
> **Radhavictory said:**
> Hello Mark,

There weren't any settings to configure in cheese......although, I did sort out the problem. After having having installed and tried out various kernels, I have settled with the 2.6.30. My system is stable since, window effects work beautifully along with Cairo dock in openGL mode.....also the cam is working just fine!

Thanks for trying to give a hand....I hope I have been of help too!

Ciao!
Victory

P.S- if you want to switch between kernels, at startup when you see Grub loading.....3,2,1.....press esc and you can choose between the various kernels that are installed on your system.

Hi Victory,

Sorry it's taken so long for me to reply - been REALLY busy with work etc! Thanks for replying and I'm glad you got your problem sorted out. Great tip on the kernel selection tool. I didn't know about that one so I'll try and remember that one!

I've recently installed Cairo dock and I'm loving it and my eye candy is working a treat too so I'm really enjoying ubuntu right now. I hope lynx brings some more improvements (if possible!)

All the best,

Mark

---

