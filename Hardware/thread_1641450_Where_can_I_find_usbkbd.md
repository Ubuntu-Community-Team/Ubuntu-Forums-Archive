---
title: "Where can I find usbkbd?"
date: 2010-12-09
forum: Hardware
---

### Post by fentonpcrackshell on 2010-12-09
Very, very new to linux, so sorry in advance.  I am trying to get my USB Barcode Scanner (Wasp WWS-800) to work with ubuntu 10.10.  I've tried the solutions mentioned here:

[http://wiki.ubuntu.org.cn/index.php?title=UbuntuHelp:BarcodeReaders&variant=zh-hant#New_Fix](http://wiki.ubuntu.org.cn/index.php?title=UbuntuHelp:BarcodeReaders&variant=zh-hant#New_Fix)

But it's not working.  When I plug in the device, and do
```
dmesg | tail
```I still get
```
[  131.289783] generic-usb: probe of 0003:04B4:CFA1.0005 failed with error -22
```When I do [FONT=Bitstream Vera Sans Mono]cat /boot/grub/grub.cfg[/FONT]

The following IS listed, so I think I got that part right: 

```
### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
# Force the messy USB CCD barcode reader to use the more lenient usbkbd driver
KERNEL=="event[0-9]*", SYSFS{idVendor}=="04b4", SYSFS{idProduct}=="cfa1", ACTION=="add", RUN+="/lib/udev/check_driver usbkbd $devpath $env{ID_BUS}"
### END /etc/grub.d/40_custom ###
```I also did the local rules thing:
```
~$ cat /etc/udev/rules.d/10-local.rules
KERNEL=="event[0-9]*", SYSFS{idVendor}=="04b4", SYSFS{idProduct}=="cfa1", ACTION=="add", RUN+="/lib/udev/check_driver usbkbd $devpath $env{ID_BUS}"
```When I do

I think my problem is with usbkbd.  I am still getting:
```
~$ sudo modprobe usbkbd
FATAL: Module usbkbd not found.
```I tried commenting it out in the blacklist file, but that doesn't seem to do any good.  Any ideas?

Thanks

---

### Post by Fafler on 2010-12-09
It seems Ubuntu 10.10 doesn't have usbkbd anymore. I think your choices are either a downgrade to a older Ubuntu version or a build custom kernel without usbhid. [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by fentonpcrackshell on 2010-12-09
Thanks.

I am not stuck on 10.10.  Do you know how far I have to go back?

---

### Post by Fafler on 2010-12-09
I have no idea. Try the live CD's and just go back through the versions till you find it.

---

