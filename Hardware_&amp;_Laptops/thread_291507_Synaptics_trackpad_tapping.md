---
title: "Synaptics trackpad tapping"
date: 2006-11-02
forum: Hardware &amp; Laptops
---

### Post by Beige on 2006-11-02
I've been trying to disable trackpad clicking on my acer 1692 running 6.06.1, 

I've found loads of threads suggesting i add MaxTapTime=0 to the Synaptics Touchpad device in xorg.conf. Fair enough, but i dont have an entry for a touchpad, the only mouse type device listed is "Configured Mouse".



when i run cat /proc/bus/input/devices it outputs the following

I: Bus=0011 Vendor=0001 Product=0001 Version=abba
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event0
B: EV=120013
B: KEY=6 2000000 43802078 f850f401 f2ffffdf ffefffff ffffffff ffffffff
B: MSC=10
B: LED=7

I: Bus=0011 Vendor=0002 Product=0007 Version=0000
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input2
H: Handlers=mouse0 event1 ts0
B: EV=b
B: KEY=6420 0 7000f 0 0 0 0 0 0 0 0
B: ABS=11000003



The second part being of intrest as it clearly states i have a Synaptics touchpad. Apart from not being in xorg.conf it works flawlessly, even Fn+F7 disables it, as it should.


Any ideas lads? as i'm spent :-k

---

### Post by alohre on 2006-11-03
try setting your driver in xorg.conf to "synaptics" in the mouse section and then add the MaxTapTime to that section.

---

### Post by Predius on 2006-11-03
Read the following from the Ubuntu blog, might help you with this.

[http://ubuntu.wordpress.com/2006/03/24/disable-synaptics-touchpad/](http://ubuntu.wordpress.com/2006/03/24/disable-synaptics-touchpad/)

---

### Post by Beige on 2006-11-04
ok guys, i've tried modifying xorg.conf based on what you mentioned, but anything i tried leads xorg to flip out and leave me at a command prompt :mad:

hmm...

---

### Post by Beige on 2006-11-04
woo, progress

the entry for my mouse now looks like

```
Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "Synaptics"
	Option "SendCoreEvents" "true"
	Option "Device" "/dev/input/mice"
	Option "Protocol" "auto-dev"
	Option "HorizScrollDelta" "0"
	Option "SHMConfig" "on"
EndSection
```

And it all still works, however adding the option max tap time, or running synclient TapButton1=0 still don't work...




Just looked into  /var/log/Xorg.0.log and noticed the following

(II) LoadModule: "Synaptics"
(WW) Warning, couldn't open module Synaptics
(II) UnloadModule: "Synaptics"
(EE) Failed to load module "Synaptics" (module does not exist, 0)

It then goes on to load some wacom modules successfully, not that i have any wacom hardware.

---

