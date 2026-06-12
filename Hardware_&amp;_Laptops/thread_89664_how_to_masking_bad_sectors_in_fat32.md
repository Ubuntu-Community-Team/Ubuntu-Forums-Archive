---
title: "how to masking bad sectors in fat32"
date: 2005-11-13
forum: Hardware &amp; Laptops
---

### Post by Newlad on 2005-11-13
there are many bad sectors in my hard disk.
i can use #fsck -c  to repair the ext3 partition
but i can not repair other fat32 partitions

i try to use the commands

#sudo fsck.vfat -t -a /dev/hda1

but it's other tell me the bad sectors' position,but no repair it
every time when i boot the system,will check the vfat partitions on volume manage and then puts the bad sections' position,but i can into my ubuntu

my questions:

1.how can i repair the fat32 file system, let my dear ubuntu don's check the   fat32 partitions on booting,and how to let the system don't use the bad  sectors.

2.when i use #fsck -c ,it will put the bad sectors to bad list,but where are the bad list?

3.how can i kown which file is on which bad sector?


PS:
because the bad sectors ,the windows XP can not  loading in,so i only use ubuntu,in my school ,there are few person use linux ,i am like a rare  species,
so i want to get help here

thanks for everyone,to have a good day

---

### Post by aysiu on 2005-11-13
A co-worker of mine said there's something on [Knoppix](http://www.knopper.net/knoppix/index-en.html) that's a repair NTFS utility. I'm not sure what it's called, but maybe it can fix FAT32 as well? It's worth a shot.

---

