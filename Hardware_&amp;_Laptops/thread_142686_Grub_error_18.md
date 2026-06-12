---
title: "Grub error 18"
date: 2006-03-10
forum: Hardware &amp; Laptops
---

### Post by Gregk on 2006-03-10
Hello, I am trying to install ubuntu on my 300mhz p2 w/ asus p2L97 motherboard. I have previously installed it with success using a 1.8Gb hard drive, but have recently aquired a 80Gb drive. The motherboard detects the drive fine, as master. The installer ran fine except when it rebooted it came up with grub error 18. What does this error mean? what did i do wrong?

---

### Post by amohanty on 2006-03-11
From the Grub manual at:
[http://www.gnu.org/software/grub/manual/grub.html#Stage2-errors](http://www.gnu.org/software/grub/manual/grub.html#Stage2-errors)

> 8 : Selected cylinder exceeds maximum supported by BIOS
    This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general). 

You either need to upgrade your BIOS to a more recent vintage or in case thats not possible change your mobo.

AM

---

### Post by lha on 2006-03-11
Usually older bioses can't boot from partitions that exceed a certain limit. (Most common is at ~8.5GB) If you find an upgrade to your bios that removes this limit, you can use it. Otherwise you need to create a small(er) root or /boot partition in the beginning of you drive. If you can't find a bios upgrade that helps, easiest thing to do is to reinstall and use manual partitioning to create a root smaller than 8.5GB (my root is ~5GB), a swap partition and use the rest for /home.

---

