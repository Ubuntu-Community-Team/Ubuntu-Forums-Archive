---
title: "Can't install on clean drive"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by sbg101 on 2009-08-29
I've been trying to install 9.04 on my desktop computer without success. After selecting install from the splash screen, all I get is a blank screen and a blinking cursor. Even after I zero-filled the HDD with KillDisk, the results are the same.

Thinking that errors had happened in the download of the .iso or in burning it to CD, I put the same disk in an older laptop that still has XP on it expecting the same or similar results. Instead, Ubuntu installed flawlessly without any deletion/addition of boot parameters.

Since there isn't anything on the HDD with which to have conflicts, I have no idea what is causing the hangup or how to remedy this frustration. 

My hopes are to have Ubuntu installed on my main HDD, with XP on a secondary. The secondary HDD, as well as an additional CD-R have been disconnected until I can get Ubuntu up and running.

Now that I've had a couple of days to play with Ubuntu on my laptop, I would really like to have it on my desktop. 

Stats:

AMD 64 3200+
4 GB Ram
GeoForce 8500

Any suggestions would be greatly appreciated!

---

### Post by tal007 on 2009-08-29
This is what I would do: 

1. Check it in your bios setting to see if it is seen by your BIOS.

2. Check Master/Slave hardware setting on your hard drive.

3. Run your CD without installing if you can.

4. Examine the partition table using the partition editor from 
   tool bar.

3. Check if any connection to your drive is loose.


3. Check power to your drive. Make sure it is not loose.

---

### Post by presence1960 on 2009-08-29
[Boot Options]("https://help.ubuntu.com/community/BootOptions") - scroll down to the section about F4. that's what you want to use : safe graphics mode

if that does not work try [alternate text based installer]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

---

