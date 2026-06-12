---
title: "PS/2 Mouse stopped working, 32bit only"
date: 2013-02-23
forum: Hardware
---

### Post by nicks27 on 2013-02-23
My PS/2 mouse has stopped working after recent updates. I see a pointer in the middle of the screen but the mouse in unresponsive.

The machine is Xubuntu 12.04 (kernel 3.2.0-38),  dual boot 64-bit and 32-bit. The mouse was previously working under both systems (previous kernel versions) but has now stopped working in in 32-bit. The mouse still works fine in when booted in 64-bit.

Some info from the 32-bit system is as follows:

```
$ **uname -a**
Linux sonata 3.2.0-38-generic #61-Ubuntu SMP Tue Feb 19 12:20:02 UTC 2013 i686 athlon i386 GNU/Linux

$ **cat /proc/bus/input/devices | grep -A 7 -B 1 "PS/2"**
I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Generic Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input3
U: Uniq=
H: Handlers=mouse0 event3 
B: PROP=0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0

$ **dmesg | grep "PS/2"**
[    1.366314] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.366940] mousedev: PS/2 mouse device common for all mice
[   11.754041] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input3
```... compared with the 64-bit system:

```
$ **uname -a**
Linux sonata 3.2.0-38-generic #61-Ubuntu SMP Tue Feb 19 12:18:21 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

$ **cat /proc/bus/input/devices | grep -A 7 -B 1 "PS/2"**
I: Bus=0011 Vendor=0002 Product=0005 Version=0000
N: Name="ImPS/2 Generic Wheel Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input3
U: Uniq=
H: Handlers=mouse0 event3 
B: PROP=0
B: EV=7
B: KEY=70000 0 0 0 0

$ **dmesg | grep "PS/2"**
[    1.134344] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.134962] mousedev: PS/2 mouse device common for all mice
[   18.388025] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input3
```Any ideas on how to further diagnose/fix this please?

---

