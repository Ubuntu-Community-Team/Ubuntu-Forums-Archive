---
title: "&quot;Unknown Monitor&quot; Resolution Problem : ("
date: 2010-04-18
forum: Hardware
---

### Post by WiReIs on 2010-04-18
Hi, im very new to linux in general, ive been brought up with Windoze all my life so any help would be very much appreciated :)

I installed Ubuntu 9.10 onto my own laptop after hearing from a few friends that its better than any windows OS.. which i fully agree, everything works fine and im really enjoying the Ubuntu OS... However my dad has took a liking to the Ubuntu OS after playing about on my laptop and he has decided he would also like to convert from Windoze Vista to ultimate Ubuntu on his own laptop, i installed the new Ubuntu OS onto his laptop and went to adjust the resolution and its only giving me an option between 800 x 600 (4:3) and 640 x 480 (4:3) its also saying "unknown monitor".. the ideal resolution for his laptop would be 1280 x 800 (16:10) how can i fix this 

Thanks in advance, Ross

---

### Post by wojox on 2010-04-18
What type of card does he have? Run this in the terminal and post it back up here:

```
lspci | grep -i net
```

---

### Post by WiReIs on 2010-04-18
> 00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)


is the right info? i ran that command u gave on terminal

---

### Post by Techer on 2010-04-18
No I don't think that's the info needed.
Try running
```
lspci
```
(the "| grep -i net" part of the suggested command passes the output of "lspci" to "grep -i net" which in turn only outputs the lines that contain "net" to the console)
and search for a video controller. My video controller is
```
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce GT 130M] (rev a1)
```I'm not an expert yet, but I doubt we need to know what network adapter he has to fix this problem.

I know of one thing that could fix this problem:
Go to System->Administration->Hardware Drivers on the menu and install any proprietary drivers available.

Good luck:)

---

### Post by wojox on 2010-04-18
I think I've been up to long:

```
lspci | grep VGA
```

---

### Post by WiReIs on 2010-04-18
Yea that one worked :)  

> 01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)I tried going to System> Admin> Hardware Drivers.. "no proprietary drivers are in use on this system"

Do i need to install drivers for my card type?

---

### Post by pi/roman on 2010-04-18
There usually are not any proprietary drivers and it should not be necessary to recognize the monitor.  You should first try updating your xorg.conf file, then check to see if there are newer sis drivers.

---

### Post by WiReIs on 2010-04-18
is there a command i can enter into the ubuntu terminal to update my xorg.config file?

sorry about this dude, im a total noob with ubuntu linux

---

### Post by pi/roman on 2010-04-18
This will create a new xorg.conf
sudo X :2 -configure
My guide is here:
[http://ubuntuforums.org/showthread.php?t=1401835](http://ubuntuforums.org/showthread.php?t=1401835)

---

### Post by WiReIs on 2010-04-18
Thanks Pi/romain i will give this a try and keep u posted :)

---

### Post by bunny rabbit on 2010-04-27
Hey pi/roman, That guide is excellent!

---

### Post by pi/roman on 2010-04-28
> **bunny rabbit said:**
> Hey pi/roman, That guide is excellent!
Thanks, it does need a little bit of touching up but there hasn't seemed to be much interest in it so I haven't bothered much with it.

---

