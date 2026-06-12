---
title: "Detailed Hard Drive Monitor"
date: 2013-04-11
forum: Hardware
---

### Post by NR8703 on 2013-04-11
Hi,

Is there any utility for Ubuntu 12.04 to monitor disk command LBA, Command Length (Transfer length), Read/Write bandwidth etc. Most of the tools I explored including iotop, iostat, etc did not contain LBA information, command length information. The utility needs to be passive and not run any benchmarks. The disk is primarily SCSI/SATA.

Appreciate any help on this :)

Thanks

---

### Post by NR8703 on 2013-04-17
So, I got this running by modifying the kernel driver for SCSI and recompiling the kernel. Right now the LBA, transfer length etc is printed via the printk command. 
Is there any way to filter this based on the user id?

Any help is appreciated.

Thanks

---

