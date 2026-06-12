---
title: "Help with software RAID 5 installation"
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by rs232 on 2009-09-08
Hi all, I've just switched to ubuntu after years of Red Hat and Fedora.
I'm now installing my server with 3x500Gb HD SATA.
This is what I did:

```
sda1 4gb SWAP
sda2 250mb /boot ext3
sda3 496.1 GB RAID

sdb1 4gb SWAP
sdb2 250mb UNMOUNTED ext3
sdb3 496.1 GB RAID

sdc1 4gb SWAP
sdc2 250mb UNMOUNTED ext3
sdc3 496.1 GB RAID
```

I've created a RAID 5 with the 3 partitions sda3/sdb3/sdc3, and I'm running a LVM volume over it mounting "/"

Installed Xen and rebooted, everything works fine.

I now would like the system to bootup even in case sda (first device in the bios boot order) is failing. As /boot is not set in a raid I thought about copying the content of sda2 (/boot) into sdb2 and sdc2, modify the menu.lst of grub adding the options to boot from (hd1,1) & (hd2,1)

Looking at the above scenario I guess I would have to install grub on hd1 and hd2
```
grub-install hd1
grub-install hd2
```this would make send to me as if sda is failing sdb is next in the boot sequence.
My only question is:
What about the fstab? this is into /etc (on the RAID 5) and statically points /boot to /sda2).

Do you see my point?
I just would like my system to ba able to boot properly even if one of the 3 HD Im using is failing.

Thanks to read!
rs232

---

### Post by rs232 on 2009-09-08
I did some reading.
Apparently /boot can be sored on a software RAID 1
So I've changed what stated above and created a RAID 1 for /boot using sda1 and sdb1 (leaving sdc1 unused).
I've also changed the grub menu.lst
I now have the first 2 records identical but pointing to 2 different hard disks:

hd0,1 the first (sda1 default)

hd1,1 the second (sdb1)

Until here, no probs or what so ever.
I just need to install grub in the MBR of the second HD in case the first is failing.
I've tried:

grub-install sdb

but after the reboot I ger the grum prompt with no menu or what so ever.

Am I doing anything wrong?

thanks again for your help!
rs232

---

### Post by rs232 on 2009-09-09
FIY the solution is:
```

sudo grub
grub> root (hd1,1)
grub> setup (hd1)
grub> quit
```

---

