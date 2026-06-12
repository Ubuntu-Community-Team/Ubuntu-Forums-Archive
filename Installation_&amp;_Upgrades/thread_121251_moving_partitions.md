---
title: "moving partitions"
date: 2006-01-24
forum: Installation &amp; Upgrades
---

### Post by dninja on 2006-01-24
I currently have the following partitions on my drive:

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    hda1                    Primary   Linux swap / Solaris              3002.23 
    hda2        Boot        Primary   Linux ext3       [/boot]            98.71
    hda3                    Primary   Linux ReiserFS   [/tmp]           1003.49
    hda5                    Logical   Linux ReiserFS   [/]             20003.89
    hda6                    Logical   Linux ReiserFS   [/home]          5000.98
    hda7                    Logical   Linux ReiserFS                    3100.94
    hda8                    Logical   Linux                            10240.48
    hda9                    Logical   NTFS volume set                  20480.95
                            Logical   Free Space                       17092.14

I need to install windows and I can only do that on a primary partition but as I've no primary partitions left I need to shift things around to allow me to create a new primary one. The only partitions I need to keep are 2, 5, 6 and 7, the rest can be dropped, are there any ways to shunt this lot around to free up a 20GB primary partition?

---

