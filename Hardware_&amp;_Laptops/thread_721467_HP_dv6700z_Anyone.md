---
title: "HP dv6700z Anyone?"
date: 2008-03-11
forum: Hardware &amp; Laptops
---

### Post by le_vainqueur on 2008-03-11
Hi, I'm considering buying an HP dv6700z (the z is for Athalon processors), and I was wondering if anyone has had success with Ubuntu (or any Linux) on this laptop.  There are only a couple of threads on this forum about problems people are having, so I'm hoping that difficulties are more the exception than the rule.  The problems that have been revealed in these posts, however, are about pretty big things (wifi and sound).  A quick Google search suggests that some people have been able to solve these problems.

Also, I couldn't find this model in the hardware testing from Ubuntu.  Not sure what that means.


Thanks,

LV

---

### Post by le_vainqueur on 2008-03-14
*bump*

---

### Post by CalderCoalson on 2008-06-11
Ok, I just got one yesterday, and the only three problems initially were the wireless card, (BCM4328 ) the video card, and suspending.  All were fixed by this morning.

My setup is:
AMD Athlon(TM) 64 X2 Dual-Core Processor TK-57 (1.90 GHz)
15.4" diagonal WXGA High-Definition HP BrightView Widescreen Display (1280 x 800)
2GB DDR2 System Memory (2 Dimm)
NVIDIA GeForce Go 7150M
HP Imprint Finish (Radiance) + Microphone
Wireless LAN 802.11a/b/g/n and Bluetooth
160GB 5400RPM SATA Hard Drive
SuperMulti 8X DVD+/-R/RW with Double Layer Support
6 Cell Lithium Ion Battery

None of the fixes are really that hard, and now it's running beautifully, so I'd say it's well worth it.  I wrote a short guide from what I remember.



**Suspend** ( [http://blog.vaxius.net/?p=43](http://blog.vaxius.net/?p=43) )
Open Terminal and type:
```
	sudo pico /etc/default/acpi-support
```
Then change the following settings to false:
```
	SAVE_VBE_STATE=false
	POST_VIDEO=false
	USE_DPMS=false
```

**Wireless (32-bit with BCM43xx card)** ( [http://ubuntuforums.org/showthread.php?t=616801](http://ubuntuforums.org/showthread.php?t=616801) )
Download and unzip: [http://ubuntuforums.org/attachment.php?attachmentid=50636&d=1195424847](http://ubuntuforums.org/attachment.php?attachmentid=50636&d=1195424847)
You may need an account on the Ubuntu forums.
Open Terminal and type:
```
	sudo apt-get install ndiswrapper
```
Click *System > Administration > Windows Wireless Drivers.*
Click install, and select the *bcmwl5.inf* from wherever you unzipped it.  Restart.

**Video Card**
Make sure you are connected to the internet.
Click *System > Administration > Hardware Drivers*.
Check Enable next to the one titled NVIDEIA accelerated graphics driver.  Restart.

---

