---
title: "Mount external usb hd under dapper server"
date: 2006-08-28
forum: Hardware &amp; Laptops
---

### Post by baryonyx on 2006-08-28
Hi

I'm trying to connect an external usb hard disk to a machine running the 6.06 server edition.  I've successfully connected the same drive to a standard ubuntu desktop install so the drive should work.     

When I connect the drive and power it on, nothing happens and dmesg | tail doesn't show anything. 

I can see usbcore loaded in a module listing but I'm not sure if that's sufficient for the device to be detected.  

I'm not sure if the server edition handles external usb devices differently but I'm pretty much stumped at this point.

Any suggestions would be appreciated.

---

### Post by Jussi Kukkonen on 2006-08-28
Not much help, but:
> I'm not sure if the server edition handles external usb devices differently but I'm pretty much stumped at this point.
In my experience they work exactly in the same way -- server doesn't automount with pmount of course, like Gnome seems to.
Not that it should matter, but I think I've always powered the disk on first, then connected USB -- and devices appear.

> I can see usbcore loaded in a module listing but I'm not sure if that's sufficient for the device to be detected. 
Should have usb-storage too, I guess...

---

### Post by baryonyx on 2006-08-28
That was my problem.  usb-storage isn't loading at boot.  A quick modprobe loaded it and my usb drive appeared.  

Thanks a lot for the quick response

---

