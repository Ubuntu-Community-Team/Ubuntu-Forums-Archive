---
title: "Left touchpad button scrolls down when clicked"
date: 2009-08-10
forum: Hardware
---

### Post by mandarhobbit on 2009-08-10
Alright, I posted this a while ago, and no one answered, which might have been my fault, because I didn't include a lot of detail, so here we go...


```
amanda@Isidore:~$ cd /var/lib/acpi-support/; grep '.' *-*
bios-version:93.09
system-manufacturer:Gateway
system-product-name:MT6730
system-version:1MA80000040

```

Linux Isidore 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686 GNU/Linux

Ubuntu 2.6.28-13.45-generic

```
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
U: Uniq=
H: Handlers=event1 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button (CM)"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=4000 0 0 0 0

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input4
U: Uniq=
H: Handlers=mouse0 event4 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=04f2 Product=b012 Version=9323
N: Name="Gateway USB 2.0 Webcam"
P: Phys=usb-0000:00:1a.7-3
S: Sysfs=/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0/input/input7
U: Uniq=
H: Handlers=event7 
B: EV=3
B: KEY=1 0 0 0 0 0 0 0 0

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/input/input8
U: Uniq=
H: Handlers=kbd event8 
B: EV=3
B: KEY=3f000b 0 0 0 0 0 0 0

I: Bus=0011 Vendor=0002 Product=0007 Version=12b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input10
U: Uniq=
H: Handlers=mouse1 event9 
B: EV=b
B: KEY=6420 0 7000f 0 0 0 0 0 0 0 0
B: ABS=11000003
```

```

amanda@Isidore:~$ xinput list
"Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=2	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"AT Translated Set 2 keyboard"	id=3	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=4	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"SynPS/2 Synaptics TouchPad"	id=5	[XExtensionPointer]
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 1472
		Max_value is 5472
		Resolution is 1
	Axis 1 :
		Min_value is 1408
		Max_value is 4448
		Resolution is 1

```

Now, what it's doing, is when I left click on something, instead of using the tap, it will scroll down. Makes it an annoyance at best of times and downright impossible to do graphical editing, which is what I normally do. I think the problem is in the mapping, but I'm at a loss on how to fix it.

---

