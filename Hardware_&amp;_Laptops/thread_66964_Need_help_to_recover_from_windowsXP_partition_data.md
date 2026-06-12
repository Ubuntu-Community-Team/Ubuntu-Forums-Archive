---
title: "Need help to recover from windowsXP partition data into Linux"
date: 2005-09-18
forum: Hardware &amp; Laptops
---

### Post by kmanivel on 2005-09-18
Hi,

Somehow I screwed up WindowsXP partition while installing Ubuntu 5.04, as follows.
See below for the SFDISK information.
I had used 16GB partition (/dev/hda1) as C drive in WindowsXP, the remaining 64GB   
as D drive (/dev/hda2 or /dev/hda5). The 16 GB partition has been used for installing Linux OS.

Now I need to recover the data from the 64GB D drive partition into Linux.
Please note that I can't reinstall the WindowsXP OS. I need to recover the files through Linux or any other way.

I just need to get copy some of the files in that partition. I don't have to keep that indefinitely. I must copy some of the files from that partition, Thats it.

Anybody who has information that would help me, contact me.
See below for the SFDISK information.

Thanks,
Manivel
[email]kmanivel@yahoo.com[/email]

[COLOR=Blue]--------------------------------------------------------------------------------------------------------------------
root@kmanivel:/home/kmanivel # sfdisk -l -x /dev/hda

Disk /dev/hda: 155061 cylinders, 16 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: The partition table looks like it was made
  for C/H/S=*/255/63 (instead of 155061/16/63).
For this listing I'll assume that geometry.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/hda1   *      0+   1949    1950-  15663343+  83  Linux
/dev/hda2       1950    9728    7779   62484817+   f  W95 Ext'd (LBA)
                         start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/hda3          0       -       0          0    0  Empty
/dev/hda4          0       -       0          0    0  Empty

/dev/hda5       1950+   9728    7779-  62484786   fd  Linux raid autodetect
                       start: (c,h,s) expected (1023,254,63) found (1023,1,1)
    -           1950    1949       0          0    0  Empty
    -           1950    1949       0          0    0  Empty
    -           1950    1949       0          0    0  Empty
--------------------------------------------------------------------------------------------------------------------
[/COLOR]

---

### Post by linkunderscore on 2005-09-18
[QUOTE=kmanivel]Hi,

Somehow I screwed up WindowsXP partition while installing Ubuntu 5.04, as follows.
See below for the SFDISK information.
I had used 16GB partition (/dev/hda1) as C drive in WindowsXP, the remaining 64GB   
as D drive (/dev/hda2 or /dev/hda5). The 16 GB partition has been used for installing Linux OS.

Now I need to recover the data from the 64GB D drive partition into Linux.
Please note that I can't reinstall the WindowsXP OS. I need to recover the files through Linux or any other way.

I just need to get copy some of the files in that partition. I don't have to keep that indefinitely. I must copy some of the files from that partition, Thats it.

Anybody who has information that would help me, contact me.
See below for the SFDISK information.

Thanks,
Manivel
[email]kmanivel@yahoo.com[/email]

[COLOR=Blue]--------------------------------------------------------------------------------------------------------------------
root@kmanivel:/home/kmanivel # sfdisk -l -x /dev/hda

Disk /dev/hda: 155061 cylinders, 16 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: The partition table looks like it was made
  for C/H/S=*/255/63 (instead of 155061/16/63).
For this listing I'll assume that geometry.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/hda1   *      0+   1949    1950-  15663343+  83  Linux
/dev/hda2       1950    9728    7779   62484817+   f  W95 Ext'd (LBA)
                         start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/hda3          0       -       0          0    0  Empty
/dev/hda4          0       -       0          0    0  Empty

/dev/hda5       1950+   9728    7779-  62484786   fd  Linux raid autodetect
                       start: (c,h,s) expected (1023,254,63) found (1023,1,1)
    -           1950    1949       0          0    0  Empty
    -           1950    1949       0          0    0  Empty
    -           1950    1949       0          0    0  Empty
--------------------------------------------------------------------------------------------------------------------
[/COLOR][/QUOTE]


:LOL: MOVING YOUR FAVORITE JPEGS ;) ;) ;)

---

### Post by aysiu on 2005-09-19
For some reason, the Ubuntu Guide seems to be down, but I have a backup copy:
```

sudo mkdir /media/windows
sudo mount /dev/hda2 /media/windows/ -t vfat -o iocharset=utf8,umask=000
```

Of course, if it's actually /dev/hda5, then you'd change that second part, appropriately.

---

### Post by kmanivel on 2005-09-19
The mounting method didn't work..Somehow the File System Type changed.

Its not NTFS or VFAT. It is represented as ' Linux raid autodetect'. I don't know what this means.

Anybody knows how to mount a 'RAID' partition?

Thanks,
Manivel

---

