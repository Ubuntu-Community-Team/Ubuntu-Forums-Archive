---
title: "lvm hard drive failure"
date: 2008-08-12
forum: General Help
---

### Post by Goofee691 on 2008-08-12
hi all i have a lvm setup for a file server and recentlly one of my 500GB drives has failed, i have tried to find information on recoving the data but it all has to deal with raid but i only have lvm spread across 2 500GB drives and 2 250GB drives. one of the 500GB drives suddenlly stopped spinning up and now i want to try to recover as much data as i can from my remaining drives since they should have worked like a JBOD raid setup. how would this be possible?

---

### Post by Goofee691 on 2008-08-15
anyone able to help with this?

---

### Post by Goofee691 on 2008-08-25
well its been a week and no reply, i have over 1TB of data spread out over these 4 drives and want to try and get some of it back. i hope i do not have to send the drive in for data recovery even though the drive still is in warranty due to the cost of recovery.

---

### Post by Goofee691 on 2008-09-25
ok well i just finished using norton Ghost to backup all the the drives completely to my new 1TB drive so i could safely experiment on the drives

here is some more information hopefully with this someone can help me

```
sean@Sean-Desktop:~$ sudo pvscan
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  PV unknown device   VG 1.5TB   lvm2 [465.76 GB / 0    free]
  PV /dev/sde1        VG 1.5TB   lvm2 [465.76 GB / 0    free]
  PV /dev/sdg1        VG 1.5TB   lvm2 [232.88 GB / 0    free]
  PV /dev/sdh1        VG 1.5TB   lvm2 [232.88 GB / 0    free]
  Total: 4 [1.36 TB] / in use: 4 [1.36 TB] / in no VG: 0 [0   ]

```

```
sean@Sean-Desktop:~$ sudo lvdisplay
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Volume group "1.5TB" not found

```

```
sean@Sean-Desktop:~$ sudo vgdisplay
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Volume group "1.5TB" not found

```

```
sean@Sean-Desktop:~$ sudo pvdisplay
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Can't read 1.5TB: skipping
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Can't read 1.5TB: skipping
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Can't read 1.5TB: skipping
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Can't read 1.5TB: skipping
```

```
sean@Sean-Desktop:~$ sudo fdisk -l

Disk /dev/sda: 160 GB, 160039272960 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1       19456   156280288    7  HPFS/NTFS

Disk /dev/sdb: 160 GB, 160039272960 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *           1         122      979933   83  Linux
/dev/sdb2             123       19457   155300355   fd  Lnx RAID auto

Disk /dev/sdc: 160 GB, 160039272960 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdc1               1         122      979933   82  Linux swap
/dev/sdc2             123       19457   155300355   fd  Lnx RAID auto

Disk /dev/sdd: 160 GB, 160039272960 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdd1               1         122      979933   82  Linux swap
/dev/sdd2             123       19457   155300355   fd  Lnx RAID auto

Disk /dev/sde: 500 GB, 500105249280 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sde1               1       60801   488384001   8e  Linux LVM

Disk /dev/sdf: 1000 GB, 1000202273280 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdf1               1      121601   976760001    b  FAT32

Disk /dev/md0: 477 GB, 477099141120 bytes
255 heads, 63 sectors/track, 58004 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/md0p1               1       58005   465925131   83  Linux 

Disk /dev/sdg: 250 GB, 250056737280 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdg1               1       30401   244196001   8e  Linux LVM

Disk /dev/sdh: 250 GB, 250056737280 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdh1               1       30401   244196001   8e  Linux LVM

```

well thats all i was able to come up with on the internet and i tried something else which i think im going to have to restore my images for since i do not know how to restore the backup it made

```
sean@Sean-Desktop:~$ sudo vgreduce 1.5TB -v --removemissing
    Finding volume group "1.5TB"
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find all physical volumes for volume group 1.5TB.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
  Couldn't find device with uuid 'NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu'.
    Creating directory "/etc/lvm/archive"
    Archiving volume group "1.5TB" metadata (seqno 6).
    1.5TB/Data has missing extents: removing (including dependencies)
    Removing LV Data from VG 1.5TB
    Removing PV with UUID NzHJwi-WcIG-wxo2-1Ysn-9U7j-3rrj-LNUoVu from VG 1.5TB
    Creating directory "/etc/lvm/backup"
    Creating volume group backup "/etc/lvm/backup/1.5TB" (seqno 7).
  Wrote out consistent volume group 1.5TB

```

