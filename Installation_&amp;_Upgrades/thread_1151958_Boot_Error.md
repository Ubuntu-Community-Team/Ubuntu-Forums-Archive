---
title: "Boot Error"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by Z3R0600D on 2009-05-07
I recently tried to install ubuntu 9.04 (jaunty) as a dual boot OS, I already had XP Pro installed. The installation seemed to go ok until I rebooted as requested. When it booted up it didn't HA well it tried and what displayed after about 1min. was:
 
GRUB Loading stage 1.5.
 
 
GRUB loading, please wait...
Error 21
 
also displayed Error 18 but that went away after a few reboots
 
I'm using an HP 530 notebook and before it looks to the GRUB I have 3 options
either hold F9 to select boot device, F10 ROM based setup or F12 Network Service Boot.
 
So I can't even get to my BIOS from what I can see.
 
Any help would be great please I want to recover this system.

---

### Post by lykwydchykyn on 2009-05-07
Error 21 is described as "unknown boot error", which isn't very helpful for you.  Error 18 indicates that the kernel it's trying to load is an invalid format, which would suggest to me that the file is corrupted.

My best guess at this point is that you might have physical problems with the RAM or Hard drive.  You can diagnose this using the Ubuntu CD.

RAM: Boot to the CD and select "test memory" from the initial menu.

Hard drive: Boot the CD all the way to the desktop.  Open a terminal window and enter this command:
```

sudo badblocks -v /dev/sda

```
That should tell you if you have bad sectors on the hard drive and how many.

Let us know what you discover.

---

### Post by Z3R0600D on 2009-05-07
Thanks for the quick reply I'll try and get it taken care of within the day but I tried booting to the CD as one of my first options and the notebook seemed not to be able to see the disc which makes me think it was a bad burn.
 
I'll try and get a better disc and see if that boots.

---

