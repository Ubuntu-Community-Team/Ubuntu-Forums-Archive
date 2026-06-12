---
title: "ATI HD 2900 &amp; The AMD Unsupported Hardware Watermark"
date: 2009-05-12
forum: Hardware
---

### Post by patrickalexson on 2009-05-12
Alright.

This is the ONLY problem I have faced with 9.x
If this could be resolved, I would be a very happy end user.
[B]
I am very new to linux so bare with me as I am just a pawn.[/B]

So ive got the Sapphire ATI HD 2900 PCIe card, I enabled the restricted drivers and now when I boot up my system, I get this god-forsaken watermark 'AMD Unsupported Hardware'

I have tried searching the web for answers and the only one I found was about copying over a certain 'control' file. There is already one present so I thought eh, thats probably not going to fix it. Other users were saying it worked some times, and didnt other times.

**MISSION:**

**PRIMARY OBJECTIVE:** Find a stable ATI drive as the one I use hates applications that run in 'full screen' mode and blurs text at the bottom of the screen until I move the mouse over it.

**SECONDARY OBJECTIVE:** If we cannot get a stable driver, then I need to figure out a way to DISABLE the watermark as it overlaps all my applications and in Warzone 2100 I cant see the dam minimap

---

### Post by patrickalexson on 2009-05-12
bump

---

### Post by patrickalexson on 2009-05-12
bump again, someone have a suggestion? it looks like my drivers are up to date

---

### Post by patrickalexson on 2009-05-13
... can I get at least a 'hey we are working on finding a solution'?

---

### Post by patrickalexson on 2009-05-13
bump again, someone, please?

---

### Post by Helekryl on 2009-09-20
**Concerning the primary objective:**
Try to download the most recent linux driver from ati.amd.com. Your model is supported since fglrx v8.41.7: [http://wiki.cchtml.com/index.php/Hardware#RADEON_HD](http://wiki.cchtml.com/index.php/Hardware#RADEON_HD)

After downloading, install it using, for example, this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually)
(fits not only for Intrepid - I've successfully applied it to Jaunty fglrx installation). But note that:
a) the list of required dependencies mentioned ("sudo apt-get install build-essential...") is missing ia32-libs and linux-headers-$(uname -r) 
b) sometimes it is nesessary to perform the "dpkg -i ..." option from a root console without starting X (in my case, the primary deb package gave me an error message while trying to install it over the previous one from X functioning, but installed correctly in text mode)
c) after installation, if X server cannot start, it's usually xorg.conf fault. Better to have a previous version (any) of fglrx which worked on your system at least without crash, in order to have a xorg.conf which doesn't crash X server and then configure it with Catalyst Control Center.


If no correct xorg.conf is present and amdcccle does not want to access it, the only option is a manual xorg.conf editing, though this is not the best option. In order to make X server function properly, the config should contain something like this:

```

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1440x900"
	EndSubSection
EndSection
```

Especially, if no DefaultDepth and Depth are specified in your config, X server tries to start with default color depth value of 8, which is not supported by fglrx. The "Driver" option with a value "fglrx" is also essential.


**Concerning the secondary objective:**
No matter if you succeeded at the previous objective or not, download xorg-driver-fglrx for Intrepid from, for example, [http://packages.ubuntu.com/intrepid/xorg-driver-fglrx](http://packages.ubuntu.com/intrepid/xorg-driver-fglrx) (don't forget to select the right architecture, i386 or amd64), unpack it w/o installation, and copy the files "control" and "signature" from <unpacked folder>/data/etc/ati/ to /etc/ati, overwriting the same files there. Then reboot.

---

