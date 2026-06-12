---
title: "Ubuntu 8.04, Hp laptop, bluetooth and virtual pc"
date: 2008-07-29
forum: Hardware
---

### Post by UnSkiLd on 2008-07-29
I recently installed ubuntu 8.04 on my work laptop, inside virtual pc 2007. I had to do it this route since work wouldn't want me to take XP off and put this one. But I wanted to start gearing myself towards a Linux Dist.

So as far as I know I have all the correct files installed for my bluetooth to work. I had to degrade my version of bluez-utils because I guess there is a major bug in the latest version.

When I do a hcitool scan: this is what it returns

>  hcitool scan
Device is not available: No such device

when I do an hcitool inq:
>  hcitool inq
Inquiring ...
Inquiry failed.: No such device

when I do a lsmod | grep blueL

>  lsmod | grep blue
bluetooth              61156  0 

when I do a dmesg | grep Blue:

> dmesg | grep Blue
[ 1544.748766] Bluetooth: Core ver 2.11
[ 1544.785338] Bluetooth: HCI device and connection manager initialized
[ 1544.786184] Bluetooth: HCI socket layer initialized

from what I am reading it looks like it is initialized, but does that mean it is initialized with my bluetooth card?

If the bluetooth in ubuntu is not communicating with the built-in bluetooth on my laptop - could this be because it is running inside Virtual PC 2007?

Can someone provide a fix for this or a work around?

My goal is to be able to communicate with my phone via bluetooth only, not usb or serial. Alot of examples I see are for usb and serial.

Thanks for the time.

---

### Post by madrunner on 2008-07-29
i am having this same problem with my blue tooth dell mouse, maybe some blue tooth deviceds are not compatible with Ubuntu?

---

### Post by jimv on 2008-07-29
I'm fairly certain that bluetooth isn't going to work with VirtualPC 2007 because it's not using your hardware to run Ubuntu, it's using virtualized, generic hardware.  BUT if you have a USB bluetooth dongle, you may be able to get it to work with VirtualBox instead, which supports passing USB devices to the virtualized OS.

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

---

### Post by madrunner on 2008-07-29
im not runnning Ubuntu virtualy but i still have troble with my bluetooth devices ex mouse and keyboard, any help there?

---

