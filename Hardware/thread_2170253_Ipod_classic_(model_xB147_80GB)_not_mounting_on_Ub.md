---
title: "Ipod classic (model xB147 80GB) not mounting on Ubuntu 11.04"
date: 2013-08-25
forum: Hardware
---

### Post by vhml76 on 2013-08-25
[FONT=Verdana][COLOR=#000000]Hello,

I've been having problems mounting my Ipod Classic ([/COLOR][/FONT]model xB147 80GB) after formatting it with a Mac due to a db corruption. Plug it in, I get the following notification:

> Unable to mount "iPod". mount: wrong fs type, bad option, bad superblock on /dev/sdb2, missing codepage or helper program, or other error In some cases useful info is found in syslog - try dmesg | tail or so

This is what I get when I type dmesg|tail:

```
[ 5363.335508] sd 13:0:0:0: [sdb] 19488471 4096-byte logical blocks: (79.8 GB/74.3 GiB)
[ 5363.335996] sd 13:0:0:0: [sdb] Assuming drive cache: write through
[ 5363.361861]  sdb: [mac] sdb1 sdb2
[ 5363.363450] sd 13:0:0:0: [sdb] 19488471 4096-byte logical blocks: (79.8 GB/74.3 GiB)
[ 5363.363999] sd 13:0:0:0: [sdb] Assuming drive cache: write through
[ 5363.364004] sd 13:0:0:0: [sdb] Attached SCSI removable disk
[ 5363.655977] sd 13:0:0:0: [sdb] Bad block number requested
[ 5363.656005] hfs: unable to find HFS+ superblock
[ 5363.755905] sd 13:0:0:0: [sdb] Bad block number requested
[ 5363.755941] hfs: unable to find HFS+ superblock

```
Anyone have similar issues or know of a solution it would be much appreciated.

Ubuntu 11.04 (natty) GNOME 2.32.1 / [FONT=Verdana][COLOR=#000000]Ipod Classic ([/COLOR][/FONT]model xB147 80GB)

---

### Post by vhml76 on 2013-08-25
I solved my problem by formatting the Ipod in exFAT format using Windows 7 and allowing Itunes to restore it to the default settings. The Ipod now works fine with Ubuntu and Banshee media player.

---

