---
title: "Touchpad issue on Gateway LT21 (Acer 532h)"
date: 2010-07-17
forum: Hardware
---

### Post by alluringreality on 2010-07-17
Computer: LT2119U Gateway netbook (rebranded Acer 532h)
Note: Memtest 86+ ran without issue for over 10 hours
OS: 10.04 Ubuntu, Mint, Peppermint live CDs

The touchpad on the netbook jumps around the edges of the screen, and opens items at random when touched. I have tried the Crunchbang Alpha 2 live CD and it loads with a normally working touchpad every time. I've read through a number of things, but I'm still not sure how to get the touchpad in Ubuntu to work the same as Crunchbang.


**Items from /proc/bus/input/devices in Ubuntu distribution**

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input4
U: Uniq=
H: Handlers=mouse0 event4 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0002 Product=0008 Version=0000
N: Name="PS/2 Mouse"
P: Phys=isa0060/serio1/input1
S: Sysfs=/devices/platform/i8042/serio1/input/input7
U: Uniq=
H: Handlers=mouse1 event7 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0002 Product=0008 Version=7326
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input8
U: Uniq=
H: Handlers=mouse2 event8 
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003


**Items from /proc/bus/input/devices in Crunchbang**

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input3
U: Uniq=
H: Handlers=mouse0 event3 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0002 Product=0007 Version=25b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input6
U: Uniq=
H: Handlers=mouse1 event6 
B: EV=b
B: KEY=6420 0 70000 0 0 0 0 0 0 0 0
B: ABS=11000003


**Other Issues I've noticed**
- I get the [http://ubuntuforums.org/showthread.php?t=1443231&page=1](http://ubuntuforums.org/showthread.php?t=1443231&page=1) message on boot, but my Laptop shows the same thing and doesn't seem to have any resulting issues from that.
- Headphone jack works, but speakers do not work. The headphone jack on maximum is about the volume of Windows 7 at 1/2 volume. This happens on both Ubuntu and Crunchbang.

---

