---
title: "hard disk errors on 2 of 4 RAID-5 drives"
date: 2009-10-12
forum: Hardware
---

### Post by balance07 on 2009-10-12
console is displaying the following errors during boot:
```

Starting up ...
Loading, please wait...
[   28.557598] ata3: exception Emask 0x1 SAct 0x0 SErr 0x0 action 0x0 t4
[   28.557647] ata3: CPB resp_flags 0x11: , CMD error
[   30.805038] ata4: exception Emask 0x1 SAct 0x0 SErr 0x0 action 0x0 t4
[   30.805087] ata4: CPB resp_flags 0x11: , CMD error

```
the disk setup is:
sda: 1 TB disk: one 1 TB partition
sdb: 1 TB disk: one 1 TB partition
sdc: 1.5 TB disk: one 1 TB partition, one 500 GB partition
sdd: 1.5 TB disk: one 1 TB partition, one 500 GB partition

four 1 TB partitions in RAID-5 array
two 500 GB partitions in RAID-1 array
both RAID arrays in one LVM logical volume.

the whole system freezes not long after boot. running Ubuntu Server 8.04.3

i've been able to keep the system up for a few hours at a time and run some rsync to get data off of the drives, but does anyone know what i should expect soon?

are both these new 1.5 TB drives gonna die? any way to check or fix?

thanks for all ideas!

---

### Post by Dark_Stang on 2009-10-12
Get your stuff backed up, then run the manufacturer's diagnostics tools on each drive to see exactly what drives are failing. If they're not failing, just rebuild the RAID and reformat. If they are failing and they're under warranty, get thems wapped out.

---

### Post by balance07 on 2009-10-13
yeah i'm trying to backup, but the server keeps freezing. any idea why that is happening, when these drives are purely storage drives? / and /home are on another physical drive.

---

