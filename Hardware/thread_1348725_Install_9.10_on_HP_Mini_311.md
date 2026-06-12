---
title: "Install 9.10 on HP Mini 311"
date: 2009-12-07
forum: Hardware
---

### Post by perigee on 2009-12-07
Hello all, 

I just got a Mini 311, and followed all instrument on 

[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/).

It booted successfully from my USB key, but after chosen "install ubuntu",
everything is frozen.  Anyone has any ideas ? Thank you in advance.


Perigee

---

### Post by perigee on 2009-12-07
I've tried use utility on ubuntu to create bootable USB key,  it works. But it blocked at first restart (after installation)... :-(

Perigee

---

### Post by perigee on 2009-12-07
The system is start once in every two restarts...
and wifi does not work. Try to figure out ...

---

### Post by perigee on 2009-12-07
maybe it has conflict with ION platform ? or just couldn't find right driver ?

---

### Post by perigee on 2009-12-07
b43-phy ERROR: ....

---

### Post by perigee on 2009-12-07
In recovery mode,  process blocked at : 
[2.420729] b43-pci-bridge 0000:03:00.0: PCI INT A -> Link[AX3A] ->
GSI 16 (level, low) -> IRQ 16

Any ideas ? 


Pg

---

### Post by lightalchemist on 2009-12-08
Same problem here on my HP Mini 311. 

I was able to launch Ubuntu Netbook Remix (UNR) using USB drive. It showed the new interface for UNR without any problem although I did not try running any applications before selecting installations.

I then installed UNR. Installation was successful. Upon reboot, with the USB drive removed, system appears to hang after selection of OS. All the screen shows is a blinking cursor.

However manage to boot into windows XP home without any problem although it seems that starting up is much slower than before.

Also able to boot into Ubuntu 9.10 desktop version (NOT remix) using USB thumbdrive without any problem.

Noticed that the light on HP mini 311 indicating wifi connection was orange instead of blue. Not sure whether this is related although the reason could likely be because the wifi do not work out of the box as indicated by some threads on the ubuntu forums.

Would be really grateful if anyone could provide a solution.

---

### Post by lightalchemist on 2009-12-08
Btw did u guys choose the netbook remix (UNR) or the version for desktop?

---

### Post by lightalchemist on 2009-12-08
For others: This thread may be of some help.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/479597](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/479597)

---

### Post by perigee on 2009-12-08
I'm using Desktop version, since I just don't like the interface of UNR. 
Seems the problem is related to Broadcom wifi -- the module b43, since 
my system stoped in recovery mode on the line of checking b43 ...

---

