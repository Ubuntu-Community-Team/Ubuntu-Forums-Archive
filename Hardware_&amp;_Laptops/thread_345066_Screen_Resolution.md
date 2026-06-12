---
title: "Screen Resolution"
date: 2007-01-23
forum: Hardware &amp; Laptops
---

### Post by boilermaker on 2007-01-23
Following is my display details:

Intel(R) Graphics Media Accelerator Driver for Mobile Report


Driver Version:		6.14.10.4410
Operating System:		Windows XP* Home Edition, Service Pack 2
Default Language:		English
DirectX* Version:		9.0
Minimum Graphics Memory:	8 MB
Maximum Graphics Memory:	128 MB
Graphics Memory in Use:	10 MB
Processor:		x86 family 6 Model 13 Stepping 8
Processor Speed:		1396 MHZ


*   Accelerator Information   *

Accelerator in Use:		Mobile Intel(R) 915GM/GMS,910GML Express Chipset Family
Video BIOS:		1219
Current Graphics Mode:	1280 by 800 True Color (60 Hz)



*   Devices Connected to the Graphics Accelerator   *


Active Notebook Displays: 1


*   Notebook   *

Monitor Name:		Plug and Play Monitor
Display Type:		Digital
Gamma Value:		3.54
DDC2 Protocol:		Supported
Maximum Image Size:	Horizontal: Not Available
			Vertical:   Not Available
Monitor Supported Modes:
640 by 480 (60 Hz)
800 by 600 (60 Hz)
1024 by 768 (60 Hz)
1280 by 800 (60 Hz)



How should I change the screen resolution to 1280*800


Also eveytime i boot up the system crashes with a message like 
"Failure to load desktop daemon"


How can i Fix it

Thanks in advance:)

---

### Post by Stemp on 2007-01-23
> How should I change the screen resolution to 1280*800

Edit your /etc/X11/xorg.conf (command : gksudo gedit /etc/X11/xorg.conf) 
Look at the Section "Screen"
You should have a line like this 
```
DefaultDepth    24
```
and  lines like that :
```
SubSection "Display"
                Depth           24
                Modes           "800x600" "640x480"
EndSubSection

```

Just add your resolution :

```
                Modes           "1280x800" "800x600" "640x480"
```

---

