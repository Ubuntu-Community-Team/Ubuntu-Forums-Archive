---
title: "System doesn't boot correctly anymore"
date: 2009-03-09
forum: Hardware
---

### Post by sara g on 2009-03-09
Hello -

I've been happily using Ubuntu on my Toshiba Satellite for a few months now, and today it suddenly won't boot up.

I get this screen:

```
Boot from (hd0,0) ext3   c8f588c1-a0d6-449a-886d-710f5359aa14
Starting up ...pe
Loading, please wait...
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/34754255-2494-4292-8288-bee26654dca6) = dev(8,5)
kinit: trying to resume from /dev/disk/by-uuid/34754255-2494-4292-8288-bee26654dca6
kinit: No resume image, doing normal boot...
mount: mounting /dev/disk/by-uuid/c8f588c1-a0d6-449a-886d-710f5359aa14 on /root failed: Invalid argument
mount: mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.


BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu7) built in-shell (ash)
Enter help for a list of built-in commands

(initramfs)
```

If I try typing "reboot", then the system appears to boot normally but then hangs with a black screen.

If instead I try typing "exit", then I get a "kernel panic" and the caps lock light starts to flash.

What should I do?

Sara

---

### Post by bazzer on 2009-03-13
Hi - is it a dual boot system? If so, maybe a bootloader from the other OS has broken grub for whatever reason and it needs to be reinstalled.

If it's not dual boot, maybe one of two things has happened. 1- grub is broke and needs reinstalling or 2- you actually have nothing on the disk (it says 'No such file or directory' for some pretty critical folders). If it's the second, you'll have to reinstall the entire system.

---

### Post by sara g on 2009-03-13
It is not a dual-boot system, and I think there is something on the disk, because otherwise it would not have got as far as it did. What is grub and how do i reinstall it?

---

