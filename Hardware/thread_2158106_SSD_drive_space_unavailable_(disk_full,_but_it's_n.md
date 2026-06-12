---
title: "SSD drive space unavailable (disk full, but it's not)"
date: 2013-06-27
forum: Hardware
---

### Post by sysmatck on 2013-06-27
I've got some Disk Full errors when copying some files, and this is the second time this happends. When I open gParted, available space is about 7gb on the drive I'm copying. This is my first SSD drive, and I'm running it with a lubuntu 13.04 x64.

When I do: $ LANG=C df -h
I get something like this:

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        17G  5,7G  9,8G  37% /
/dev/sda3        92G   85G  1,6G  99% /home
------------------------------------------------------------

This is weird: 17 - 5,7 = 11,3; And 92 - 85 = 7; I guess something went wrong with the default blocks size when formating. But I'm a little out of ideas... I don't know how to search for a solution, that's why I'm asking for help here! Drive is a "hp ssd v300a". SMART test on drivers manager points nothing wrong!

$ LANG=C sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00002818

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     5326847     2662400   82  Linux swap / Solaris
/dev/sda2   *     5326848    40142847    17408000   83  Linux
/dev/sda3        40142848   234440703    97148928   83  Linux

---

### Post by Cheesemill on 2013-06-28
By default 5% of the space on an ext4 volume is reserved for roots use only in case of emergencies. This way if a user or runaway process uses up all of the space there is still enough free space left for root to keep the system functioning.

This explains the discrepancy between the actual free space remaining and the free space reported by tools such as df.

---

### Post by sysmatck on 2013-06-28
Ok, so... 92Gb * 0.05 = 4,6Gb; 4,6 + 1,6 = 6,2Gb...

Yeah, almost there, but I guess I've got an explanation... I had no space problems with my HDD, I' missing this 6,2G! Any information about a better option for fs type? Does reiserfs has better "use rates", at least to use on my /home ?

---

### Post by Cheesemill on 2013-06-28
You can change the amount of reserved space with the tune2fs command. The following will change it to 1%...
```
tune2fs -m 1 /dev/sda3
```

The partition needs to be unmounted at the time so it's probably just going to be easiest to boot into recovery mode to do this.

On large RAID arrays I've reclaimed 500GB of space before by setting it to 0%. This is perfectly safe to do on a storage only drive but I'd recommend leaving at least a GB or so reserved on your root partition. Remember that this reserved space was introduced when drives were only a couple of hundred MB is size so 5% was an acceptable default. With today's drives though the default is way too much in my opinion.

Also bear in mind that it isn't a good idea to run an ext partition at over 90% capacity anyway as you will start to get heavy fragmentation.

---

### Post by sysmatck on 2013-06-28
Great! I did... And also moved some rarely used .vdi to a pen-drive

Now I have:

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        17G  5.7G  9.8G  37% /
/dev/sda3        92G   71G   20G  78% /home

About 1gb is still protected, and I don't pretend to use the drive untill 99%, but sometimes, while moving files this space is usefull!

Tnx.

---

