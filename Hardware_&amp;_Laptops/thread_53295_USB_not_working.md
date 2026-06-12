---
title: "USB not working"
date: 2005-07-31
forum: Hardware &amp; Laptops
---

### Post by ricardo06 on 2005-07-31
Hello,

Can somebody help me figure out what is wrong ?
For quite a while I thought I had a problem with printing, as my usb printer did not work (it does work on an other machine not under ubuntu) but i did not care much. 
Now I tried to install an usb wifi lan adapter and both (i've got two of diffrent brand) would not work.
the devices are recognized by the USB controller :

[COLOR=Blue]richard@ubuntu:~$ lsusb
Bus 003 Device 004: ID 0b3b:1630 Tekram Technology Co., Ltd
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 04b8:0005 Seiko Epson Corp. Stylus Printer
Bus 001 Device 001: ID 0000:0000
richard@ubuntu:~$[/COLOR]

The device manager ( System>device manager ) detects them.

When I print everythings goes fine , no errors, but nothing happens. The cups demon is there :

[COLOR=Blue]richard@ubuntu:~$ ps -e | grep cups
 5494 ?        00:00:00 cupsd
 6682 ?        00:00:05 gnome-cups-icon
richard@ubuntu:~$[/COLOR]

On the other hand, when i insert the usb wifi adapater, it is hotplugged detected but the 'usbnet' daemon does not start. (even if i start it manually the connection between the daemon and the adpater does not seem to be realized).

It seems to me that the connection between devices drivers and the actual H/W peripheral is not done so long as the H/W is connected to an usb port. 

Can somebody help a bit  ?

Richard

My H/W
AMD64 3500+
512 MB
chipset ati XPRESS200P (many pb with this one)

---

