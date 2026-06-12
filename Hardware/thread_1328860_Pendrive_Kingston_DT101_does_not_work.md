---
title: "Pendrive Kingston DT101 does not work"
date: 2009-11-16
forum: Hardware
---

### Post by Danys on 2009-11-16
Hi,

    I 've bought this pendrive 4 days ago and I only used it 3 times until it doesn't work.
    I connect it and then use the lsusb command:

```

dany@urano:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 007: ID 0c76:0005 JMTek, LLC. Transcend Flash disk**
Bus 001 Device 002: ID 064e:a102 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
dany@urano:~$ 

```But fdisk -l command doesn't show it:

```

root@urano:/home/dany# fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1956    15711538+   7  HPFS/NTFS
/dev/sda2            1957       30401   228484462+   5  Extended
/dev/sda5            1957       29653   222476121   83  Linux
/dev/sda6           29654       30401     6008278+  82  Linux swap / Solaris
root@urano:/home/dany# 

```Any idea ??

I 'm using an Acer 751 with Ubuntu 9.10 ( I tested it with a desktop and 8.10 too )

Thanks in advance!

---

