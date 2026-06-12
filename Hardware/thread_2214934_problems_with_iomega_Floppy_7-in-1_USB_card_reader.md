---
title: "problems with iomega Floppy 7-in-1 USB card reader"
date: 2014-04-03
forum: Hardware
---

### Post by Johan_Vandewalle on 2014-04-03
I'm just starting to use Ubuntu and installed it on my Acer Aspire 7720Z laptop (a dual boot system Ubuntu and Windows 7).

I try to use my old iomega Floppy 7-in1 USB card-reader in Ubuntu (Windows 7 has no drivers available for this old model). The device is detected and I can use the floppy drive. The memory cards aren't (Compact Flash, SD) mounted and I can't find them. Using df -h in the terminal gives following result:[INDENT]johan@ACER-Aspire-7720Z:~$ df -h
Filesystem          Size     Used   Avail  Used%  Mounted on
/dev/sdb2           28G     1,1G     25G      4%   /
none                 4,0K          0    4,0K      0%   /sys/fs/cgroup
udev                 1,5G     4,0K    1,5G      1%   /dev
tmpfs               301M     1,3M   299M      1%   /run
none                 5,0M          0   5,0M      0%   /run/lock
none                 1,5G     212K   1,5G      1%   /run/shm
none                100M       40K  100M      1%   /run/user
/dev/sdb3           23G     182M    22G      1%   /boot
/dev/sdb4           42G      1,4G    38G      4%   /home
/dev/sdb5           28G       46M    26G      1%   /tmp
/dev/sdb6           51G      6,4G    42G     14%   /usr
/dev/sdb7           14G     998M    12G       8%   /var
/dev/sdb8           19G       44M    18G      1%   /srv
/dev/sdb9           23G     217M    22G      1%   /opt
/dev/sdb10          51G      52M    48G      1%   /usr/local
/dev/sda2          149G      75G    74G     51%   /media/johan/FE1884A118845A93
/dev/sda1          100M      26M    75M    26%   /media/johan/Door systeem gereserveerd
/dev/sdb1          140G      15G  126G     11%   /media/johan/Gegevens
/dev/sdc            1,4M     619K  805K     44%   /media/johan/P3HD
[/INDENT]

The last device /dev/sdc is the floppy drive on the iomega Floppy 7-in-1 USB card-reader (/dev/sdc). The Compact Flash card and the SDHC card (in fact a MicroSDHC card within an adaptor) don't appear in the list.

My laptop has a build in SD card-reader. When I put a 16 GB SDHC card (in the SD-adaptor) in that reader. The card is recognized and auto mounted.

Using df -h in the terminal gives following result:[INDENT]johan@ACER-Aspire-7720Z:~$ df -h[/INDENT]
[INDENT]Filesystem              Size     Used   Avail  Used%  Mounted on[/INDENT]
[INDENT]/dev/sdb2               28G     1,1G     25G      4%   /[/INDENT]
[INDENT]none                     4,0K          0    4,0K      0%   /sys/fs/cgroup[/INDENT]
[INDENT]udev                     1,5G     4,0K    1,5G      1%   /dev[/INDENT]
[INDENT]tmpfs                   301M     1,3M   299M      1%   /run[/INDENT]
[INDENT]none                     5,0M          0   5,0M      0%   /run/lock[/INDENT]
[INDENT]none                     1,5G     212K   1,5G      1%   /run/shm[/INDENT]
[INDENT]none                    100M       40K  100M      1%   /run/user[/INDENT]
[INDENT]/dev/sdb3               23G     182M    22G      1%   /boot[/INDENT]
[INDENT]/dev/sdb4               42G      1,4G    38G      4%   /home[/INDENT]
[INDENT]/dev/sdb5               28G       46M    26G      1%   /tmp[/INDENT]
[INDENT]/dev/sdb6               51G      6,4G    42G     14%   /usr[/INDENT]
[INDENT]/dev/sdb7               14G     998M    12G       8%   /var[/INDENT]
[INDENT]/dev/sdb8               19G       44M    18G      1%   /srv[/INDENT]
[INDENT]/dev/sdb9               23G     217M    22G      1%   /opt[/INDENT]
[INDENT]/dev/sdb10             51G      52M    48G      1%   /usr/local[/INDENT]
[INDENT]/dev/sda2             149G      75G    74G     51%   /media/johan/FE1884A118845A93[/INDENT]
[INDENT]/dev/sda1             100M      26M    75M    26%   /media/johan/Door systeem gereserveerd[/INDENT]
[INDENT]/dev/sdb1             140G      15G  126G     11%   /media/johan/Gegevens[/INDENT]
[INDENT]/dev/sdc               1,4M     619K  805K     44%   /media/johan/P3HD
/dev/mmcblk0p1     15G       32K   15G       1%   /media/johan/6633-6633[/INDENT]

This time both the floppy drive on the iomega Floppy 7-in-1 USB card-reader (/dev/sdc) and the 16 GB MicroSDHC card (in the SD-adaptor) on the laptops build in SD card-reader (/dev/mmcblk0p1) are shown in the list.

Who knows how I can get the Compac Flash Card reader and the SD card-reader on the iomega Floppy 7-in-1 USB Card reader working properly. Do I need a different driver and if so, where can I get it?

Johan Vandewalle

---

