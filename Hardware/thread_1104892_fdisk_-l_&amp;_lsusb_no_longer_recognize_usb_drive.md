---
title: "fdisk -l &amp; lsusb no longer recognize usb drive"
date: 2009-03-24
forum: Hardware
---

### Post by sagramor on 2009-03-24
seemingly out of the blue ubuntu no longer recognizes my lacie external usb drive. 
fdisk -l returns nothing other than the normal hdd sda partitions. lsusb only returns this:
```
Bus 002 Device 003: ID 0408:030c Quanta Computer, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 069: ID 046d:c048 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
i have no idea where to go from here/
 normally i have to force mount it because i have a bad habit of not unmounting it when i'm done. 
hope i haven't screwed something up.

any ideas anyone?

---

### Post by sagramor on 2009-03-24
:sigh: *bump*

---

### Post by mrsteveman1 on 2009-03-24
If it doesn't even register in the kernel log (dmesg) or with lsusb, not much can be done from the OS side.

Did you recently change something? Upgrade or change the kernel? Does it work on another machine?

---

### Post by sagramor on 2009-03-24
....great

after about my 4th reboot it recognizes it. 
this is precisely why i hate posting on ubuntu forums.
the majority of the time the problem seems to mysteriously fix itself.
probably human error once again. is it possible to assign the umount command
to an icon on the desktop so that hopefully this doesn't happen again?

thanks for your quick reply mrsteveman1.

---

### Post by mrsteveman1 on 2009-03-25
If it is an external drive it should just show on the desktop where you can right click and eject it.

---

### Post by sagramor on 2009-04-13
right, it started doing this after i umount-ed the drive. thanks.

---

