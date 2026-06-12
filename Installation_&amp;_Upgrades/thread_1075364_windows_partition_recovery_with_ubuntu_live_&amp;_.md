---
title: "windows partition recovery with ubuntu live &amp; testdisk?"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by kinuxn00b on 2009-02-20
hi 

i have a problem , my partition table got corrupted earlier while i was trying to install ubuntu hardy on to the windows c: drive 

the windows Hdd was partitioned as c: primary and the rest D: ,E: ,F: logical drives

i was able to view the corrupted partitions with testdisk 

[IMG]http://img11.imageshack.us/img11/1989/screentestdiskjc6.jpg[/IMG]

should i mark that movies drive as L too before i write the change ?


thanks

---

### Post by caljohnsmith on 2009-02-20
Are those testdisk results you posted from the "deeper search" feature, or are they from the "quick scan"? I would definitely not recommend using the results from just the quick scan, because often they are not accurate as far as finding the valid partitions. Before you use testdisk to recover your partitions, please post the output of:
```
sudo fdisk -lu
sudo sfdisk -d
```
And we can work from there if you want.

---

### Post by ubunutstm on 2009-02-21
sorry i had to re register ,

those are "deeper scan" results 

```
fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   234436544   117218241    f  W95 Ext'd (LBA)



```


```
sfdisk -d

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=234436482, Id= f
/dev/sda2 : start=        0, size=        0, Id= 0
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0



```



thanks

---

### Post by caljohnsmith on 2009-02-21
OK, if those were the deeper scan results, I would go ahead and mark the "Movies" partition as "L" (assuming you want to recover it), or if testdisk doesn't let you mark it as "L", you should be able to mark it as "P" instead. I would mark "Appz" and "Vmware" as "L" as you showed in your first post. Once you've done that, you can press "enter" to get the next screen, then select "Write" to write the new partition table. Let me know how that goes or if you run into problems.

---

