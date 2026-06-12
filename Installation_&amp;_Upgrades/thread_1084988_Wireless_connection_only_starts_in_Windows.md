---
title: "Wireless connection only starts in Windows"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by smcasten on 2009-03-02
Hi All...I tried out Ubuntu booting up from a CD and now want to install it on to my laptop.  However there is a problem.  Booting up this way leaves the manual on/off key *off* for the wireless connection.  Using windows, the wireless defaults on and then I can use  the on/off key to turn it off manually.  If I am encountering this problem with the CD bootup, I am hesitant to install the program onto the hard drive.  Does anyone know of a way to get around this issue?  Thanks in advance.  steve c

---

### Post by avtolle on 2009-03-02
Sometimes, the only way to get wireless to work is post-install, i.e., it doesn't work from the Live CD, but once installed, the necessary kernel modules and drivers can be installed, etc. to get wireless to work. Other times, wireless works from the Live CD, but there is no visual indication of it working, as the Linux drivers don't turn on a light, etc.

When booting from the Live CD, click on the Network Manager icon (the two computers) in the top panel, and if your wireless card is detected and is working, you will get a listing of any wireless networks detected, as well (if you are on a wired connection) an indication of that, too. Alternatively, right-click the computer icon, and see if wireless enabled is checked; if so, then your wireless card is detected.

---

### Post by smcasten on 2009-03-02
> **avtolle said:**
> 
there is no visual indication of it working, as the Linux drivers don't turn on a light, etc.

Doesn't the little red x on the Network Manager tell you whether or not the wireless connection is working?

[QUOTE CONTINUED] When booting from the Live CD, click on the Network Manager icon (the two computers) in the top panel, and if your wireless card is detected and is working, you will get a listing of any wireless networks detected, as well (if you are on a wired connection) an indication of that, too. Alternatively, right-click the computer icon, and see if wireless enabled is checked; if so, then your wireless card is detected.[/QUOTE]

I had done as you suggested and tried so many different ways to connect using the Network Manager that I will have to go back and see if Ubuntu detects the wireless network on boot up...I don't think it did because I manually entered the network info which made no difference...but I will check again to be sure.  I did follow all the steps in the help menu as far as setting up the interent connection.

---

### Post by avtolle on 2009-03-02
> **smcasten said:**
> Doesn't the little red x on the Network Manager tell you whether or not the wireless connection is working?

[QUOTE CONTINUED] When booting from the Live CD, click on the Network Manager icon (the two computers) in the top panel, and if your wireless card is detected and is working, you will get a listing of any wireless networks detected, as well (if you are on a wired connection) an indication of that, too. Alternatively, right-click the computer icon, and see if wireless enabled is checked; if so, then your wireless card is detected.

I had done as you suggested and tried so many different ways to connect using the Network Manager that I will have to go back and see if Ubuntu detects the wireless network on boot up...I don't think it did because I manually entered the network info which made no difference...but I will check again to be sure.  I did follow all the steps in the help menu as far as setting up the interent connection.[/quote]
If there was a red x on the Network Manager icon, that would indicate no network connection (wireless and wired both), so if you were not connected to the router or modem by a cable, and were trying to use your wireless card only, yes, that would be evidence that your wireless isn't detected.

My best guess from what you have posted is that your wireless card isn't being detected by the Live CD. Do you know what chipset it uses, e.g., Atheros, Broadcom, RealTek? There are different solutions for each.

---

### Post by smcasten on 2009-03-02
It's a Broadcom chipset

---

### Post by ironblossom on 2009-03-03
i have the same prob.........my chipset is RealTek......
i installed ubuntu 8.10......check "Hardware Devices"........theres no hardware found.

---

### Post by ironblossom on 2009-03-03
> **ironblossom said:**
> i have the same prob.........my chipset is RealTek......
i installed ubuntu 8.10......check "Hardware Devices"........theres no hardware found.

[http://ubuntuforums.org/showthread.php?t=1086113](http://ubuntuforums.org/showthread.php?t=1086113)
got some pics of output of *ifconfig* , *sudo etc/init.d/networking restart * and *ifup eth0*

---

