---
title: "Bluetooth modules/firmware"
date: 2009-05-18
forum: Hardware
---

### Post by tadeas on 2009-05-18
Is there any way to find out which module or firmware is used to get my Bluetooth adapter working? I've searched dmesg as well as lsmod, but I can't figure it out.
The adapter is:
```
root@belgarath-laptop:~# lsusb | grep Bluetooth
Bus 005 Device 002: ID 0930:0508 Toshiba Corp. Integrated Bluetooth HCI
```
Here's my dmesg and lsmod:
[http://tadeas-moravec.yc.cz/dmesg.txt](http://tadeas-moravec.yc.cz/dmesg.txt)
[http://tadeas-moravec.yc.cz/lsmod.txt](http://tadeas-moravec.yc.cz/lsmod.txt)

Moreover how do I find which packages are (were) necessary to get it working?

I have a plain Kubuntu 9.04 installation with all upgrades but all I've installed manually above the base installation was vim, mc and the radeonhd driver...

---

