---
title: "GRUB boot woes with Compaq SMART 2 RAID controller"
date: 2006-01-25
forum: Hardware &amp; Laptops
---

### Post by nihilocrat on 2006-01-25
I can't get Breezy to boot correctly with my current setup. I was able to install everything fine, and if I start the installer and immediately execute a shell, I can even mount the drive I installed everything to (/dev/ida/c0d0p1). When partitioning the disks, it showed up correctly as /dev/ida/c0d0p1. However, when booting the system without the CD, the kernel says it can't find /dev/ida/c0d0p1 and drops to a BusyBox shell, from which I can't see any meaningful devices beyond the CD-ROM. I even try starting the CD with "rescue root=/dev/ida/c0d0p1" and it still can't find it, and the kernel proceeds to panic.

After looking closely at demsg, it reports when booting from the CD that it detects the Compaq SMART 2 controller fine, and thus /dev/ida/c0d0p1. When booting from the rescue option or without the disk, it doesn't seem to detect it before panicking. There is probably some step in the process, some kernel module loaded, or something to that effect which happens AFTER mounting the root filesystem, which allows the kernel to see the RAID array. Would compiling a custom kernel with Compaq SMART 2 support compiled in (as opposed to a module) help, or is there some easier way?

---

