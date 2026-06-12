---
title: "Compaq NC6320 Partition Help...Please"
date: 2008-06-15
forum: Hardware
---

### Post by Camuso21 on 2008-06-15
I have a HP (Compaq NC6320) that came with a 5.46GB FAT32 partition used for recovery purposes. The problem is that I have backup disks and don't really need/want it anymore. Furthermore I want to shrink my Windows NTFS partition so I can make more room for my Ubuntu install. 

I've downloaded a KNOPPIX live CD so I could theoretically shrink my Windows partition, and resize my Ubuntu partition. My only problem is that the only partitions that show up in QTParted is the  Windows NTFS partition, and the HP Backup FAT32 partition. It doesn't appear to have a Ubuntu EXT3 or swap partition. Is this because I just used Wubi to install? Would you kindly offer some assistance?

---

### Post by overdrank on 2008-06-15
> **Camuso21 said:**
> I have a HP (Compaq NC6320) that came with a 5.46GB FAT32 partition used for recovery purposes. The problem is that I have backup disks and don't really need/want it anymore. Furthermore I want to shrink my Windows NTFS partition so I can make more room for my Ubuntu install. 

I've downloaded a KNOPPIX live CD so I could theoretically shrink my Windows partition, and resize my Ubuntu partition. My only problem is that the only partitions that show up in QTParted is the  Windows NTFS partition, and the HP Backup FAT32 partition. It doesn't appear to have a Ubuntu EXT3 or swap partition. Is this because I just used Wubi to install? Would you kindly offer some assistance?

Hi and yes Wubi does not create a partition for ubuntu. That is the use for wubi to make it easier for new user.

---

### Post by prshah on 2008-06-15
> **Camuso21 said:**
> It doesn't appear to have a Ubuntu EXT3 or swap partition. 

Wubi does not create a partition, as you have divined. You can however  eliminate your FAT32 partition and resize your NTFS prtition, and then resize your wubi partition with [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html).. see the section "Resizing virtual disks using LVPM"

btw, if you want to xfer your wubi install into a full fledged ubuntu partition-based installation, LVPM is designed to do that. The guide in the URL above is very detailed and with tons of screenshots. A proper partition-based installation of ubuntu is streets faster than a Wubi installation.

---

### Post by Camuso21 on 2008-06-15
Well ok then, thanks for the quick replies, I'll have to see what I can do then. Is there anyway I can create a EXT3 partition for Ubuntu and maintain all of my current settings?

---

### Post by prshah on 2008-06-15
> **Camuso21 said:**
>  Is there anyway I can create a EXT3 partition for Ubuntu and maintain all of my current settings?

Err... I repeat:

[b]> **prshah said:**
> 
btw, if you want to xfer your wubi install into a full fledged ubuntu partition-based installation, LVPM is designed to do that. The guide in the URL above is very detailed and with tons of screenshots. A proper partition-based installation of ubuntu is streets faster than a Wubi installation.[/b]

---

### Post by Camuso21 on 2008-06-15
Ha, whoops must have glanced over that bit. Thanks a lot, it looks like I figured out how I'm going to spend my day.

---

