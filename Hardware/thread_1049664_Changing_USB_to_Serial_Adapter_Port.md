---
title: "Changing USB to Serial Adapter Port"
date: 2009-01-24
forum: Hardware
---

### Post by dbsoundman on 2009-01-24
I have a basic USB to serial adapter which I need to use with minicom. When I plugged it in I did a dmesg | grep usb to see where it was connected, and it came up as /dev/usblp0. So I configured minicom to look to this as the serial port. However, minicom never gets past the "initializing modem" screen with this setup. I've seen other sites mentioning the USB mounting to ttyUSB or something like that. I was wondering if there was some way I could force this device to mount to that. I have had this problem with Ubuntu and openSUSE actually. I just need to make minicom work somehow through this adapter. Thanks!

-Dan

---

### Post by ieee488 on 2009-01-24
USB-serial adapters are problematic even in Windows.

It might be easier to buy a PCI card with serial ports.

---

### Post by dbsoundman on 2009-01-24
Unfortunately, I don't have any PCI ports left on my desktop, and of course can't use them on my laptop...maybe a PCMCIA card or something?

-Dan

---

### Post by ieee488 on 2009-01-25
[http://www.cooldrives.com/usb-serial-adapters-rs-232-single-multi-port.html](http://www.cooldrives.com/usb-serial-adapters-rs-232-single-multi-port.html)
claims that they have drivers for Linux for their USB-RS232 adapters

I see people selling PCMCIA-RS232 cards on eBay.

Good luck.

---

### Post by user11 on 2009-02-11
is there any other work-around for this? I can't do this with my lap-top.

---

### Post by geraldm on 2009-02-11
I have seen a work-around in the Hardware and Laptop forum.  The USB device 
must display its serial number, and FTDI cords do that.  The workaround needs to assign it to a serial type such as ttyUSBx, where x is a number.  This is done in the
UDEV code at boot-up or plug-in time.   I do not have the thread ID, but searching for the FTDI or UDEV code for FTDI devices might find it.  The serial number
would be shown in the file /proc/bus/usb/devices file, and possibly also within the /sys subdirectories.

Gerald

---

