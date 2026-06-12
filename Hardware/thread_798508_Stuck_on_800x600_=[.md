---
title: "Stuck on 800x600 =["
date: 2008-05-18
forum: Hardware
---

### Post by blizma on 2008-05-18
[EDIT] Xubuntu, not kubuntu!

Hi guys.

I am having trouble getting other screen reolutions. The hghest res i can have is 800x600 =[
I read about doing something in the xorg but i dont see anything i can do with mine. Also i tried a '2-wire technique'. The other resolutions did show up, but when i selected i just got black screen.

This is on a Toshiba Satellite Pro L20

Please help :D




Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbVariant"	"a"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by Mhurst1 on 2008-05-18
Did you try using the restricted driver?

---

### Post by blizma on 2008-05-18
> **Mhurst1 said:**
> Did you try using the restricted driver?

No idea what that is :D

PLease explain =[

---

### Post by teaker1s on 2008-05-18
System>Administration>Hardware drivers

it will list a restricted driver.
failing that you can use "envy" installer for nvidia or ati

if your graphics are not ati or nvidia then 

Applications>accessories>terminal
type in this code and post output

```
lspci -v
```

---

### Post by blizma on 2008-05-18
```
phill@JahPhill:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at b0080000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at b0000000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: fast devsel
	Memory at 30000000 (32-bit, non-prefetchable) [disabled] [size=512K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
	Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1840 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04) (prog-if 20 [EHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at b0040000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=08, sec-latency=32
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: b0100000-b01fffff
	Capabilities: <access denied>

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1c00 [size=256]
	I/O ports at 18c0 [size=64]
	Memory at b0040800 (32-bit, non-prefetchable) [size=512]
	Memory at b0040400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04) (prog-if 00 [Generic])
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: medium devsel, IRQ 19
	I/O ports at 2400 [size=256]
	I/O ports at 2000 [size=128]
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, medium devsel, latency 0

00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04) (prog-if 80 [Master])
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 21
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 18b0 [size=16]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: medium devsel, IRQ 11
	I/O ports at 20a0 [size=32]

06:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, medium devsel, latency 168, IRQ 17
	Memory at b0100000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=06, secondary=07, subordinate=08, sec-latency=176
	Memory window 0: 34000000-37fff000 (prefetchable)
	Memory window 1: 38000000-3bfff000
	I/O window 0: 00003400-000034ff
	I/O window 1: 00003800-000038ff
	16-bit legacy interface ports at 0001

06:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at 3000 [size=256]
	Memory at b0101000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
	Subsystem: Intel Corporation Unknown device 2741
	Flags: bus master, medium devsel, latency 32, IRQ 16
	Memory at b0102000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

```




For some reason i cant find administrator anywhere :S

---

### Post by teaker1s on 2008-05-18
**Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)**
915 resolution is now superseeded by xserver-xorg-video-intel

```
sudo apt-get  install xserver-xorg-video-intel
```
and reboot

if it's already installed then good, if not let it install.

I'll look for a howto if you still have issues

---

### Post by blizma on 2008-05-18
Reading package lists... Done
Building dependency tree       
Reading state information... Done
915resolution is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



=/

---

### Post by teaker1s on 2008-05-18
okay try 
```
sudo apt-get  install xserver-xorg-video-intel
```

---

### Post by blizma on 2008-05-18
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-intel is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```


aww =[

---

### Post by teaker1s on 2008-05-18
okay have a look at this howto 
[http://ubuntuforums.org/showthread.php?t=351647&highlight=resolution]("http://ubuntuforums.org/showthread.php?t=351647&highlight=resolution")

---

### Post by blizma on 2008-05-18
followed the instructions there.
For some reason i don't have application-system-preferences as well as an admin option =/

I just have, Applications-settings-settings manager then from there display, and still don't have 1024 =[ =[

Man this is iterating.

Maybe i have to enable what he has done somehow?
If it makes a difference, i installed and am using compiz =/

---

### Post by teaker1s on 2008-05-18
okay we have identified your graphics hardware, that you have the intel resolution packages installed. 
The howto was the only one I could find with a quick search. You may find more help with a thread in beginners section titled intel 915 resolution help

---

### Post by blizma on 2008-05-18
Followed another tut, no success =[

Is it possible to do vnc or remote desktop with you?
I realy have NO idea what im doing :D


EDIT: omg i might be the most stupid person, i clicked the wrong thing :d i have xubuntu not kubuntu =D >BLUSH<

---

### Post by teaker1s on 2008-05-18
while I am trying to help you I will decline vnc or remote desktop, this is not because I don't want to help. In fact I would like to help but I don't want to remotely break your desktop.

I will have another look around forums for a more upto date thread, if you can't get the resolution higher in system settings

We used to dpkg-reconfigure xserver-xorg to reconfigure graphics and monitor, but in hardy these have been removed. I can only find mention of a more advanced gui on hardy heron for selecting graphics and monitor along with a whole list of bugs.
If you fancy a look then
```
gksudo displayconfig-gtk
``` (works on ubuntu, not sure on kubuntu)
other than this I would suggest a post in beginners section as my intel graphics experience is limited to older distro's

---

### Post by blizma on 2008-05-18
I dont mind if it breaks, or anything, its freshly formated xubuntu with xp dualboot i wouldnt loose anything anyway and i only use it test test stuff and to play around with ;) :D

Thanks so much for all your help so far =D

---

### Post by blizma on 2008-05-19
Maybe i should try running Ubuntu live disk to see if it makes any difference. As i understand ubuntu uses Gnome, and xubuntu xfce. Maybe gnome would run better?
I tried that command in termanl where you can config everything, but it just asks about my keyboard and not graphics card =S
Stupid question, but do i need to install a graphics driver or...? =D

---

### Post by teaker1s on 2008-05-19
I would suggest a new thread with intel 915 resolution in beginners, not because I don't want to help- in fact I do and I feel this will get you more advice than I can give on the subject.:KS

---

