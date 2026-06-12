---
title: "Can't see my ext3 partitions during install?"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by neomaxi on 2009-01-20
Hello,  I am trying to install Ubuntu 64.bit 8.10 on my Hardrive from the live CD.  However, the only partitions that are availble to me during the install process are my NTFS partitions.  I have 6 other EXT3 partitions with Linux mint and PClinuxOS that I do not use anymore... and they don't show up during the install partiions screen  (where it asks me where I want to install Ubuntu.

Why can I not see these partitions as viable partitions to install Ubuntu on?  I don't not want to resize my exisin NTFS partiions since I have Vista and XP on them....

Thanks in advance!!!

---

### Post by caljohnsmith on 2009-01-20
Did you try choosing the "manual" partitioning option during the installation process? If that doesn't help, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -lu
```
And please post the output.

---

### Post by neomaxi on 2009-01-20
> **caljohnsmith said:**
> Did you try choosing the "manual" partitioning option during the installation process? If that doesn't help, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -lu
```
And please post the output.

Yes, I did the maual partintion option and it didn't show up.
Im not at home now so I can can't try what you request.  I will try once I get home and post the results..

---

