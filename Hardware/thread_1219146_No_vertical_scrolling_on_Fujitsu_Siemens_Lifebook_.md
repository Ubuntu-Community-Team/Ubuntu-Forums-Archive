---
title: "No vertical scrolling on Fujitsu Siemens Lifebook S7010D"
date: 2009-07-21
forum: Hardware
---

### Post by p10 on 2009-07-21
I have been unable to get vertical scrolling on my Fujitsu Siemens Lifebook S7010D for as long as I have been running Ubuntu on it (at the moment 9.04). But yesterday I all of a sudden could scroll. I had not made any changes to the setup, so I thought that it had to do with some of the recent updates. 

Today everything is back to normal. No vertical scroll, but now that I know that it is possible to make it work, I want to find out how to make it work!

Now, cat /proc/bus/input/devices gives me this result:
```
I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
U: Uniq=
H: Handlers=event2 
B: EV=21
B: SW=1

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input3
U: Uniq=
H: Handlers=mouse0 event3 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab54
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Fujitsu FUJ02B1"
P: Phys=FUJ02B1/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:07/FUJ02B1:00/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=3
B: KEY=10003 0 0 0 0 0 0 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=40001
B: SND=6

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:02/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=3
B: KEY=3f000b 0 0 0 0 0 0 0

I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Generic Mouse"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input8
U: Uniq=
H: Handlers=mouse1 event8 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

```

After downloading tpconfig and running *sudo tpconfig -i* in a terminal, here is the result:
```
Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
Sensor type: unknown (0).
Geometry: rectangular/landscape/up.
Packets: absolute, 80 packets per second.
Corner taps disabled;		no tap gestures.
Edge motion: none.
Z threshold: 6 of 7.
2 button mode; corner tap is right button click.

```

Any thoughts?

---

### Post by p10 on 2009-07-21
For some reason vertical scrolling just started working again, like yesterday.

Did a quick cat /proc/bus/input/devices, giving this result:
```
I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
U: Uniq=
H: Handlers=event2 
B: EV=21
B: SW=1

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input3
U: Uniq=
H: Handlers=mouse0 event3 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab54
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Fujitsu FUJ02B1"
P: Phys=FUJ02B1/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:07/FUJ02B1:00/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=3
B: KEY=10003 0 0 0 0 0 0 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=40001
B: SND=6

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:02/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=3
B: KEY=3f000b 0 0 0 0 0 0 0

I: Bus=0011 Vendor=0002 Product=0007 Version=0fb1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input9
U: Uniq=
H: Handlers=mouse1 event8 
B: EV=b
B: KEY=6420 0 70003 0 0 0 0 0 0 0 0
B: ABS=11000003

I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Generic Mouse"
P: Phys=synaptics-pt/serio0/input0
S: Sysfs=/devices/platform/i8042/serio4/serio5/input/input10
U: Uniq=
H: Handlers=mouse2 event9 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

```

As you can see, I now have the synaptics touchpad listed. And the "generic mouse" settings have changed. 

Can anyone make sense of this sudden change??

Any idea how I can make this change permanent?

---

