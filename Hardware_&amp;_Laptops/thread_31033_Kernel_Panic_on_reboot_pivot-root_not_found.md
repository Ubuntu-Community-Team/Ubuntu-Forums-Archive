---
title: "Kernel Panic on reboot: pivot-root not found"
date: 2005-05-01
forum: Hardware &amp; Laptops
---

### Post by dmallery on 2005-05-01
on a known good Supermicro 370DE6 mobo (smp) when the system reboots in the middle of an install: 

Starting Ubuntu...
pivot_root: No such file or directory
/sbin/init: 428: cannot open dev/console: No such file
Kernel panic - not syncing: Attempted to kill init!

sigh!

any clues will be followed.

this box was running current updated knoppix.

thanks in adavnce

dave mallery

---

### Post by nad on 2005-05-01
It can't find your kernel when switching from the boot image probably because of a raid device. What's your drive setup? With a knoppix disk, whats the auto-configured /boot/grub/menu.lst? You may need to just point grub in the right direction.

---

### Post by lee_connell on 2005-05-20
i have same issue.  i have a raid0 on two drives.

md0 is my root and i use /boot and /swap as non raid devices.

---

### Post by brianglass on 2005-10-16
I have a similar problem, though I am not using RAID.

See my [previous post]("http://www.ubuntuforums.org/showthread.php?t=76852&highlight=smp+panic").

My /boot/grub/menu.lst file shows the following for the working configuration:

```
title           Ubuntu, kernel 2.6.12-9-amd64-generic Previous
root            (hd0,0)
kernel          /boot/vmlinuz.old root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img.old
savedefault
boot
```

And the following for the non-working SMP installation. Both initrd and vmlinux exist in the specified location.

```
title           Ubuntu, kernel 2.6.12-9-amd64-k8-smp
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-amd64-k8-smp root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-amd64-k8-smp
savedefault
boot
```

As far as I can tell I have turned RAID off in the BIOS. Any ideas?

---

