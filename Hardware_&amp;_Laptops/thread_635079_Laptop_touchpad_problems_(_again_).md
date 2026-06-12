---
title: "Laptop touchpad problems ( again )"
date: 2007-12-08
forum: Hardware &amp; Laptops
---

### Post by linuxonbute on 2007-12-08
I have just bought a Zepto Znote 3215W and have installed Gutsy on it.

It mostly works well but i have a problem with the touchpad.

cat /proc/bus/inpuUbuntu

```

I: Bus=0011 Vendor=0002 Product=0005 Version=0063
N: Name="ImPS/2 Logitech Wheel Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=mouse1 event2 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

```

The touchpad works well TOO WELL!!!!!

as soon as I touch it with my finger if it's over a link or an icon it will be as if I have selected it and takes me to a different web site or launches a program.

I have tried many of the suggestions on this site and others but i just found one which said I should install the latest synaptics driver.

This didn't work but the trouble shooting file which came with it says 
```

If you are using a 2.6 linux kernel, check the /proc/bus/input/devices
file. The touchpad must be identified a "SynPS/2 Synaptics TouchPad"
or an "AlpsPS/2 ALPS TouchPad". If it is identified as a "PS/2 Generic
Mouse" or "PS/2 Synaptics TouchPad", something is wrong.

```

The question is where do I go with this, anyone any ideas?

---

### Post by rocko_mtv on 2008-01-18
Did you solve your touchpad issue yet?

---

