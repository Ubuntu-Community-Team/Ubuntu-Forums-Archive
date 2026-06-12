---
title: "USB-stick not mounted automatically"
date: 2007-03-07
forum: Hardware &amp; Laptops
---

### Post by rpw on 2007-03-07
Hello,

I've got Ubuntu 6.10 on my desktop computer and one little problem with a USB-stick (Sandisk Cruzer 256MB, about 2 or 3 years old).

When I plug it into the computer, no matter which availabe USB-place, it is not mounted automaticly. 

sudo lsusb gives me the following output:

Bus 002 Device 003: ID 0781:5150 SanDisk Corp. SDCZ2 Cruzer Mini Flash Drive (thin)

Found a workaround in this thread [http://www.ubuntuforums.org/showthread.php?t=361540&highlight=usb+stick](http://www.ubuntuforums.org/showthread.php?t=361540&highlight=usb+stick), that worked for me -> sudo modprobe -r ehci_hcd

So it's possible to get the device mounted (half aotumounted ;-)), but is there a way to get this problem fixed completly? It's a kind of annoing to allways do the modprobe before plugging in the USB-stick, normaly I forget to do, then I have to unplugg, do the modprobe and plugg it in again...

Regards,

rpw

---

### Post by dotman on 2007-03-07
Well in the thread that you linked to he had a fix. Blacklist ehci_hcd. Since it may or may not effect other devices, you may want to ask easy_target how its has been going for him.

---

