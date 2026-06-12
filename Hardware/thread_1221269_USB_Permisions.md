---
title: "USB Permisions"
date: 2009-07-23
forum: Hardware
---

### Post by sparker256 on 2009-07-23
Trying to get my Saitek Switch Panel to be recognized in Ubuntu 9.04
I have done the following in trying to get it to work.


bill@bill-desktop:~$ cat /proc/bus/input/devices | grep -A 7 -B 1 "Switch Panel"I: Bus=0003 Vendor=06a3 Product=0d67 Version=0100
N: Name="HOLTEK Saitek Pro Flight Switch Panel"
P: Phys=usb-0000:00:0a.1-7.3/input0
S: Sysfs=/devices/pci0000:00/0000:00:0a.1/usb1/1-7/1-7.3/1-7.3:1.0/input/input7
U: Uniq=
H: Handlers=event7 
B: EV=13
B: KEY=fffff 0 0 0 0 0 0 0 0
B: MSC=10

Created a udev rule named "/lib/udev/rules.d/10-saitekswitchpanel.rules" with the following content:

SUBSYSTEMS=="input", \
ATTRS{name}=="HOLTEK Saitek Pro Flight Switch Panel", \
NAME="input/%k", MODE="0666", SYMLINK="input/saitekswitchpanel"

Re-pluged the panel

bill@bill-desktop:~$ ls -al /dev/input/saitekswitchpanel
lrwxrwxrwx 1 root root 6 2009-07-23 15:14 /dev/input/saitekswitchpanel -> event7

Checked to see if the panel actually works

bill@bill-desktop:~$ cat /dev/input/saitekswitchpanel | hexdump
cat: /dev/input/saitekswitchpanel: Permission denied

Not sure why I am getting Permision denied

With a MODE="0666" did not think I should have to use sudo

Not sure where to go from here.

Thanks Bill

---

