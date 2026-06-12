---
title: "udev rule for mx1000 of mx3200 combo"
date: 2007-03-17
forum: Hardware &amp; Laptops
---

### Post by Tiftof on 2007-03-17
Hi,

I used to have a udev rule so that my mx1000 would be accessible through /dev/input/mx1000 (or /dev/input/event9, don't know anymore) so I could configure my xorg.conf easily. But I lost the rule after a clean install and I am not able to reconstruct it :p

Here's the output of "cat /proc/bus/input/devices" for my mx3200 combo:

I: Bus=0003 Vendor=046d Product=c512 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.0-1/input0
S: Sysfs=/class/input/input3
H: Handlers=kbd event3 
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=ff1f

I: Bus=0003 Vendor=046d Product=c512 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.0-1/input1
S: Sysfs=/class/input/input4
H: Handlers=kbd mouse2 ts2 event4 
B: EV=20007
B: KEY=ffffffff 0 0 1878 d800d100 1e0000 0 0 0
B: REL=143
B: LED=ff00

none of the udev rules found elsewhere for mx1000 work for me, because my keyboard and mouse have the same name...

any help?

Thanks

---

### Post by Tiftof on 2007-03-18
nevermind, found it myself: 

KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Receiver",SYSFS{../device/bInterfaceNumber}=="01", NAME="input/event9"

---

