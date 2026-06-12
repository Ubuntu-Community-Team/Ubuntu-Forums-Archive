---
title: "Targus ACP50US docking station video driver help"
date: 2010-12-06
forum: Hardware
---

### Post by sirjeff2000 on 2010-12-06
I'm am very new to Ubuntu and I am trying to get a Targus ACP50us working on my toshiba laptop with Ubuntu 10.10. Everything seems to work but the External video. I've googled the ACP50US and Ubuntu and tried other combinations and found only one solution. Unfortunately it was from an August post in 2007. it goes a bit beyond my current abilities and I'm not sure it would even work with 10.10 - Could someone take a look at the info here and help me possibly apply the solution if it is possible? Please remember I am new to the OS so instructions will need to be very verbose.

Thanks
Jeff


---------------- The Post -----------------------
2007-08-30
Targus ACP50US 
I got this off woot and it arrived to today. And it works under linux, with a bit of work.

Update Kernel module

The dock uses the sis usb vga chipset, but sisusb.c does not include the USB vendor/product ID combination, so add that to linux-source-2.6.20/drivers/usb/misc/sisusbvga/sisusb.c
{ USB_DEVICE(0x0711, 0x0550) },
with the other lines that say USB_DEVICE (somewhere around 3435 in my version).

While a monitor is connected, insmod sisusbvga should activate the monitor.


New xorg.conf

In xorg.conf, the driver you want to use is 'sisusb'.

Section "Device"
Identifier "gfx"
Driver "sisusb"
VendorName "Videocard vendor"
BoardName "usb video"
EndSection

To test:

Xorg :1 -config /etc/X11/xorg.conf.usbvga -sharevts

---

