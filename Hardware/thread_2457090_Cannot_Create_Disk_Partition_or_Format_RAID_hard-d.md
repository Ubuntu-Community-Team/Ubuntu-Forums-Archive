---
title: "Cannot Create Disk Partition or Format RAID hard-drive enclosure"
date: 2021-01-25
forum: Hardware
---

### Post by pjfin123 on 2021-01-25
I have a [NexStar® GX USB 3.0 Dual 2.5” SATA SSD/HDD RAID Enclosure]("https://vantecusa.com/products_detail.php?p_id=212&p_name=NexStar%C2%AE+GX+USB+3.0+Dual+2.5%E2%80%9D+SATA+SSD%2FHDD+RAID+Enclosure&pc_id=1&pc_name=2.5%22+Enclosures&pt_id=1&pt_name=Hard+Drive+Enclosures#tab-4") that I'm attempting to use as an external hard drive on Ubuntu 20.04 in RAID-1. The instructions say to create a partition table, and format the disk (extrapolating from Windows/Mac instructions), and it says that it is Linux compatible. I've tried formatting from both the disks app and GParted and both fail with unhelpful error messages. I've also tried formatting to both GPT and MBR and neither work. 

```
Failed to commit changes to device '/dev/sdc/' (input/output error during read on /dev/sdc) (g-bd-part-error-quark, 2)
```

Any help appreciated!

---

### Post by CelticWarrior on 2021-01-25
Welcome.

Unfortunately "[COLOR=#000000][FONT=&quot]input/output error" almost always means hardware failure (of the drive).[/FONT][/COLOR]

---

