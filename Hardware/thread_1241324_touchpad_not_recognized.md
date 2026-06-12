---
title: "touchpad not recognized"
date: 2009-08-15
forum: Hardware
---

### Post by Tectuktitlay on 2009-08-15
Hi,

I just installed Jackalope on my new laptop (an Asus K70IO-TY023C) and have trouble configuring the touchpad. Ubuntu doesn't seem to recognize it as a touchpad and thinks it's a mouse. In the Mouse Preferences there are no touchpad options and there is no entry for it in my xorg.conf.

How can I make Ubuntu realize it's a touchpad?

Here's my xorg.conf:

```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

Here's /proc/bus/input/devices:

```

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button (CM)"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=3
B: KEY=4000 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
U: Uniq=
H: Handlers=event3 
B: EV=21
B: SW=1

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input4
U: Uniq=
H: Handlers=mouse0 event4 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=120013
B: KEY=402000000 3803078f800d001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=046d Product=c512 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:04.0-4/input0
S: Sysfs=/devices/pci0000:00/0000:00:04.0/usb3/3-4/3-4:1.0/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=120013
B: KEY=1000000000007 ff800000000007ff febeffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=ff1f

I: Bus=0003 Vendor=046d Product=c512 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:04.0-4/input1
S: Sysfs=/devices/pci0000:00/0000:00:04.0/usb3/3-4/3-4:1.1/input/input7
U: Uniq=
H: Handlers=kbd mouse1 event7 
B: EV=20017
B: KEY=1fffffffff ffffffffffffffff ffffffffffffffff ffffffffffffffff 3300007 ff80d8fafd01d000 1f000000000000 0
B: REL=143
B: MSC=10
B: LED=ff00

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:29/device:2a/input/input8
U: Uniq=
H: Handlers=kbd event8 
B: EV=3
B: KEY=3f000b00000000 0 0 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input9
U: Uniq=
H: Handlers=kbd event9 
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=04f2 Product=b071 Version=1515
N: Name="CNF7129"
P: Phys=usb-0000:00:04.1-5
S: Sysfs=/devices/pci0000:00/0000:00:04.1/usb1/1-5/1-5:1.0/input/input10
U: Uniq=
H: Handlers=event10 
B: EV=3
B: KEY=1 0 0 0 0

I: Bus=0011 Vendor=0002 Product=0005 Version=0063
N: Name="ImPS/2 Logitech Wheel Mouse"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input11
U: Uniq=
H: Handlers=mouse2 event11 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=103

```

Any help is greatly appreciated!

Tec

---

### Post by Tectuktitlay on 2009-08-26
Is there no one who can help me?

Tec

---

