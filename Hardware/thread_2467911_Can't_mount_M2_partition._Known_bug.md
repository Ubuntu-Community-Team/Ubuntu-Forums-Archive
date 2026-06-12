---
title: "Can't mount M2 partition. Known bug?"
date: 2021-10-12
forum: Hardware
---

### Post by Mugsy323 on 2021-10-12
I have a 500GB M2 drive in my PC that I've split into a 120GB boot partition and a 350GB data partition. The first partition auto-mounts and is fine. The extended/data partition is not only ignored, but "GParted" won't even let me mount it (grayed out.)

Is this a known bug? If not, is there a (non-destructive) way to fix this?

TIA

---

### Post by Dennis N on 2021-10-12
Do you want the data partition to mount on startup? It has to be formatted, and you would need a correct entry in **/etc/fstab** to do the mounting. If you did these things, post your /etc/fstab and the output of:
```
 lsblk -o name,fstype,uuid
``` 
to check it.

---

### Post by The Cog on 2021-10-12
Maybe there is a small misunderstanding here: An **extended** partition is not a data partition - it is a partition that acts as a container for **logical** partitions. So your 350G data partition needs to be a logical partition: all logical partitions you create will automatically be placed inside the extended partition (until the extended partition is full, of course).
Hope this helps.

---

### Post by oldfred on 2021-10-12
Generally it is better to use gpt partitioning. Then no primary, extended, logical partitions. Just one type, essentially all primary.

But if BIOS booting you need a 1 or 2MB unformatted partition with bios_grub flag.
Or if UEFI booting need the ESP - efi system partition 300 to 500MB FAT32 with esp,boot flags.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

