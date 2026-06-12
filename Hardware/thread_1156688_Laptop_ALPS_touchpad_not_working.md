---
title: "Laptop ALPS touchpad not working"
date: 2009-05-12
forum: Hardware
---

### Post by dadrivr on 2009-05-12
I am running Xubuntu 9. 04 and my ALPS touchpad on my Dell laptop is not working.   Do I need to install drivers or configure settings?  Please keep in mind that I am new to Xubuntu and Linux when responding.   Thank you so much for your help!

---

### Post by dadrivr on 2009-05-16
bump

---

### Post by dadrivr on 2009-05-27
Any ideas?  Please help!

---

### Post by yotam on 2009-10-17
You may consider trying my Alps driver in
   [http://www.medini.org/software/alps/alps.html]("www.medini.org/software/alps/alps.html")
-- yotam

---

### Post by rb0171610 on 2009-10-17
> **dadrivr said:**
> Any ideas?  Please help!
Type the following into a terminal and post your output:
```
cat /proc/bus/input/devices
```
This is to see if Linux is detecting the device or not.
(Installing a driver will not be your solution if the hardware is not detected)

---

### Post by rb0171610 on 2009-10-17
As well as:
```
dmesg | grep input
```

---

### Post by dadrivr on 2009-10-30
I updated to the newest version of Ubuntu (9.10).  The problem still persists.  Here is the output that you requested:

cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=3
B: KEY=4000 0 0 0 0

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input3
U: Uniq=
H: Handlers=mouse0 event3 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input4
U: Uniq=
H: Handlers=kbd event4 dell-laptop 
B: EV=120013
B: KEY=500f 2902002 8380307c f910f001 feffffdf ffefffff ffffffff ffffffff
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:21/device:22/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=3
B: KEY=3f000b 0 0 0 0 0 0 0

I: Bus=0003 Vendor=046d Product=c016 Version=0110
N: Name="Logitech Optical USB Mouse"
P: Phys=usb-0000:00:1d.3-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input7
U: Uniq=
H: Handlers=mouse1 event6 
B: EV=17
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10

dmesg | grep input
[    0.432114] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.432642] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.432689] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.821592] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.006918] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.586246] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:21/device:22/input/input5
[    2.336359] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input6
[    2.336444] generic-usb 0003:046D:C016.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.3-1/input0
[  185.492630] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input7
[  185.492728] generic-usb 0003:046D:C016.0002: input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.3-2/input0
[ 3313.270746] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input8
[ 3313.270846] generic-usb 0003:046D:C016.0003: input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.3-2/input0

---

