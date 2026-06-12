---
title: "Broadcom Problems"
date: 2005-11-27
forum: Hardware &amp; Laptops
---

### Post by Euhemeros on 2005-11-27
Hello,

I installed ubuntu 5.10 today on my Compaq Presario 3210CA, which as a Broadcom BCM4306 802.11 b/g Wireless card.

Now, I have ndiswrapper installed and I've found three different files off of the Compaq driver CD: bcmwl5.inf, bcmwl5.sys, and bcmwl5a.inf. None of them, however, work and I keep on getting an 'error' message each time I try to install it:

>>Installing bmcwl5
cp: cannot stat `home/sean/Desktop/bmcwl5.inf': No such file or directory<<

I've typed everything in correctly, but it just doesn't work for any of the files.

I figure if I can't get this to work, I'll have to switch back to Windows XP.

Thanks for your help.

---

### Post by towsonu2003 on 2005-11-27
[QUOTE=Euhemeros]
cp: cannot stat `home/sean/Desktop/bmcwl5.inf': No such file or directory<<
[/QUOTE]

seems like misspelling... you wrote /b**mc**wl5.inf , had to be b**cm**wl5.inf

:p

hopefully that's it

---

### Post by mips on 2005-11-27
Read these links very carefully, 
[https://wiki.ubuntu.com/forum/hardware/ndiswrapper](https://wiki.ubuntu.com/forum/hardware/ndiswrapper)
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

The wiki recommends NOT using the drivers off your install/driver cd.

Look for posts by Lambert, [http://ubuntuforums.org/member.php?u=26479](http://ubuntuforums.org/member.php?u=26479)

---

### Post by Euhemeros on 2005-11-27
Thanks, the drivers were fine, but I was able to find the GUI programs for ndiswrapper in the link above. I used that with the drivers from the CD and everything works fine (I used bcmwl5.inf).

---

