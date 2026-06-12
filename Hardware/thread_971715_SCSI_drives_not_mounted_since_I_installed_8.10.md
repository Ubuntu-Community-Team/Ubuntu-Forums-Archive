---
title: "SCSI drives not mounted since I installed 8.10"
date: 2008-11-05
forum: Hardware
---

### Post by naoli on 2008-11-05
Hi ubunteros, 

I've got one 80*Go ATA HDD and two 36 Go SCSI*HDD. Since I installed Intrepid Ibex, the 2 SCSI ones are not mounted nor recognized anymore :
```

$ sudo fdisk -l

Disque /dev/sda: 80.0 Go, 80026361856 octets
255 heads, 63 sectors/track, 9729 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Identifiant disque: 0xdfc5dfc5

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1   *           1        4721    37921401    7  HPFS/NTFS
/dev/sda2            4722        9729    40226760    5  Extended
/dev/sda5            4722        5365     5172898+  83  Linux
/dev/sda6            9519        9729     1694826   82  Linux swap / Solaris
/dev/sda7            6030        9368    26820486   83  Linux
/dev/sda8            9369        9518     1204843+  82  Linux swap / Solaris
/dev/sda9            5366        6029     5333548+  82  Linux swap / Solaris

```

Obviously this is my 80 Go HDD. 

```
$ lsscsi
sdev_scandir_sort: left parse failed
sdev_scandir_sort: left parse failed
sdev_scandir_sort: left parse failed
sdev_scandir_sort: right parse failed
[target0:0:0]type?   vendor?  model?           rev?  -
[target4:0:0]type?   vendor?  model?           rev?  -
[0:0:0:0]    disk    ATA      WDC WD800JD-60LS 10.0  -
[4:0:0:0]    cd/dvd  TSSTcorp CDW/DVD TS-H492C TB01  -
```

I think the [target0:0:0] and the [target4:0:0] are my SCSI*drives. But I can't figure out how to mount them, manually or automatically.

Any help will be appreciated ! :)

---

### Post by naoli on 2008-11-06
up :)

---

### Post by naoli on 2008-11-09
Please ?*Anyone ? :)

---

### Post by Joseph_454 on 2008-11-14
I'm having the same issue. I have two SCSI's, and now Ubuntu won't boot.

---

### Post by psusi on 2008-11-14
Hrm.. what does your dmesg say?

---

### Post by Joseph_454 on 2008-11-14
The pertinent SCSI lines are:

-------------------------------------------------------------
scsi0: pata_via
scsi1: pata_via

...

scsi 1:0:0:0 Attached scsi generic sg0 type 5
Driver 'sr' needs updating - please use bus_type methods
----------------------------------------------------------

I get dropped to a shell on boot-up, because (according to /proc/cmdline) it's looking for a drive by UUID  (root=UUID=...), but this does not exist in /dev/disk/by-uuid/...

My guess is I need to set or override the value for "root" on the command line, but I'm not sure where to look for an acceptable value.

I've used ubuntu with these drives since 7.x, so I'm not sure what has changed in 8.10

---

### Post by psusi on 2008-11-14
> **Joseph_454 said:**
> The pertinent SCSI lines are:

-------------------------------------------------------------
scsi0: pata_via
scsi1: pata_via



That's IDE, not SCSI.  What kind of disks do you have in the box?  Try just waiting a few seconds then exit from the busybox shell and see if the system continues to boot.  Also are you using the raid functions of that via controller?

---

### Post by Joseph_454 on 2008-11-14
> **psusi said:**
> That's IDE, not SCSI.  What kind of disks do you have in the box?  Try just waiting a few seconds then exit from the busybox shell and see if the system continues to boot.  Also are you using the raid functions of that via controller?
Yeah, 'SG' appears to be the (IDE) DVD drive. I'm unable to exit the shell, as it keeps dropping me back to it. The real problem appears to be the fact that the root path "/dev/disk/by-uuid/..." it's using in the boot args does not exist. I'm interpreting this to mean it needs another root path in order to find the SCSI drive to boot from. I don't find any likely candidates in /dev though. It's as if Ubuntu has suddenly become unaware of the disks in 8.10. The disks are just vanilla Maxtor SCSI; not using any RAID functionality. They worked beautifully (under Hardy) until I upgraded this AM.

---

### Post by dren on 2008-11-19
I have the same problem as you.  Ran an update and my disks vanished.  My NIC vanished too so at least you're lucky you still have your NIC.

---

