---
title: "How to detect the external enclosure w/o reboot"
date: 2007-11-23
forum: Hardware &amp; Laptops
---

### Post by satimis on 2007-11-23
Hi folks,


Ubuntu 7.04 workstation
P-III PC - USB1.0 port
external enclosure mounted with ATA-66 12G HD - USB connector


The enclosure can be occasional detected by PC on plugin.  Most the time I have to reboot the PC with the enclousre turned on to get it detected.  Files/data can be transferred to/from the enclosure w/o problem.  Is there any way to get it detected without reboot?  TIA


satimis

---

### Post by taurus on 2007-11-23
Just power on and plug it in.  Then, see if it appears from the output of this command from a terminal.

```
sudo fdisk -l
```

---

### Post by satimis on 2007-11-23
> **taurus said:**
> Just power on and plug it in.  Then, see if it appears from the output of this command from a terminal.

```
sudo fdisk -l
```
If it can be detected automatically by PC on plugin the cable.

$ fdisk -l (without sudoer)
/dev/sdb1 ......
/dev/sdb2 ......

2 partitions on the HD.   Otherwise nothing displayed.  I have to reboot PC to get the enclosure detected at booting.

---

