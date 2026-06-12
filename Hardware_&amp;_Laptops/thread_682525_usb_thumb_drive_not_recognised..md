---
title: "usb thumb drive not recognised."
date: 2008-01-30
forum: Hardware &amp; Laptops
---

### Post by griz on 2008-01-30
Hi all,

When I plug my usb thumb drives into my P3 running 7.10, they are not recognised.  The last 2 lines of dmesg are:

[ 1584.823075] usb 2-1: new full speed USB device using uhci_hcd and address 4
[ 1585.346318] usb 2-1: device not accepting address 4, error -71


I really need to get these thumb drives working on this computer as my laptop decided to die the other day and I really don't want to load a Windows OS on this box lol.

Griz.

---

### Post by cdtech on 2008-01-30
sudo /etc/init.d/hal restart

You should get " * Restarting Hardware abstraction layer hald"

If that doesn't work..

Be sure you are in the group:
usermod -a -G plugdev <username>

Or check if modules are loaded
lsmod | grep usb

if the modules are not there:

sudo apt-get install modconf
sudo modconf
go to kernel/drivers/usb/storage and add support

Hope this helps.......

---

### Post by griz on 2008-01-30
Thanks for that Cdtek, but still no joy.  the modules are loaded, but the thumb drive still not recognised.  Both are Sandisks, one a Mini and the other a U3 type.  This is the printout from lsmod | grep usb:

usbmon                 21560  0 
usb_storage            73024  0 
libusual               18448  1 usb_storage
ide_core              116804  1 usb_storage
usbhid                 29536  0 
hid                    28928  1 usbhid
scsi_mod              147084  5 usb_storage,sg,sd_mod,sr_mod,libata
usbcore               138632  7 ehci_hcd,usbmon,usb_storage,libusual,usbhid,uhci_hcd

Is there anything there that doesn't look right?

Griz.

---

### Post by cdtech on 2008-01-30
In some cases, disconnecting the card on some other computer improperly (from what I've heard) can cause this effect. I would recommend you try to connect the device to some other USB enabled system to unmount it properly, or try using the live CD for the task to see if that corrects it.

Sorry I can't be of any more help...

---

