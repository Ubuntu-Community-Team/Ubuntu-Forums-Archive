---
title: "I/O Errors with Addonics' 5 Port HPM-XU  Port Multipliers (ad5hpmreu)"
date: 2012-09-03
forum: Hardware
---

### Post by mongolito404 on 2012-09-03
I purchased an [Addonics' 5 Port HPM-XU Port Multipliers (ad5hpmreu)]("http://www.addonics.com/products/ad5hpmreu.php") standalone SATA controller. And cannot get it to wotk with Ununtu 12.04 running on my laptop using an USB 2 connection.

I currently running a 3.2.0 kernel (3.2.0-29-generic #46-Ubuntu SMP x86_64) which seems to be unable to detect the # HDD connected to the controller. The system log is filled with I/O errors (see attached log), the kernel seems to fail to read the partition table of the drives.

Addonics provides a "HPM RAID Management utility" for Linux. When using it, it is only able to detect one HDD at random of the 3 connected HDDs.

When using the HPM RAID Management utility an an old MacBook, the three connected drive are detected properly. So I assume the controller, disks and connection are fine.

Out of curiosity, I also tried to plug the controller to a Raspberry Pi running Debian Wheezy (kernel 3.1.9+ armv6l) and a WR703N router running OpenWRT snapshot (kernel 3.3.8 #1 mips). Both have the same behaviour, disk are not properly detected by the kernel and the log are filled with I/O errors.

The controller uses a JMicron JMB393 chipset. Has anyone experienced (and solved?) similar issues with a similar product?

---

### Post by mongolito404 on 2012-09-05
Addonics' technical support confirmed the issue and is investigating it. According to them, there i no issue when using their eSATA to USB adapter, so the HPM-XU is faulty.

---

