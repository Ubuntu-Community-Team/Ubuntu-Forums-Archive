---
title: "Hardy Touchpad Not Detected by kernel"
date: 2008-02-18
forum: Hardware &amp; Laptops
---

### Post by Elitist_Phoenix on 2008-02-18
Hi there, the hardy heron kernel (thus neither does xorg) doesn't seem to detect my laptops touchpad. Though weirdly enough the tpconfig utility does. Really kinda stumped and have tried everything. 

Take into consideration when suggesting anything that my kernel only has one boot parameter:
```
kernel		/boot/vmlinuz-2.6.24-8-generic root=UUID=2da6b423-961a-4d5e-a30e-e552604d761b ro acpi=ht
```
This is for another bug i've found where my laptop lid is always detected as closed. The touchpad doesn't even get detected with acpi on.

The "Logitech USB-PS/2 Optical Mouse" is the USB mouse i've got plugged in at the moment so i can use it and no it doesn't work if it unplugged completely from the start.

Thanks in advance


```
root@discostu:/home/discostu# uname -a
Linux discostu 2.6.24-8-generic #1 SMP Thu Feb 14 20:40:45 UTC 2008 i686 GNU/Linux
```

```
root@discostu:/home/discostu# tpconfig
Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).

```

```
root@discostu:/home/discostu# cat /proc/bus/input/devices
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=046d Product=c03d Version=0110
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:13.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:13.0/usb2/2-1/2-1:1.0/input/input2
U: Uniq=
H: Handlers=mouse1 event2 
B: EV=17
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=40001
B: SND=6
```



```
discostu@discostu:~$ dmesg | egrep -i 'input|touch|track'
[   23.523263] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   23.543112] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   26.933390] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:13.0/usb2/2-1/2-1:1.0/input/input2
[   26.959136] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:13.0-1
[   36.410198] input: PC Speaker as /devices/platform/pcspkr/input/input3
```

Also doesn't seem to be an uncommon problem
[http://ubuntuforums.org/showthread.php?t=528462](http://ubuntuforums.org/showthread.php?t=528462)
[http://ubuntuforums.org/showthread.php?t=667193](http://ubuntuforums.org/showthread.php?t=667193)

---

### Post by Elitist_Phoenix on 2008-03-01
Filed a bug report. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196808](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196808)

---

