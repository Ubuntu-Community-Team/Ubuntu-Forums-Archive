---
title: "two ati graphic cards HD 3650 with fglrx driver doesn't work together"
date: 2008-09-15
forum: Hardware
---

### Post by masc-at on 2008-09-15
hi!

i'm pretty new to ubuntu. i installed a amd 64bit machine with hardy this weekend. everything works fine with one exeption: the graphic cards. i need four monitors on this machine, preferable with different screens (to send the output to monitor three, for example). 

if i'm just using one of them (both are PCIe x 16 asus radeon hd 3650) everything works fine, on both connectors are the monitors working. but if i configure X to use both at one time, the fglrx driver mentions about 
(EE) fglrx(2): Multiview is not supported on the first adapter; this screen will now shutdown. 
and only two monitors (on the first adapter) are working. using amdcccle didn't help me too. 

i tried to disable AIGLX and dri without success. the other non-proprietary ati and radeonhd driver doesn't support this chipset with the versions shipped with  hardy. 

does anybody use the fglrx driver with two ident graphic cards? or another ideas? 

bye...masc.

ps. i forgot to save the config and X.log , i'll post them tomorrow in the morning.

---

### Post by illdred on 2008-09-24
Hey
 right on, I'm glad you are working on four monitors too.
I've got a pair of radeon HD 2400 cards and I'm still trying to get all four screens working.

Let me know if you make any progress!

---

### Post by markbuntu on 2008-09-24
You need to configure the cards with aticonfig. Type aticonfig --help to get a list of options. This is fairly new so you need one of the latest drivers, 8.8 or 8.9. if you do not have the latest driver you can follow these directions, Method 2:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

There is a thread around here where some guy is running 4 monitors with HD3650 cards so it can be done.

---

### Post by cobra7 on 2008-09-26
Same prablem with two HD3850 - both fglrx 8.522 and 8.532 complain about disabled Multiview, however fglrx 8.501 works, but there are stability issues (hardlocks etc).

---

### Post by markbuntu on 2008-09-26
The newer drivers from ati 8.8 and 8.9 offer more features for multiple cards and monitors. If you are using an older driver you might consider updating.

---

### Post by Continental Driftt on 2008-12-11
Both illdred and I were able to get two ATI Radon HD 2400 cards working simultaneously.  I first ran /sbin/lspci -n to get the addresses of the two cards:

```
...
00:1f.2 0106: 8086:2922 (rev 02)
00:1f.3 0c05: 8086:2930 (rev 02)
01:00.0 0300: 1002:94c1
03:00.0 0604: 10b5:8111 (rev 21)
04:00.0 0300: 1002:94cc
```

The 1002 lines are the ones I needed.  Then I edited /etc/ati/amdpcsdb by adding these lines:

```
[AMDPCSROOT/SYSTEM/2ID-1002-94c1-0/DDX]
MultiviewEnabled=V1
MultiviewHeterogeneous=V1
[AMDPCSROOT/SYSTEM/2ID-1002-94cc-0/DDX]
MultiviewEnabled=V1
MultiviewHeterogeneous=V1
```

illdred says that the MultiviewHeterogeneous=V1 lines are not necessary.  I also added the same lines to /etc/ati/amdpcsdb.default, which illdred also says is not necessary.  YMMV.

Then I added the extra devices and monitors to my /etc/X11/xorg.conf file:

```
# Xorg configuration created by system-config-display

Section "ServerLayout"
	Identifier     "single head configuration"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Screen         "aticonfig-Screen[0]-1" LeftOf "aticonfig-Screen[0]-0"
	Screen         "aticonfig-Screen[1]-0" LeftOf "aticonfig-Screen[0]-1"
	Screen         "aticonfig-Screen[1]-1" RightOf "aticonfig-Screen[0]-0"
	InputDevice    "Keyboard0" "CoreKeyboard"
	Option	    "Xinerama" "on"
	Option	    "Clone" "off"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "dri"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "on"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:4:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-1"
	Driver      "fglrx"
	BusID       "PCI:4:0:0"
	Screen      1
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]-1"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-1"
	Device     "aticonfig-Device[0]-1"
	Monitor    "aticonfig-Monitor[0]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]-0"
	Device     "aticonfig-Device[1]-0"
	Monitor    "aticonfig-Monitor[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]-1"
	Device     "aticonfig-Device[1]-1"
	Monitor    "aticonfig-Monitor[1]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

And then restarted my machine.  I was very, very happy.

---

### Post by markbuntu on 2008-12-11
The latest ati drive 8.12 also supports surroundview now which will allow some pci cards to be used with certain IGP gpus for multiple monitors according to their release notes. It was very vague.

---

### Post by Ricercar on 2009-02-12
> **Continental Driftt said:**
> Both illdred and I were able to get two ATI Radon HD 2400 cards working simultaneously.  I first ran /sbin/lspci -n to get the addresses of the two cards:

And then restarted my machine.  I was very, very happy.


Could you kindly retrace your steps in getting this to work. I have 3 ATI Radeon HD 3600 cards on my Intrepid. I have tried in vein to get the system to display on any of the other two cards. 
I have tried through ATI  Catalyst Control center, but all that does is allow me to use two monitors (off one of the Graphic cards).

Reading your post. I did the following
aticonfig --adapter=all --initial 
which generated for me an  xorg.conf file

Then I tried rebooting but still nothing. Much appreciated if you would show me the basic steps of creating xorg.conf file and what should be done.

---

### Post by Ricercar on 2009-02-12
Never mind. Got it to work. On Intrepid all I did was replace the xorg.conf with the default simple version. Then issued executed aticonfig --adapter=all --initial=dual-head  and it generated the xorg.conf
On rebooting all monitors working. Proceeed to use ati catalyst control center to adjust the resolutions and display positions as well as enable xinemera. Only thing missing would be the 3D effects.

---

