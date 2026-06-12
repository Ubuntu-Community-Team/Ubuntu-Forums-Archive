---
title: "SiS UniVGA3"
date: 2010-10-13
forum: Hardware
---

### Post by Xilmwa on 2010-10-13
The story goes like this: I install Ubuntu 10.04 on an old PC I had lying around with integrated graphics: SiS UniVGA3 apparently, and everything works great. I upgrade to 10.10, still everything's running fine. I decide I want to change my login wallpaper, and install gdm2setup, meanwhile a kernel update is going on. I reboot into this 960x600 (or something similar) resolution that isn't even fitting on my screen, and it won't let me set back to 1024x768. I figure I must have messed something up to the point of no return, so I do a clean install of Ubuntu 10.10 thinking it would fix the problem; no.

My next idea was to reinstall Ubuntu 10.04 and do an upgrade from there, but I figured I'd ask if anyone had a better idea.

Here's the output of lspci | grep VGA
```
xilmua@Xilmua-ubuntu:~$ lspci | grep VGA
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
```This may also be a clue to the puzzle:
```
xilmua@Xilmua-ubuntu:~$ cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
xilmua@Xilmua-ubuntu:~$ xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
xrandr: Failed to get size of gamma for output default
```
```
xilmua@Xilmua-ubuntu:~$ gtf 1024 768 60

  # 1024x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 64.11 MHz
  Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync

xilmua@Xilmua-ubuntu:~$ xrandr --newmode "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync
xrandr: Failed to get size of gamma for output default
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  151 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  19
  Current serial number in output stream:  19
```

---

### Post by Xilmwa on 2010-10-14
I booted from the Ubuntu 10.04 desktop CD, and got the same results: 960 by some nonsense. Any idea what's going on here?

---

### Post by Xilmwa on 2010-12-05
I did a little bit more digging and found that the problem was my monitor wasn't being detected right. I have a Dell P990 monitor, so anyone with that who might happen to stumble across this: hit alt+f2 and type "gksudo gedit /etc/X11/xorg.conf" without quotes.

Paste this in, save, and reboot.

```
Section "Device"
	Identifier "Configured Video Device"
	Driver "sis"
EndSection

Section "Monitor"
	Identifier "Configured Monitor"
	HorizSync 30-96
	VertRefresh 40-120
EndSection

Section "Screen"
	Identifier "Default Screen"
	Monitor "Configured Monitor"
	Device "Configured Video Device"
EndSection
```

---

