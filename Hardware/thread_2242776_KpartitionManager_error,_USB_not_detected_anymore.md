---
title: "KpartitionManager error, USB not detected anymore"
date: 2014-09-03
forum: Hardware
---

### Post by jigar2 on 2014-09-03
Hi,
I was trying to remove a partition from my external USB disk and Kpartitionmanager gave me some error. Now the USB isn't detected. It is an old 1TB USB but was working fine earlier. Is it gone or can I use it again?

Thanks.

Heres the output of ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo fdisk -l[/FONT][/COLOR]
```

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0001f126


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1941506047   970752000   83  Linux
/dev/sda2      1941508094  1953523711     6007809    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5      1941508096  1953523711     6007808   82  Linux swap / Solaris



```

---

### Post by yancek on 2014-09-04
'Some error' is a little bit vague.  If the fdisk output you posted is the drive in question, you have one very large system partition with a small Extended partition and your swap.  What did it look like before?  Were there other partitions?  Was this drive just a data partition or did you have an OS on it?

---

### Post by jigar2 on 2014-09-04
[COLOR=#000000][FONT=Ubuntu]I don't know the exact error. I was trying to remove a NTFS partition out of the two that I had, it took a really long time and then showed me an error message. 
I realise now my external USB disk isn't showing in the fdisk output as well, those are just my system partitions on my laptop.
[/FONT]
[FONT=Ubuntu]I tried the disk on two WIN machines and no luck there either.[/FONT]
[FONT=Ubuntu]Its probably dead !
[/FONT]
[FONT=Ubuntu]Thanks for the reply[/FONT][/COLOR]

---

### Post by yancek on 2014-09-04
Might be dead.  If you are using GPT partitioning with windows 8, the fdisk output is often not accurate but it usually shows some output for any drive along with a message suggesting you use GParted.

---

