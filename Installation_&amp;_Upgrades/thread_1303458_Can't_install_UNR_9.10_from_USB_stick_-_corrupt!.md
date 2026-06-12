---
title: "Can't install UNR 9.10 from USB stick - corrupt?!"
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by ChrisUK on 2009-10-28
I want to install UNR 9.10 onto my Samsung NC20 and I'm having some problems.

First thing I did was download UNR 9.10 .iso (680MB file) from here;
[http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/) 

Then I downloaded and installed UNetbootin onto my Windows machine and followed the instructions here;
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

All went well and I put the USB stick into my netbook and booted it up. 
I was then displayed a screen by UNetbootin giving me 3 options (Default, Help or OEM install) with a countdown of 10 secs. I chose default and it went through all the loading text, etc. and displayed the loading icon for a while - then the screen goes white and I can hear the Ubuntu login sound but the screen keeps changing colour from white, to red, to green, to blue, etc. and it does that continuously! 

Here is a video to explain it better;
[http://www.youtube.com/watch?v=zrbv4VHTYp8](http://www.youtube.com/watch?v=zrbv4VHTYp8)

Any idea why that is happening?
What should I do now?

---

### Post by ChrisUK on 2009-10-28
I just downloaded Ubuntu Netbook Remix again from two different sources and tried them both but I still get the same symptoms.
The screen just changes colour with the Ubuntu login sound!

---

### Post by FountainDew on 2009-10-29
I have this exact problem too, can some one help?

---

### Post by FountainDew on 2009-10-29
For some reason, I could install UNR if I used a 1GB USB stick as opposed to using an 8GB stick. Both were FAT32, strange.

Anyways, its working now! :D

---

### Post by jocheem67 on 2009-10-29
There's word that it's about the usb-media that one uses. Some work others don't....](*,)

---

### Post by dummy910 on 2009-10-29
If that stick has the **horrid U3 system** on it, check out my post on how I turned a U3 stick into a bootable Ubuntu Install-Upgrade thumb-drive.

[http://ubuntuforums.org/showthread.php?t=1273928](http://ubuntuforums.org/showthread.php?t=1273928)
(note: i tried every how to  could find, but I figured it out on my own, nothing else work and in fact I used this very stick to upgrade a few machines to 9.10 already today)

---

### Post by FountainDew on 2009-10-30
> **dummy910 said:**
> If that stick has the **horrid U3 system** on it, check out my post on how I turned a U3 stick into a bootable Ubuntu Install-Upgrade thumb-drive.

[http://ubuntuforums.org/showthread.php?t=1273928](http://ubuntuforums.org/showthread.php?t=1273928)
(note: i tried every how to  could find, but I figured it out on my own, nothing else work and in fact I used this very stick to upgrade a few machines to 9.10 already today)

+1. Wish I could give you rep, because I totally remember U3 FS now. ;)

---

### Post by lhong1987 on 2009-11-02
I have been having the same problem.
It is my personal opinion that .iso burning to thumbdrive sucks.
Anyway, I have so far used usb-creator/Unetbootin in Ubuntu and Windows.
I used the same thumbdrive to install UNR 9.04 with no problem.

I'm thinking I might want to convert .iso into .img and use the img burner.
I'll post with result tonight (in history lecture at the moment)

---

### Post by lhong1987 on 2010-08-18
I completely forgot about this thread.

Apparently some eee does not recognize usb stick right.
"Some BIOS's (eg., the Eee PC netbook') have trouble recognizing that the USB is bootable. You may have to trick it into booting using the following method: At boot, enter the BIOS by pressing F2. Then, right as you exit the BIOS, hit the Esc key. For some systems, this will bring up the boot menu."
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

