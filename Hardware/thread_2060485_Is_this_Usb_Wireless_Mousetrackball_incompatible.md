---
title: "Is this Usb Wireless Mouse/trackball incompatible?"
date: 2012-09-20
forum: Hardware
---

### Post by drumour on 2012-09-20
Trying out new mouse/trackball. Does not appear to work in Ubuntu 12.04, but does work on Windows 7 without drivers (none supplied)

**lsusb gives:**
...
Bus 003 Device 004: ID 7545:1094

**ls /dev/input/mouse* gives two results. **

/dev/input/mouse0  /dev/input/mouse1

mouse0 is working wired Microsoft Intellimouse. 


**cat /proc/bus/input/devices gives 3 entries for the device:**

I: Bus=0003 Vendor=7545 Product=1094 Version=0110
N: Name="HID 7545:1094"
P: Phys=usb-0000:07:00.0-2.3/input0
S: Sysfs=/devices/pci0000:00/0000:00:1c.7/0000:07:00.0/usb3/3-2/3-2.3/3-2.3:1.0/input/input19
U: Uniq=
H: Handlers=mouse1 event16 
B: PROP=0
B: EV=17
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=143
B: MSC=10

I: Bus=0003 Vendor=7545 Product=1094 Version=0100
N: Name="HID 7545:1094"
P: Phys=usb-0000:07:00.0-2.3/input1
S: Sysfs=/devices/pci0000:00/0000:00:1c.7/0000:07:00.0/usb3/3-2/3-2.3/3-2.3:1.1/input/input20
U: Uniq=
H: Handlers=sysrq kbd event17 
B: PROP=0
B: EV=120013
B: KEY=10000 7 ff800000 7ff febeffdf f3cfffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=7545 Product=1094 Version=0100
N: Name="HID 7545:1094"
P: Phys=usb-0000:07:00.0-2.3/input2
S: Sysfs=/devices/pci0000:00/0000:00:1c.7/0000:07:00.0/usb3/3-2/3-2.3/3-2.3:1.2/input/input21
U: Uniq=
H: Handlers=kbd event18 
B: PROP=0
B: EV=1f
B: KEY=4837fff 72ff32d bf544446 0 0 1 20c10 b17c000 267bfa d941dfed 9e1680 4400 0 10000002
B: REL=40
B: ABS=1 0
B: MSC=10

Should I add this to incompatible hardware list?

---

### Post by jerrrys on 2012-09-20
Got some hits here that may help out

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Microsoft+Intellimouse&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Microsoft+Intellimouse&as_qdr=all&sa=Google+Search&lang=en)

---

