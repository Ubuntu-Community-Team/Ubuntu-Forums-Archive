---
title: "no display in xorg.config file?"
date: 2008-09-22
forum: Hardware
---

### Post by orygunpenguin on 2008-09-22
there doesn't seem to be any driver info in my x11.config. video card is a radeon mobility 7500. Is this handled anywhere else? 


[ATTACH]86094[/ATTACH]

---

### Post by Kevbert on 2008-09-22
Unless you have any problems you don't need a defined driver.  But if you want to use one you can use this:
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"ati"
EndSection
```

---

### Post by orygunpenguin on 2008-09-22
is there any other way to confirm that the proper driver for the card is installed? 'lshw -class video' shows the card but again no driver is listed. 
I've tried a few things mentioned in other's threads but it seems something is amiss and I am unsure of where to go from here. 
Thanks

---

### Post by Kevbert on 2008-09-23
Here's my video (from your command)
```
  *-display               
       description: VGA compatible controller
       product: G70 [GeForce 7600 GS]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list
       [COLOR="Red"]configuration: driver=nvidia latency=0 module=nvidia[/COLOR]
```
If you're saying that nothing is displayed under configuration then it's more than likely that you are using the generic, built in driver.  It may be worth adding the previously mentioned driver to xorg,conf  You'll need to reboot to use the driver.

---

### Post by orygunpenguin on 2008-09-23
I added the generic driver to xorg.conf, still no video driver listed with lshw -class video (same output after reboot) 

I may look at an alternative distro. PClos didn't have anywhere near the hardware problems Ubuntu has on this machine. I don't really care if it is a slightly older kernel. This sort of stuff is what made me give up on redhat some 6 years ago. 
as long as pretty generic harware has problems, I don't think the dream of a massive migration from windows is in the cards yet unfortunately.

---

### Post by markbuntu on 2008-09-23
xorg.conf is being deprecated. This is not an Ubuntu issue, it is where Xorg is going. No matter what distro you use, if it uses X, you will have the same experience. If you want to find out what driver your card is using you can look in the Xorg.0.log.

---

### Post by orygunpenguin on 2008-09-24
Ah , som light on the subject. I will give it a try 
e
Thanks

---

### Post by Richard9795 on 2008-09-28
i somehow got a driver for this card, and it is up and running. i can share my xorg.conf with anyone with this problem:

its kind of long:

Section "Device"
Identifier "ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
Driver "radeon"
BusID "PCI:1:0:0"
Option "AGPMode" "4"
Option "AGPFastWrite" "True"
Option "EnablePageFlip" "True"
Option "AGPSize" "32"
Option "DRI" "true"
Option "EnableDepthMoves" "true"
Option "AccelMethod" "XAA"
Option "NoAccel" "False"
Option "XAANoOffscreenPixmaps"
Option "ColorTiling" "on"
Option "RenderAccel" "true"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-49
VertRefresh 43-72
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Radeon Mobility 7500 M7 (RV200 LW)"
Monitor "Generic Monitor"
DefaultDepth 16
SubSection "Display"
Depth 1
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection
EndSection

---

