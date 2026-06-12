---
title: "Touchpad hardware buttons not working"
date: 2019-11-01
forum: Hardware
---

### Post by blecky80 on 2019-11-01
Hello,

since I updated some time ago to Bionic Beaver I got the problem that both hardware buttons of the touchpad stop working. The buttons of the trackpoint are working as they should.
The Laptop is a Lenovo Edge E520. Following some first results:

```

xinput --list &#9121; Virtual core pointer id=2    [master pointer (3)]
&#9116; &#8627; Virtual core XTEST pointer id=4    [slave pointer (2)]
&#9116; &#8627; TPPS/2 IBM TrackPoint id=12    [slave pointer (2)]
&#9116; &#8627; SynPS/2 Synaptics TouchPad id=11    [slave pointer (2)]
&#9123; Virtual core keyboard id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard id=5    [slave keyboard (3)]
    &#8627; AT Translated Set 2 keyboard id=10    [slave keyboard (3)]
    &#8627; Video Bus id=7    [slave keyboard (3)]
    &#8627; Power Button id=6    [slave keyboard (3)]
    &#8627; ThinkPad Extra Buttons id=13    [slave keyboard (3)]
    &#8627; Video Bus id=8    [slave keyboard (3)]
    &#8627; Integrated Camera: Integrated C id=9    [slave keyboard (3)]


```

```
cat /proc/bus/input/devices 
I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: PROP=0
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input2
U: Uniq=
H: Handlers=sysrq kbd event2 leds 
B: PROP=0
B: EV=120013
B: KEY=402000000 3803078f800d001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input4
U: Uniq=
H: Handlers=mouse0 event3 
B: PROP=9
B: EV=b
B: KEY=6420 30000 0 0 0 0
B: ABS=260800011000003

I: Bus=0011 Vendor=0002 Product=000a Version=0000
N: Name="TPPS/2 IBM TrackPoint"
P: Phys=synaptics-pt/serio0/input0
S: Sysfs=/devices/platform/i8042/serio1/serio2/input/input5
U: Uniq=
H: Handlers=mouse1 event4 
B: PROP=21
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0019 Vendor=17aa Product=5054 Version=4101
N: Name="ThinkPad Extra Buttons"
P: Phys=thinkpad_acpi/input0
S: Sysfs=/devices/platform/thinkpad_acpi/input/input6
U: Uniq=
H: Handlers=rfkill kbd event5 
B: PROP=0
B: EV=13
B: KEY=10040 0 18040000 0 50100000000000 0 1701b02102004 c000280041114000 10e000000000000 0
B: MSC=10

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:3b/LNXVIDEO:00/input/input7
U: Uniq=
H: Handlers=kbd event6 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input8
U: Uniq=
H: Handlers=kbd event7 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input9
U: Uniq=
H: Handlers=event8 
B: PROP=0
B: EV=21
B: SW=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input10
U: Uniq=
H: Handlers=event9 
B: PROP=0
B: EV=21
B: SW=4

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input11
U: Uniq=
H: Handlers=event10 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0003 Vendor=5986 Product=03b3 Version=0105
N: Name="Integrated Camera: Integrated C"
P: Phys=usb-0000:00:1a.0-1.5/button
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input12
U: Uniq=
H: Handlers=kbd event11 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0
```

I've run evtest as well, but there is complete no reaction to the hardware buttons.
The touchpad itself is working fine.

Thanks for your support.
Regards,
 Björn

---

### Post by mörgæs on 2019-11-03
Hi, welcome to the fora.

The first unspecific test when troubleshooting this kind of problems is often: How does it work in a live boot of 19.10?

---

