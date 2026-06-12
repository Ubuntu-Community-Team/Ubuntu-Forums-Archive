---
title: "ideapad no touchpad"
date: 2021-09-04
forum: Hardware
---

### Post by johndough2 on 2021-09-04
Hi

I have tried Debian, Ubuntu and Mint resources to try and find an answer, and NADA.

So........

Working my way through the problems....

System Model * *82H9
System Type * *x64-based PC
System SKU * *LENOVO_MT_82H9_BU_idea_FM_IdeaPad 3 17ITL6

Piriform Speccy reports...

Standard PS/2 Keyboard
* * Device Kind * *Keyboard
* * Device Name * *Standard PS/2 Keyboard
* * Vendor * *MSFT
* * Location * *Intel LPC Controller/eSPI Controller (U Premium) - A082
* * * * Driver
* * * * * * Date * *6-21-2006
* * * * * * Version * *10.0.19041.1
* * * * * * File * *C:\Windows\system32\DRIVERS\i8042prt.sys
* * * * * * File * *C:\Windows\system32\DRIVERS\kbdclass.sys

HID-compliant mouse
* * Device Kind * *Mouse
* * Device Name * *HID-compliant mouse
* * Vendor * *MSFT
* * Location * *I2C HID Device
* * * * Driver
* * * * * * Date * *6-21-2006
* * * * * * Version * *10.0.19041.1
* * * * * * File * *C:\Windows\system32\DRIVERS\mouhid.sys
* * * * * * File * *C:\Windows\system32\DRIVERS\mouclass.sys


I did not have a mouse attached in W10 but have to use it linux.


So who is the Vendor?  MSFT   ????

Are there any drivers?


Laptop:~$ cat /proc/bus/input/devices

I: Bus=0011 Vendor=0001 Product=0001 Version=ab83
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

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Ideapad extra buttons"
P: Phys=ideapad/input0
S: Sysfs=/devices/pci0000:00/0000:00:1f.0/PNP0C09:00/VPC2004:00/input/input3
U: Uniq=
H: Handlers=rfkill kbd event3 
B: PROP=0
B: EV=13
B: KEY=81000800100c03 4400000000300000 0 2
B: MSC=10

I: Bus=0003 Vendor=0000 Product=0538 Version=0111
N: Name=" USB OPTICAL MOUSE"
P: Phys=usb-0000:00:14.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/0003:0000:0538.0002/input/input8
U: Uniq=
H: Handlers=mouse0 event5 
B: PROP=0
B: EV=17
B: KEY=70000 0 0 0 0
B: REL=903
B: MSC=10


Thanks in advance for any help.

---

### Post by bcschmerker on 2021-09-04
**I recognize the HID firmware Vendor tag from one of *my* Questions here:  What models Microsoft® Hardware&#8482; keyboard and pointer?**  *lenovo*® builds its products primarily for Windows, uses the Microsoft Corporation compiler for the FADT tables.  In X.org, libinput (/usr/lib/xorg/modules/input/libinput-drv.so) should be able to handle all three HID subsections (viz., the AT Translated Set 2 keyboard at /devices/platform/i8042/serio0/input/input2; the IdeaPad&#8482; Extra Buttons at /devices/pci0000:00/0000:00:1f.0/PNP0C09:00/VPC2004:00/input/input3; and the USB Optical Mouse at /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/0003:0000:0538.0002/input/input8).  Don't know why no detection of a presumed Synaptics touchpad at present; for an *e*machines®/ac*e*r® EL1210-09 that I've in prep for a projection-'puter mission, LinUX 5.x instantly detected the PS/2 Synaptics touchpad integrated into one IBM SK-8840 (FRU# 42C0014) on the i8042 Aux serial port, detected and daisy-chained the integrated Trackpoint as a PS/2 Generic Mouse through the touchpad.

**Addendum:**  Suggest installing the Synaptics Touchpad driver for X.org: ```
sudo apt install xserver-xorg-input-synaptics
``` and report back on touchpad detection.

---

### Post by johndough2 on 2021-09-05
Hi

Thanks.

Something I have already tried, but a little more input...

Laptop:~$ sudo xinput list-props 4
Device 'Virtual core XTEST pointer':
	Device Enabled (116):	1
	Coordinate Transformation Matrix (118):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	XTEST Device (235):	1


Laptop:~$ sudo xinput --list-props 8
Device 'Ideapad extra buttons':
	Device Enabled (116):	1
	Coordinate Transformation Matrix (118):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	libinput Send Events Modes Available (238):	1, 0
	libinput Send Events Mode Enabled (239):	0, 0
	libinput Send Events Mode Enabled Default (240):	0, 0
	Device Node (241):	"/dev/input/event3"
	Device Product ID (242):	0, 0


So something is actually acknowledged as present.

What next ?

---

### Post by johndough2 on 2021-09-05
Hi 
Additional info

The NumPad arrows etc move the "pointer" very slowly.

Now I am beginning to think the "Ideapad extra buttons" may be those and not anything to do with the touchpad itself.


Anything else I could try?

---

