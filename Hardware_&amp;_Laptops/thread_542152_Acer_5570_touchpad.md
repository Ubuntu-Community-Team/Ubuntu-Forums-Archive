---
title: "Acer 5570 touchpad"
date: 2007-09-03
forum: Hardware &amp; Laptops
---

### Post by Anacrusis on 2007-09-03
Hello,
I've got Kubuntu 7.04 installed on my Acer 5570 laptop and everything seems to be working very well except for one thing. I cannot get the touchpad to work completely. Scrolling does not work and the 4 way navigational buttons do not work. I've tried everything, searched the forums, google...etc. and cannot find any solutions to this.

$cat /proc/bus/input/devices show that I have a Synaptics touch pad:
I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Synaptics TouchPad"
P: Phys=isa0060/serio4/input0
S: Sysfs=/class/input/input2
H: Handlers=mouse1 ts1 event2
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3


But loading the synaptics driver in xorg.conf results in the follwing error:
Query no Synaptics: 6003C8
(EE) touchpad no synaptics touchpad detected and no repeater device
(EE) touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "touchpad"
(II) UnloadModule: "synaptics"



Does anybody have any thoughts or ideas as to how I could get full use out of my touchpad?

As for the navigational buttons, running xev does not show any output when pressing them, so I'm guessing they also rely on the synaptics driver to work.

Thanks in advance.

---

### Post by Anacrusis on 2007-09-04
Can anybody help?

---

