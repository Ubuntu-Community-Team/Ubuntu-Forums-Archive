---
title: "Will GRUB detect Chicago"
date: 2006-02-13
forum: Hardware &amp; Laptops
---

### Post by trav1085 on 2006-02-13
I am getting a new computer soon from Dell and will get a external second harddrive for it, I will install Ubuntu and other oses on it, such as DOS, Windows 3.1, Windows 98, and even Windows Chicago (a windows 95 beta)

1) Will GRUB detect old oses such as DOS and old versions of Windows

2) Will it detect a beta OS that was not known

---

### Post by BenTyreman on 2006-02-13
GRUB doesn't detect the operating system (as far as I know). All you need to do is add a chainloader entry to menu.lst, and it will then use what ever boot record was on the device you specified. This way, you can have a GRUB boot menu with a "Second hard drive" option. Selecting this would then bring up the standard Windows boot menu.

On a side issue, are you sure you can get Windows running on an external hard drive? I would have thought that it doesn't load the mass storage drivers early enough to boot from the drive.

---

