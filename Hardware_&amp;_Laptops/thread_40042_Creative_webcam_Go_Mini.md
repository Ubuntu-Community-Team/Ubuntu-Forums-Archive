---
title: "Creative webcam Go Mini"
date: 2005-06-07
forum: Hardware &amp; Laptops
---

### Post by WishMaster on 2005-06-07
Hi
I recently (few days ago) installed Ubuntu 5.04 as a dual boot on my [Acer TravelMate 661 LCi](http://users.pandora.be/Nyx/ubuntu.html).

I also have a Creative webcam Go Mini, which *should* work under Linux as I read.
I have been following this "tutorial" on how to get the thing to work: [http://www.linux.com/howtos/Webcam-HOWTO/hardware.shtml](http://www.linux.com/howtos/Webcam-HOWTO/hardware.shtml)

_2.1. Drivers and Modules_
Driver isn't in the kernel (did "dmesg" in console and didn't see the cam)
The driver does exist as a module in /lib/modules/2.6.10-5-386/kernel/drivers/usb/media/stv680.ko

Doing "lsmod" showed that the module wasn't loaded.
"modprobe stv680" and afterwards "lsmod", showed that the module was loaded.

_2.2. Supporting the Connection Type_
"For at least one webcam category, the STV0680-based models, working libusb support is recommended.
Libusb is a library that allows access to the USB functions in Linux through userspace and without the need to enable kernel support and insert modules.
Don't try to use libusb while your particular kernel webcam support is enabled either statically or the module loaded; you can only use one at at time."
So I did --> "rmmod stv680" to unload the module and to use "libusb".

"cat /proc/filesystems" gives only "nodev usbfs"
"You may need to mount usbdevfs to enable it and see the device files, which you can do at the command line with mount -t usbdevfs none /proc/bus/usb. "

> root@LinuxBert:/home/bert # mount -t usbdevfs none /proc/bus/usb
mount: unknown filesystem type 'usbdevfs'

wtf....?

When I started GnomeMeeting, it said "no devices detected"
The cvs-build of aMSn 'supports' cam for msn, but didn't work either.

Is there anyone who can help me out?

---

### Post by it.henrik on 2006-08-09
Sorry .. wrong thread :P

---

