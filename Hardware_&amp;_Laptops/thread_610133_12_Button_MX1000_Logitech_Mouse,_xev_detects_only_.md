---
title: "12 Button MX1000 Logitech Mouse, xev detects only 5 Buttons"
date: 2007-11-11
forum: Hardware &amp; Laptops
---

### Post by fung on 2007-11-11
First of all, I have searched the forums using many different different combinations of words and have many different guides and everything but I have found no description or solution of my problem except [http://ubuntuforums.org/showthread.php?t=173500](http://ubuntuforums.org/showthread.php?t=173500) which similar to what I'm experiencing. I've already consulted the MX1000 guide at [https://help.ubuntu.com/community/MX1000Mouse](https://help.ubuntu.com/community/MX1000Mouse) but it doesn't help at all.

Basically, I think the problem is the OS isn't detecting my other mouse buttons. I have to admit I'm a bit of a noob when it comes to Linux. Xev says my thumb buttons map to 2 and 3 and the middle thumb button and horizontal scroll don't even register. My mouse is part of the MX3100 wireless keyboard/mouse combo so there's a receiver that connects to the ps/2. 

I'm running gutsy
Here's my /proc/bus/input/devices
```
david@Asus-Linux:~$ cat /proc/bus/input/devices
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=40001
B: SND=6

I: Bus=0011 Vendor=0002 Product=0002 Version=0042
N: Name="PS2++ Logitech MX Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input3
U: Uniq=
H: Handlers=mouse1 event3 
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=143

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=button_power/button/input0
S: Sysfs=/class/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/class/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=3
B: KEY=100000 0 0 0

```

Here's my most recent iteration of xorg.conf that didn't break x
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
        Option          "Protocol"              "auto"
	Option		"Emulate3Buttons"	"false"
        Option          "Buttons"               "7"
        Option          "ZAxisMapping"          "6 7"
        Option          "ButtonMapping"         "1 2 3 6 7 4 5 6"
EndSection
```

Any help would be appreciated. Thanks

---

