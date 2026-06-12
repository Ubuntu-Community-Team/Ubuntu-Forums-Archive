---
title: "Ubuntu can't detect my Alps touchpad"
date: 2006-08-14
forum: Hardware &amp; Laptops
---

### Post by SparkyFlooner on 2006-08-14
Ubuntu can't detect my Alps touchpad on my Fujutsi Lifebook N-Series laptop.

Fedora detects it, so I know it's in there somewhere.  Ubuntu shows no trace of it in /proc/bus/input/devices.

I still kind of a linux noob, so I don't know how to tell the kernel where hardware is and what driver to use.

Ideas anyone?

( .../input/devices dump from Fedora.)
I: Bus=0011 Vendor=0002 Product=0008 Version=7322
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio4/input0
S: Sysfs=/class/input/input2
H: Handlers=mouse1 event2
B: EV=f
B: KEY=420 0 670000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003

---

### Post by DJ Scribblinni on 2006-08-14
Try this how to and see if anything goes. 
[http://www.ubuntuforums.org/showthread.php?t=78904&highlight=ALPS+TouchPad]("http://www.ubuntuforums.org/showthread.php?t=78904&highlight=ALPS+TouchPad")

---

### Post by SparkyFlooner on 2006-08-15
The problem is it's not enumerated in the devices list.

There's no mouse input device at all in the devices list.

---

### Post by LordMau on 2006-08-29
+1
same issue, different laptop, no entry under /proc/bus/input/devices, so nearly all the other howtos can't be used.

winxp of course had no problem with the touchpad.

---

### Post by LordMau on 2006-09-01
Bumpimg, also tried zenwalk on the same laptop it also did not detect the touchpad during installation and upon operation. 

If this helps I see a common error in ubuntu and zen installs :

hw_random: RNG not ... (sorry forgot exact message, it maybe "detected")

---

### Post by LordMau on 2006-09-03
Tried 2 other livecds. PCLinuxos also did not detect the trackpad. Damnsmall linux did detect it.

Anybody at all with advice? I'd really like to make ubuntu work with the trackpad here.

---

