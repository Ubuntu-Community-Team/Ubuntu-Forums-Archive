---
title: "Help with GRUB on FAT16"
date: 2009-07-12
forum: Installation &amp; Upgrades
---

### Post by brandon88tube on 2009-07-12
I'm kind of confused and need some help with getting grub working on a FAT16 partition.

---

### Post by merlinus on 2009-07-12
Can you provide more info, e.g. what operating systems are installed on your computer, are you dual-booting, what is on the fat16 partition?

Posting results of

```
sudo fdisk -l
```

will be useful.

---

### Post by brandon88tube on 2009-07-12
I'm trying to dual boot with Ubuntu and Windows XP. I would like to have a separate partition for boot < that being on the fat16. The rest shouldn't really matter, but I'll post my fdsisk anyways. If I have to do a full reinstall of everything, I'm fine with that because XP isn't even really setup and Ubuntu was just installed as well.
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5582e76e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5222    41945683+   7  HPFS/NTFS
/dev/sda2            7834       19457    93369780    7  HPFS/NTFS
/dev/sda3  *         5223        5238      128520    6  FAT16
/dev/sda4            5239        7833    20844337+   5  Extended
/dev/sda5            7573        7833     2096482+  82  Linux swap / Solaris
/dev/sda6            5239        7572    18747792   83  Linux


```

---

### Post by cariboo on 2009-07-12
I'm not sure Ubuntu will boot if you try to format /boot as fat16. I personally don't see the need for a separate boot partition, I usually just have 3 partitions /, /home and swap.

---

### Post by brandon88tube on 2009-07-12
I want grub to be on a separate partition so that if anything happens to the main install grub won't screw up.

---

### Post by brandon88tube on 2009-07-12
Nevermind, its not that important. When I find that I have more free time and I still want to do this, that is when I will mess with it. Sorry to waste time.

---

