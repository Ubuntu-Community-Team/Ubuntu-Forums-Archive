---
title: "acpi only partly works (worked fully on the live cd)"
date: 2006-10-25
forum: Hardware &amp; Laptops
---

### Post by sedd on 2006-10-25
Hi,

I've got an HP nw9440 laptop, and the acpi system worked fine on the dapper live cd. Brightness controls, battery meter, everything.  But after installing and updating, a few things stopped working: brightness controls, battery meter, the ac plug/unplug events and the sleep button.  The power button and screen close/open events still work.

I've tried every kernel in the repository, with no luck. Obviously my hardware is compatible, because it works on the live cd. There's just a software problem somewhere, and I'm trying to find out where it is. 

This seriously limits the portability of this computer. Its like having a car with a broken gas gauge. You don't want to drive very far. Any help would be very much appreciated.

---

### Post by goodfella on 2006-10-25
I had a problem also when I upgraded to dapper.  My computer would go through the process of shutting down but at the end it would just sit there and not completely turn off.  I read a post on another thread that said to add "acpi=force" to my grub menu.lst.  Here is an example:

title           Ubuntu, kernel 2.6.15-27-k7
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.15-27-k7 root=/dev/hdb2 ro quiet splash **acpi=force**
initrd          /boot/initrd.img-2.6.15-27-k7
savedefault
boot

This solved that problem.

---

