---
title: "hi im trying to partition my hard drive"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by blake7 on 2009-05-08
hi can you or show me a step buy step guid cheers

---

### Post by dstew on 2009-05-08
I assume you are using Gparted. Here is a [tutorial]("http://www.dedoimedo.com/computers/gparted.html").

---

### Post by donpedrodos on 2009-05-08
Well i just setup a drive to hold my /home an my swap and a test partition for new versions of ubuntu and backup.

A lot of playing around with deleting, creating and moving partitions on one drive.

Had to change some file manualy that at boot they would mount automaticly.
Than i lost the boot-splash too and i remembered this was happening one time before after moving the swapfile.
The next item brought me back on track what was going wrong:
[http://ubuntuforums.org/showpost.php?p=5377919&postcount=5](http://ubuntuforums.org/showpost.php?p=5377919&postcount=5)

I think there should be an application that takes care of all these thing, so as updating you menu.list & fstab and to fix you boot-splash ( /etc/initramfs-tools/conf.d/resume)

So if you never played with a partitionar before, Ubuntu can be a chalange to get everything up and running like 1-2-3.

The application to use is Gparted as mentioned above.
Note that editing a partition wil only work when a disk is unmounted.

After any change by moving or deleting and creating partitions, Ubuntu wil be unable to automount this partition.
This wil only work after you edit your fstab.

If all this above is abra cadabra, start to educate yourself and read as much as posible information about the subject.

Otherwise you could in the worst case endup with an unbootable system.

---

