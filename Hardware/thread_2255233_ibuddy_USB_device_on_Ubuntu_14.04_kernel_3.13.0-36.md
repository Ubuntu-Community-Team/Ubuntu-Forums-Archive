---
title: "ibuddy USB device on Ubuntu 14.04 kernel 3.13.0-36"
date: 2014-12-03
forum: Hardware
---

### Post by sapg on 2014-12-03
I'm sure I got this working on another Ubuntu 14.04 machine but I'm having a problem on one particular machine.  I'm wondering if anyone else has seen this.  I'm pretty sure the only difference is that the machie it worked on was a laptop and this machine is a desktop.

I'm trying to use a TENX iBuddy USB toy, it is basically some LEDs and a motor in the shape of an MSN angel/fairy thing.

I've successfully compiled and loaded the driver from this github project - [https://github.com/tietomaakari/ibuddy-lkm](https://github.com/tietomaakari/ibuddy-lkm)


When I try to use the driver - 

~$ echo 1 > /proc/driver/ibuddy/0/heart
  bash: /proc/driver/ibuddy/0/heart: No such file or directory

~$ lsmod |grep ibuddy
  ibuddy                 13913  0 

$ cat /etc/modprobe.d/usbhid.conf 
  options usbhid quirks=0x1130:0x0001:0x0004

I've even tried this -

~$ grep quirk /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="usbhid.quirks=0x1130:0x0001:0x0004"

But for some reason usbhid still claims the device -

kernel: [   45.100590] input: i-Buddy as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.1/input/input16
Dec  3 10:34:14  kernel: [   45.100685] hid-generic 0003:1130:0002.0005: input,hidraw1: USB HID v1.10 Device [i-Buddy] on usb-0000:00:1d.0-1.6/input1

The device ID seems to be the same as in the README -

~$ lsusb
Bus 002 Device 005: ID 0bda:0184 Realtek Semiconductor Corp. RTS5182 Card Reader
Bus 002 Device 004: ID 1130:0002 Tenx Technology, Inc. iBuddy

Anyone got any ideas?

---

