---
title: "Multi touch trackpad gestures in 11.04"
date: 2011-05-11
forum: Hardware
---

### Post by skinns on 2011-05-11
Hi, Just installed 11.04 on a Samsung 900x3a, mostly works fine, but I can't get 3 and 4 finger gestures to work (two finger scrolling and right clicking works).

I followed the instructions here
[https://wiki.ubuntu.com/Multitouch/Testing/CheckingMTDevice](https://wiki.ubuntu.com/Multitouch/Testing/CheckingMTDevice)

Here's the output
sudo lsinput/dev/input/event7
   bustype : BUS_I8042
   vendor  : 0x2
   product : 0x7
   version : 433
   name    : "SynPS/2 Synaptics TouchPad"
   phys    : "isa0060/serio1/input0"
   bits ev : EV_SYN EV_KEY EV_ABS


sudo mtdev-test /dev/input/event7
error: could not grab the device


3 and 4 finger gestures work in windows, so the trackpad can definitely do it, does anyone know how to get it working?

Thanks

---

### Post by prunch1910 on 2011-05-12
Edited to remove mistake

---

### Post by lumix on 2011-05-29
Same result.

Bump.

---

### Post by jonathon6017 on 2011-06-02
bump

---

