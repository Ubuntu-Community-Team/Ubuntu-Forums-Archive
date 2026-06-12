---
title: "I hear the startup drum then nothing..."
date: 2006-06-28
forum: Hardware &amp; Laptops
---

### Post by chrluc on 2006-06-28
Installed dapper on an ibm t20 (had breezy on it and no problems) and it will take me restarting the system about 5 to 10 times before I actually get a login screen, I hear the startup drum and all I see is a cursor.... and nothing I have let it sit for 10 or 15 min and nothing ever happens, any ideas. by the way the bios is current.

---

### Post by dlai on 2006-06-28
Posted in the bug tracker:
> 

This appears to be a hardware bug. See [http://www.thinkwiki.org/wiki/Problem_with_video_related_system_lockup](http://www.thinkwiki.org/wiki/Problem_with_video_related_system_lockup) and [http://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/2006-March/032672.html](http://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/2006-March/032672.html)

Adding

Option "BusType" "PCI"
Option "DmaMode" "None"

to the "Device" section in xorg.conf fixed the issue for me.


This fixed it for me... if you don't know how to edit the xorg.conf choose the Safe Mode kernel in grub..login at the text login, and type```
nano /etc/X11/xorg.conf
``` this will load the text editor and it shoul be easy to go and edit the file appropriately...

---

### Post by mstine on 2006-06-28
Also reference [http://ubuntuforums.org/showthread.php?p=1191311#post1191311](http://ubuntuforums.org/showthread.php?p=1191311#post1191311) for another possible solution.

Just referencing another method, just in case this one didn't work for someone.  :D

Matt

---

### Post by echoburns on 2007-11-20
thanks for the response.

I've managed to get to the desktop now by setting the cd to be the primary boot device.

---

### Post by echoburns on 2007-11-20
when i click install it takes ages to anything, I've been stuck on stage 1/7 for about 20 mins all i can hear is the cd going crazy, is that normal?

---

### Post by NoThanksM$ on 2008-03-26
thanks, dlai - this fixed the problem for me as well.

---

