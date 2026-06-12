---
title: "Raid 0 access after change of main disc"
date: 2014-01-15
forum: Hardware
---

### Post by martinyt on 2014-01-15
Hello forum,

I have changed my main disk (where boot and system are). I addition to this disc, I have to discs in a raid 0 setup (raid 0+1 I think, one disk mirroring the other). How, if possible, can I no connect or set up this raid without losing data?

---

### Post by TheFu on 2014-01-15
Use the backup to migrate, after all, RAID is not a backup.  There may be other ways, but having a backup would remove 95% of the fears.

Also, there is a huge difference between RAID0, RAID1 and RAID10 - which do you have?  Is this a hw-raid or mdadm solution?  If mdadm please post the contents of /proc/mdstat. It will answer our questions.  The output of **sudo parted -l** would help too. After that data is provided, an exact solution for mdadm should be possible.  It would be easiest to just restore the old mdadm.conf and fstab settings from the older OS disk, if you have it.

I know you didn't ask, but RAID0 needs to be avoided for any data needed more than 24 hrs. It is dangerous. Data loss is much more likely - multiply by the number of disks in the RAID0-set.  Basically, only video editors should use RAID0 for their temporary storage needs ... and I suspect those folks have moved to SSDs storage already since no spinning disk can come close to SSD performance.  A few SSDs in RAID0 would be amazing for that use.

Only you know your needs and will pick the best option from the available information.

---

### Post by martinyt on 2014-01-16
Thanks for the answer! I' will take a backup of the most important things, before proceding


/proc/mdstat
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sdb1[0] sdc1[1]
      976759936 blocks [2/2] [UU]

Seems I have a raid1 setup - sorry about that....it's been some years since I sat this up.

sudo parted -l:
Model: ATA SAMSUNG HD300LJ (scsi)
Disk /dev/sda: 300GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  294GB  294GB   primary   ext3            boot
 2      294GB   300GB  6095MB  extended
 5      294GB   300GB  6095MB  logical   linux-swap(v1)


Model: ATA SAMSUNG HD103SJ (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1000GB  1000GB  primary  ext4         raid


Model: ATA SAMSUNG HD103SJ (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1000GB  1000GB  primary  ext4         raid


Model: ATA Corsair CSSD-F60 (scsi)
Disk /dev/sdd: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  60.0GB  60.0GB  primary  ext4         boot


Model: Linux Software RAID Array (md)
Disk /dev/md1: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  1000GB  1000GB  ext4


It is a mdadm solution yes. I have kept the commands I used for setting this up (at least I think I used it)

mknod /dev/md0 b 9 2 

mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1 

mke2fs -j /dev/md0


"would be easiest to just restore the old mdadm.conf and fstab settings from the older OS disk, if you have it." I have it and I am still using it. So how do I restore the old mdadm.conf fstab settings?  I am changing from the 
"/dev/sda: 300GB" to the ssd disk "/dev/sdd: 60.0GB"

Thanks

---

### Post by martinyt on 2014-01-20
Ok, so I figured it out. 

mdadm --assemble --scan

did the trick - rebooted and than I could  mount it. 
Edited fstad to automount.

---

