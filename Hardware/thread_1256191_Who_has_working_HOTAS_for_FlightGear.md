---
title: "Who has working HOTAS for FlightGear"
date: 2009-09-02
forum: Hardware
---

### Post by Keith_Beef on 2009-09-02
I've been reading that the Saitek x52 support is broken in recent kernels, and from looking at the bug reports it looks like it will not be supported in future. Blame the hardware manufacturers, perhaps, for dishonestly claiming that the hardware supports certain functions or has certain features, but this really annoys users whose hardware worked in earlier kernels and suddenly is turned into a paperweight.

So I'm looking for a HOTAS set-up for older planes in FlightGear, to replace the yoke that I use for modern planes.

I'm tempted by the CH Products Fighterstick and ProThrottle, but at $150 each, I'm looking for confirmation that they will work with kernel 
2.6.28-15 and up.

Is there an easy way fro, the command line to see if a controller is claiming to support BTN_DIGI and BTN_TOUCH?

For example, when I plug in my ThrustMaster Firestorm Dual Power game controller:

```

cat /proc/bus/input/devices
..snip..
I: Bus=0003 Vendor=044f Product=b300 Version=0110
N: Name="THRUSTMASTER FireStorm Dual Power"
P: Phys=usb-0000:00:1a.7-2.3/input0
S: Sysfs=/devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2.3/1-2.3:1.0/input/input9
U: Uniq=
H: Handlers=event5 js0 
B: EV=20001b
B: KEY=1fff000000000000 0 0 0 0
B: ABS=30063
B: MSC=10
B: FF=107030000 0
```

How do interpret those numbers?

I'm sure there must be somebody on here with the CH products HOTAS... who could post here the cat /proc/bus/input/devices output.

K.

---

### Post by Keith_Beef on 2009-10-20
Bump... after seven weeks of inactivity.
Doesn't this interest anybody apart from me?

K.

---

### Post by i.r.id10t on 2009-10-20
I'd post over on flightgear.org/forums

---

