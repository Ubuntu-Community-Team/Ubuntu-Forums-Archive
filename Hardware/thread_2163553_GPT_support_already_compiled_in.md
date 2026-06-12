---
title: "GPT support already compiled in?"
date: 2013-07-18
forum: Hardware
---

### Post by 1clue on 2013-07-18
Hi,

I'm looking to set up RAID on two 3T drives, they'll be RAID1 and the entire drive will be in one volume group.

I'm not getting the full size, and it makes me wonder if GPT support exists in any of the pre-compiled kernels I might have access to?

GPT=GUID Partition Support.  I don't exactly see the option in /boot/config-3.8.0-26-generic, so maybe it changed.

Maybe it's CONFIG_EFI_PARTITION?  If so I'm in luck.

Thanks.

---

### Post by steeldriver on 2013-07-18
Try formatting with parted using 'mklabel gpt'

[http://ubuntuforums.org/showthread.php?t=2159567&highlight=gpt](http://ubuntuforums.org/showthread.php?t=2159567&highlight=gpt) <-- appears to be a similar issue

---

### Post by oldfred on 2013-07-18
You can use gdisk or gparted as well.

 GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

I have not used RAID but have used gpt since 10.10.

  I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitionin

---

