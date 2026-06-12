---
title: "Maedia Keys - second touchpad"
date: 2008-07-01
forum: Hardware
---

### Post by bwiklak on 2008-07-01
Hi, I own Acer Aspire 5920G. 

As it was mentioned in another threads this notebook has multimedia keys that are visible as second Synaptic device.

I didnt found any solution to make them working properly and sometimes I touch them unintentionally and it is annoying, I decided to turn them off. 

And here is my prolem.

In ubuntu 8.04, when I delete all lines coresponding touchpad in Xorg, both touchpads - real one and media keys still work (sic!)

As you can see in my "cat /proc/bus/input/devices":

```

I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio3/input0
S: Sysfs=/devices/platform/i8042/serio3/input/input9
U: Uniq=
H: Handlers=mouse2 event9 
B: EV=b
B: KEY=6420 7001f 0 0 0 0
B: ABS=11000003

I: Bus=0011 Vendor=0002 Product=0007 Version=81b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input10
U: Uniq=
H: Handlers=mouse3 event10 
B: EV=b
B: KEY=6420 7000f 0 0 0 0
B: ABS=11000003

```

I am quite experienced in GNU/Linux but I can't disable second touchpad.

Why without any input in Xorg touchpad still works in Hardy?

Also, I figured that 
```
cat /var/log/Xorg.0.log | grep "ynaptic"
``` 

shows no lines! and two touchpads work.

Can you help me?

---

