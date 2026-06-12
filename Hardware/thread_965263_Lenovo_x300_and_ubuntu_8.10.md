---
title: "Lenovo x300 and ubuntu 8.10"
date: 2008-10-31
forum: Hardware
---

### Post by martinforsberg on 2008-10-31
Is there anybody running Ubuntu 8.10 on Lenovo x300?


/martin

---

### Post by jahboy on 2008-10-31
I upgraded from Hardy to Intrepid yesterday using the "Upgrade" button inside the Update Manager.

So far, I've noticed the following -

X300 Specific
1- ALSA sound and volume control keys work flawlessly now
2- The drivers provided for the video card, Intel X3100, GM965 do not support 3D at this time.

Generic Changes not unique to the X300
a- Middle-button scrolling no longer works on the Desktop to switch between Desktops using the Workplace Switcher.
(NEW BEHAVIOR: Move the mouse pointer over the Workspace Switcher applet in the bottom panel, and scroll the mouse wheel.)
b- /etc/X11/xorg.conf is depreciated (this isn't x300 specific, clearly)
c- Middle-button scrolling not working in Firefox
(FIX: about:config, general.autoScroll;true, middlemouse.contentLoadURL;false, middlemouse.openNewWindow;false)

---

### Post by martinforsberg on 2008-11-02
I install ubuntu 8.10 from scratch, no upgrade.


I dont know if the graphic card is ok, but 3D is working.
I use the cube and some candy.

The sound doesn't work.


/martin

---

### Post by jahboy on 2008-11-04
I finally figured out what was borking 3d - for some reason, xorg-driver-fglrx was installed during the update and was interfering with xserver-xorg-video-intel?

1. sudo apt-get remove xorg-driver-fglrx
2. restart X

---

### Post by jahboy on 2008-11-04
Sound was not working in Flash inside Firefox.  Fixed with the following command:

> sudo apt-get install libflashsupport

---

### Post by hbj on 2008-12-16
I just got an X300 and everything seemed to be detected and to run correctly right away using 8.10 AMD64.  Sound, 3D graphics, hibernate and suspend, and the built-in webcam (in skype and vlc at least).  I haven't figured out how to get sound recording to work yet though...

---

### Post by Sjums07 on 2008-12-18
I dont all have a x300 :D but i have a N200 ^^ and everything seems okay here :p sound, 3D, flash, shortcut key, etc :D

---

### Post by hbj on 2009-05-06
If you have speaker sound and microphone working in Skype, then sound recording should work too.  I'm running an X300 with 9.04, AMD64, including sound and video in Skype with the built-in mic and camera and everything is working fine.

---

### Post by nidelius on 2009-09-15
I'm running 9.04

Everything runs very smooth except my webcam. It doesn't work.
How is the webcam in 8.10?

---

