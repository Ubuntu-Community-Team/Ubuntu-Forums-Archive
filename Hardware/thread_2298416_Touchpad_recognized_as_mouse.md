---
title: "Touchpad recognized as mouse"
date: 2015-10-10
forum: Hardware
---

### Post by zach8321 on 2015-10-10
I'm not quite sure what kind of touchpad I have, although judging by the ELAN touchscreen I'm going to assume that I have an ELAN touchpad as well. I've confirmed that the touchpad ID is 12, because I successfully disabled it.

Running any synclient command just produces
```
Couldn't find synaptics properties. No synaptics driver loaded?
```

I'm on ubuntu 15.04 kernel 3.19.0-28-generic

xinput:
```
&#9121; Virtual core pointer                            id=2     [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4     [slave  pointer  (2)]
&#9116;   &#8627; Razer Razer Blade                           id=13    [slave  pointer  (2)]
&#9116;   &#8627; Razer Razer Blade                           id=15    [slave  pointer  (2)]
&#9116;   &#8627; ELAN Touchscreen                            id=16    [slave  pointer  (2)]
&#9116;   &#8627; Logitech M705                               id=11    [slave  pointer  (2)]
&#9116;   &#8627; Razer Razer Blade                           id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                           id=3     [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; USB Camera                                  id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=17    [slave  keyboard (3)]
    &#8627; Razer Razer Blade                           id=14    [slave  keyboard (3)]

```

cat /proc/bus/input/devices:
```
I: Bus=0019 Vendor=0000 Product=0001 Version=0000N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0


I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
U: Uniq=
H: Handlers=event1 
B: PROP=0
B: EV=21
B: SW=1


I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0


I: Bus=0011 Vendor=0001 Product=0001 Version=ab83
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input3
U: Uniq=
H: Handlers=sysrq kbd event3 
B: PROP=0
B: EV=120013
B: KEY=402000000 3803078f800d001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7


I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:5e/LNXVIDEO:00/input/input6
U: Uniq=
H: Handlers=kbd event4 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0


I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input7
U: Uniq=
H: Handlers=kbd event5 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0


I: Bus=0003 Vendor=1532 Product=011d Version=0111
N: Name="Razer Razer Blade"
P: Phys=usb-0000:00:14.0-5/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5:1.0/0003:1532:011D.0005/input/input8
U: Uniq=
H: Handlers=mouse0 event6 
B: PROP=0
B: EV=17
B: KEY=30000 0 0 0 0
B: REL=3
B: MSC=10


I: Bus=0003 Vendor=1532 Product=011d Version=0111
N: Name="Razer Razer Blade"
P: Phys=usb-0000:00:14.0-5/input1
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5:1.1/0003:1532:011D.0006/input/input9
U: Uniq=
H: Handlers=sysrq kbd event7 
B: PROP=0
B: EV=10001f
B: KEY=3f0003007f 0 0 483ffff17aff32d bf54444600000000 1 130f938b17c007 ffff7bfad941dfff febeffdfffefffff fffffffffffffffe
B: REL=40
B: ABS=3fffff0100000000
B: MSC=10


I: Bus=0003 Vendor=1532 Product=011d Version=0111
N: Name="Razer Razer Blade"
P: Phys=usb-0000:00:14.0-5/input2
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5:1.2/0003:1532:011D.0007/input/input10
U: Uniq=
H: Handlers=sysrq kbd event8 
B: PROP=0
B: EV=120013
B: KEY=1000000000007 ff9f207ac14057ff febeffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7


I: Bus=0003 Vendor=1532 Product=011d Version=0111
N: Name="Razer Razer Blade"
P: Phys=usb-0000:00:14.0-5/input3
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5:1.3/0003:1532:011D.0008/input/input11
U: Uniq=
H: Handlers=mouse1 event9 
B: PROP=0
B: EV=17
B: KEY=70000 0 0 0 0
B: REL=103
B: MSC=10


I: Bus=0003 Vendor=04f3 Product=0423 Version=0110
N: Name="ELAN Touchscreen"
P: Phys=usb-0000:00:14.0-6/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/0003:04F3:0423.0009/input/input12
U: Uniq=
H: Handlers=mouse2 event10 
B: PROP=2
B: EV=b
B: KEY=400 0 0 0 0 0
B: ABS=3273800000000003


I: Bus=0003 Vendor=0bda Product=579f Version=0002
N: Name="USB Camera"
P: Phys=usb-0000:00:14.0-14/button
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-14/1-14:1.0/input/input15
U: Uniq=
H: Handlers=kbd event12 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card1/input16
U: Uniq=
H: Handlers=event13 
B: PROP=0
B: EV=21
B: SW=10


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card1/input17
U: Uniq=
H: Handlers=event14 
B: PROP=0
B: EV=21
B: SW=4


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel HDMI HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:03.0/sound/card0/input18
U: Uniq=
H: Handlers=event15 
B: PROP=0
B: EV=21
B: SW=140


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel HDMI HDMI/DP,pcm=7"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:03.0/sound/card0/input19
U: Uniq=
H: Handlers=event16 
B: PROP=0
B: EV=21
B: SW=140


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel HDMI HDMI/DP,pcm=8"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:03.0/sound/card0/input20
U: Uniq=
H: Handlers=event17 
B: PROP=0
B: EV=21
B: SW=140


I: Bus=0003 Vendor=046d Product=101b Version=0111
N: Name="Logitech M705"
P: Phys=usb-0000:00:14.0-3:1
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.2/0003:046D:C52B.000C/0003:046D:101B.000D/input/input21
U: Uniq=
H: Handlers=mouse3 event11 
B: PROP=0
B: EV=17
B: KEY=ffff0000 0 0 0 0
B: REL=143
B: MSC=10
```

So far all of the solutions I've seen don't work. Any suggestions?

---

