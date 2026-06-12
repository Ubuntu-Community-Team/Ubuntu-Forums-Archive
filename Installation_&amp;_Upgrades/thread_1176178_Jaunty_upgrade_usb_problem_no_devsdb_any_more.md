---
title: "Jaunty upgrade usb problem: no /dev/sdb any more"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by smcleish on 2009-06-02
Hi,

Another problem I've had with my upgrade to jaunty is that my machine no longer mounts some usb devices (the mouse and keyboard work fine through usb). I use an external hard drive and SANSA mp3 player, and both don't work now and were fine before. They're listed by lsusb, but they don't automount any more and I can't work how to get them to mount by hand either, because /dev/sdb seems to have disappeared, and using mount or pmount with the devices that look like the right usb devices (called things like /dev/usbdev4.1) produce an error because they're not a block device. So can anyone suggest how I can get /dev/sdb back, or if there's something different in jaunty which I can use instead?

Cheers,
Simon

---

### Post by smcleish on 2009-06-04
OK this hasn't exactly been solved, it just went away after a couple of reboots of the machine. So that's good, if mystifying.

---

### Post by Aemaeth on 2009-11-05
Having some of the same issues here.

running 9.10 Alternate with LUKS Encryption on a ASUS EEEpc 1000HE previous versions of the os ran my Sansa 4GB clip without error but now the icon will briefly appear and then dissappear again. Anyone have a solution to this or is there a patch in progress?

---