now pvscan shows everything as free

```
sean@Sean-Desktop:~$ sudo pvscan
  PV /dev/sde1   VG 1.5TB   lvm2 [465.76 GB / 465.76 GB free]
  PV /dev/sdg1   VG 1.5TB   lvm2 [232.88 GB / 232.88 GB free]
  PV /dev/sdh1   VG 1.5TB   lvm2 [232.88 GB / 232.88 GB free]
  Total: 3 [931.52 GB] / in use: 3 [931.52 GB] / in no VG: 0 [0   ]
```

---

### Post by russlar on 2008-09-25
Doesn't look like there is a way, unless you were taking snapshots of your LVM before it crashed. without RAID 1 or RAID 5, you don't have any fault-tolerance. LVM alone does not protect you; all LVM does is allow you to span a filesystem across multiple physical devices.

---

### Post by Goofee691 on 2008-09-25
yep i set up the lvm purely to span the data temporarily just i never got to setting up raid

now so i don't have to bother with restoring those images i made how do i undo the last thing i did since it said it made a backup

---

### Post by _sAm_ on 2008-09-25
I just have to ask; so if one disk from a PV fails the complete LVM/PV fails? 

According to this guide here; [http://www.howtoforge.com/linux_lvm](http://www.howtoforge.com/linux_lvm) you can remove the disk(lets call it /dev/sdb1) from the PV with:

sudo vgreduce [vg name] /dev/sdb1
then:
sudo pvremove /dev/sdb1

Or am I missing something?

---

### Post by Goofee691 on 2008-09-25
that would be nice if its possible that way but how i under stand it that is for if their is no data on the drive you are removing and that you have used pvmove to remove the data from that drive, it also assumes that your volume group has unused space that that data can be moved to.

im no expert on lvm so someone correct me if im wrong

at current after a talk in irc im going to send the failed drive in for data recovery

---

### Post by panayk on 2008-09-25
According to the man pages, it looks like the disk has to be unused before it can be removed. But, also, there is an option "--partial" that can be used to access the volume groups that are affected by the failed disks. Maybe that way some of the data can be salvaged. See 'man lvm'.

---

### Post by Goofee691 on 2008-09-25
what command do you use this -- partial with?

---

### Post by _sAm_ on 2008-09-25
When it comes for the data on the disk that failed I think its lost for good. You can pay for getting it back, some firms work with that, but that would cost you a lot(and I mean _a lot_). 

For the other disk on your LVM there is this -- partial command:
[http://kbase.redhat.com/faq/FAQ_85_5843.shtm](http://kbase.redhat.com/faq/FAQ_85_5843.shtm)
But as I understand it you had to make the file with vgcfgbackup before the drive failed.

Without it I think it is lost as well, see these two:
[http://groups.google.com/group/linux.redhat/browse_thread/thread/4c7b29019d33437b](http://groups.google.com/group/linux.redhat/browse_thread/thread/4c7b29019d33437b)
[http://linux.derkeiler.com/Newsgroups/comp.os.linux.hardware/2006-09/msg00142.html](http://linux.derkeiler.com/Newsgroups/comp.os.linux.hardware/2006-09/msg00142.html)

Hope I am wrong here. 

I am running LVM myself on 1.5 TB, and I thought I would only loose the data on the disk that failed, not all the rest. So this scares me:-/ I do have backup, but still. 
I like to have the storage as one pool, so I think I will try mhddfs when next Ubuntu comes out. Its the same as LVM but you don't loose the data on the other disk if one fail(if I understand it correctly).
You can read about it here: [http://debaday.debian.net/2008/05/25/mhddfs-join-several-real-filesystems-together-to-form-a-single-larger-one/](http://debaday.debian.net/2008/05/25/mhddfs-join-several-real-filesystems-together-to-form-a-single-larger-one/)

---

