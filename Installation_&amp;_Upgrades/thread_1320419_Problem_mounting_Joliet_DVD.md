---
title: "Problem mounting Joliet DVD"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by matiaskusack on 2009-11-09
Hi everyone! I'm new on Ubuntu and I am very happy of intalled it couse it's been very effiecent for now.
 First problem came yesterday when I tried to open a Windows recorded DVD (it's been burned with Joliet Format) because I coudn't mount it for now. So if anyone knows howto mount it it will helpfull for me.
 Here i left the kernel log and the mount command y used:
```

matiaskusack@desktux:~$ sudo mount -t iso9660 /dev/sr0 /media/cdrom0
mount: block device /dev/sr0 will be mount as read only.
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       You may find aditional info on syslog, try
   dmesg | tail   
matiaskusack@desktux:~$ dmesg | tail
[ 5578.463645] sr0: rw=0, want=128, limit=4
[ 7425.335698] attempt to access beyond end of device
[ 7425.335709] sr0: rw=0, want=68, limit=4
[ 7425.335718] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[ 7666.941495] attempt to access beyond end of device
[ 7666.941508] sr0: rw=0, want=68, limit=4
[ 7666.941515] HPFS: hpfs_map_sector: read error
[ 9114.713673] attempt to access beyond end of device
[ 9114.713685] sr0: rw=0, want=68, limit=4
[ 9114.713694] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
``` Sorry about my unpolited english. Bye

---

