---
title: "Disable driver"
date: 2009-10-21
forum: Hardware
---

### Post by ThomasDenmark on 2009-10-21
Hi

I have a laptop (Acer C300) with a disfunctioning wacom tablet screen: sometimes (depending on which power supply i am using, where in the room my laptop is, how charged the battery is, etc. !!!) it thinks that I am pointing in the lower right corner of the screen. 

In Windows this meant constantly opening the clock, but I solved the problem by going to the device manager, and simply clicking "disable" on the Wacom Serial Pen Tablet.

In Ubuntu 8.04 it was no problem since it did not install the driver for the device, but after upgrading to 8.10, it means opening the trash bin at least a few time per minute. 

Is there anything like Device Manager on Linux/Ubuntu? If not, how do I disable this device/driver the Linux way?

Thomas

---

### Post by Dark_Stang on 2009-10-21
You can remove the xserver-org-input-wacom package through Synaptic, which would disable all wacom devices on that machine. That would probably be the easiest way to do that.

---

### Post by ThomasDenmark on 2009-10-21
So I guess this is the command line equivalent:

sudo aptitude purge xserver-org-input-wacom

If I change my mind, can I undo this simply by installing the same package again?

---

### Post by Dark_Stang on 2009-10-21
Yup, that command will work. It will probably also remove a few parent packages (like xserver-org-input-all) but that will be fine.

---

### Post by ThomasDenmark on 2009-10-22
Note to others: A restart is needed after purging before the tablet is actually disabled. 

Thanks for the help :)

---

