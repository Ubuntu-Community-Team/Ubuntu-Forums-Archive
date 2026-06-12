---
title: "Trackpad not working on new install of 16.04.1"
date: 2017-01-17
forum: Hardware
---

### Post by cmit2 on 2017-01-17
I installed Ubuntu on Toshiba Sattelite S55-A5295. All seems well except for the trackpad. It does not work. A bus mouse does work.

I did find this info:

I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input13
U: Uniq=
H: Handlers=mouse1 event6 
B: PROP=5
B: EV=b
B: KEY=e520 10000 0 0 0 0
B: ABS=660800011000003

So it seems it sees the trackpad?

Any help would be appreciated.

---

### Post by cmit2 on 2017-01-18
Sorry to bump this but I am still stuck. I have looked around a lot, seen problems but no solutions. I am new to this and could really use some help or idea. Thanks.

---

### Post by gupperino on 2017-01-19
It could be a driver error, but it might also be a physical issue with the trackpad. Honestly I'm not too sure what you can do at this point. Do some research on your laptop model and see what you find relating to the compatibility. Maybe you could try a different distro and see if it's a hardware or software problem.

---

### Post by mörgæs on 2017-01-19
Yes, the general advice when dealing with new hardware is to try more distros, for example 16.10 and 17.04 (development version).

---

