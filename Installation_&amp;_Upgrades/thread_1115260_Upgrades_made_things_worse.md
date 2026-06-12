---
title: "Upgrades made things worse"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by 2weird on 2009-04-03
I had been having problems running my ATI Radeon X1650 graphics card drivers (restricted) on Ubuntu 8.04. I need the driver so I can run dektop effects. The problem is that when I enable the restricted driver and refresh, nothing is diplayed. Recently I had formated my Ubuntu partition and installed Ubuntu 8.10. When I first installed it Desktop effects was running perfectly. Then the problems started.
The update manager told me that there are 300 updates to be installed so I went ahead and installed the packages. I was told to restart the computer and when I did I was experiencing the problems I have been facing before in Ubuntu 8.04. Is there a way of knowing which packages i have recently updated and undo the upgrade degrading the packages??

---

### Post by leandromartinez98 on 2009-04-03
My experience with ATI graphic drivers is that they are not well incorporated into the distribution, but their instalation is quite straightforward. Instead of downgrading, I suggest that you download the driver instalation package from here:


[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Choose your platform and install the driver just by making the downloaded file executable and running it as root. Don't care about building the packages for Ubuntu, the instalation is just too simple using the default program. Then, rebooting the machines will get your graphics to work as best as they can.

Be careful only with one thing: each time there is kernel upgrade, repeat the operation, preferentially downloading the latest driver. When a kernel upgrade occurs your previous installed driver will stop working.

Not mention that it only in the latest driver versions that ATI included support for OpenGL within visual effects.

And don't forget to disable the drivers you are using now before installing the new ones.

---

### Post by 2weird on 2009-04-03
> **leandromartinez98 said:**
> 

Be careful only with one thing: each time there is kernel upgrade, repeat the operation, preferentially downloading the latest driver. When a kernel upgrade occurs your previous installed driver will stop working.


This makes sense. My kernel was upgraded when the problems where happening.
Thanks I will install the amd version of the drivers and see what happens.

---

### Post by 2weird on 2009-04-03
Nope it didn't work. In fact it made things worse.
After the driver installation I was still experiencing the same problem so I went to recovery mode to fix x server. Usually the graphics driver will be disabled and you can log in normally. Now nothing shows even after xfix. Since there is nothing on my new installation I am thinking of moving to a new Linux distro maybe Linux Mint. Does it have the same problem with ATI graphics cards?

---

### Post by leandromartinez98 on 2009-04-03
Sorry about that. There are some tweaks suggested by the ATI developers in their site, maybe you should take a look. I would bet on that rather than changing distro, since the driver on all distros are essentially the same.

---

### Post by 2weird on 2009-04-04
Ok I installed linux mint and got the ati driver and the catalyst control center working by going to aticonfig. It seems the problem was that I had to specify the resolution via command line. Yet I still can't enable desktop effects. It asks me to enable the fglrx drivers which should be enabled if ccc is running. When I press enable it gives me the same problems.

Should I enable it and then run aticonfig ??

Edit:
The funny thing is desktop effects works on the live cd but not after installation.
Also I believe I am running the non proprietary version of the driver and desktop requires proprietary.

Here is my xorg.conf
```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "TexturedVideoSync" "on"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1152x864"
	EndSubSection
EndSection


```

---

### Post by 2weird on 2009-04-04
Solved!!

---

