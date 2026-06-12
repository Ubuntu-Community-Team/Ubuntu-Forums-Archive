---
title: "mdadm experts.... RAID5 question"
date: 2012-12-28
forum: Hardware
---

### Post by motoaxe on 2012-12-28
Hey guys,

Looking for a little help with my mdadm RAID5 array here.  I've been searching around for a few weeks now and nothing I've tried has been very fruitful in terms of results.

I'm running an mdadm RAID5 array with 3 Seagate 1TB drives for my local media storage.  It's always been a little finicky, but I've managed to keep it going for 3 years or so now with no real issues.  From time to time mdadm boots one drive from the array for no apparent reason... I'd notice, check the drive out and then re-add it with no ill effects.... until the start of December.

One day I was poking around and noticed this had happened again, so I unmounted the FS, tried to re-add the drive and for some reason it would not add itself back into the array (marked failed maybe? and I would've had to add it with --force?).  So I stupidly tried to stop the array completely and then rebooted, thinking that mdadm.conf would pick it back up again on boot.  First big mistake.  Kept getting kicked down into a busybox prompt on boot after it tried to boot the array.  Ended up doing a live boot from an 11.04 disk I had lying around (who uses CDs anymore, really??) and then doing a chroot to change the config file so I could boot without it trying to start my array.  

After the chroot shenanigans I booted back up into my "real" installation and tried to just re-build the array from scratch (I had commented everything out in my mdadm.conf).  This worked fine, so I figured I was good to go.  Tried to mount it up and got another clue things were very wrong.  mount couldn't figure out what FS type it should be.  fsck confirmed this:

```

e2fsck 1.42 (29-Nov-2011)
fsck.ext4: Group descriptors look bad... trying backup blocks...
Superblock has an invalid journal (inode 8).
Clear<y>? yes

*** ext3 journal has been deleted - filesystem is now ext2 only ***

The filesystem size (according to the superblock) is 488379968 blocks
The physical size of the device is 488314368 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? yes


/dev/md0: ***** FILE SYSTEM WAS MODIFIED *****
```

After this I decided it would probably be a good idea to take a low level backup (probably one or two days too late).  I picked up a couple 3TB drives and luckly had one last SATA port on my mobo.  

Back to the issue at hand, I tried some other stuff like "resize2fs -f /dev/md0" which fails with:

```

resize2fs 1.42 (29-Nov-2011)
Resizing the filesystem on /dev/md0 to 488314368 (4k) blocks.
resize2fs: Illegal triply indirect block found while trying to resize /dev/md0
Please run 'e2fsck -fy /dev/md0' to fix the filesystem
after the aborted resize operation

```

e2fsck -fy /dev/md0 fails as well (same results as above since the second question is "Abort[y]?").  doing just e2fsck -f /dev/md0 steps me through "correcting" all 100000+ inodes in my 2TB filesystem.  I actually had a power outage about 10 hours into this process (just weighted down my enter key to let it churn through the whole thing) so my box rebooted again.

I've since restored from my dd backup but still have the same issue.  Feeling *almost* defeated, I've run testdisk and photorec on the device but testdisk can't find the partition either and photorec gave me a bunch of garbage back (tens of thousands of text files with gibberish in them and empty music files).

Here's what I know:
-The UUID of the devices changed at some point, I've updated my mdadm.conf to reflect this so I can boot without it punting me into a busybox prompt.
-All devices show as clean in the new mdadm device (using mdadm --detail /dev/md0 or mdadm --examine on each of the component devices)
-testdisk finds some ext4 filesystem handles but can't recover them
-photorec gives me garbage back
-still have a dd image from one-step-too-far into the process

Here's mdadm's messages:
Degraded event:
```

This is an automatically generated mail message from mdadm
running on <snip>

A DegradedArray event had been detected on md device /dev/md0.

Faithfully yours, etc.

P.S. The /proc/mdstat file currently contains the following:

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdf1[2] sde1[1]
      1953519872 blocks level 5, 64k chunk, algorithm 2 [3/2] [_UU]

unused devices: <none>

```

And then the failure (I think from when I re-added the 3rd drive:
```

This is an automatically generated mail message from mdadm
running on eric-desktop

A Fail event had been detected on md device /dev/md0.

It could be related to component device /dev/sdg1.

Faithfully yours, etc.

P.S. The /proc/mdstat file currently contains the following:

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdc1[3] sdg1[4](F) sdf1[1]
      1953519872 blocks level 5, 64k chunk, algorithm 2 [3/1] [_U_]
      [===================>.]  recovery = 99.9% (976759708/976759936) finish=0.0min speed=57390K/sec

unused devices: <none>

```

Unfortunately since my box rebooted a bunch of times I can't provide dmesg output or anything like that, but any hints would be much appreciated!! :)

Thanks in advance.

---

### Post by motoaxe on 2012-12-29
A bit more info. 

Just tried to reassemble the array as follows and it's complaining about the uuids:

```

root@eric-desktop:~# mdadm --assemble /dev/md0 -v
mdadm: excess address on MAIL line: root - ignored
mdadm: looking for devices for /dev/md0
mdadm: no recogniseable superblock on /dev/md0p4
mdadm: no recogniseable superblock on /dev/md0p3
mdadm: no recogniseable superblock on /dev/md0p2
mdadm: no recogniseable superblock on /dev/md0
mdadm: no recogniseable superblock on /dev/sdg5
mdadm: Cannot assemble mbr metadata on /dev/sdg2
mdadm: Cannot assemble mbr metadata on /dev/sdg
mdadm: /dev/sdf1 has wrong uuid.
mdadm: Cannot assemble mbr metadata on /dev/sdf
mdadm: /dev/sde1 has wrong uuid.
mdadm: Cannot assemble mbr metadata on /dev/sde
mdadm: no recogniseable superblock on /dev/sdd5
mdadm: no recogniseable superblock on /dev/sdd2
mdadm: Cannot assemble mbr metadata on /dev/sdd1
mdadm: Cannot assemble mbr metadata on /dev/sdd
mdadm: /dev/sdc1 has wrong uuid.
mdadm: Cannot assemble mbr metadata on /dev/sdc
mdadm: no recogniseable superblock on /dev/sdb1
mdadm: Cannot assemble mbr metadata on /dev/sdb
mdadm: no recogniseable superblock on /dev/sda1
mdadm: Cannot assemble mbr metadata on /dev/sda
```

Here's the blkid output... looks like they match to me :|:

```

root@eric-desktop:~# blkid
/dev/sda1: UUID="240607f6-81f1-4444-a3f8-a25bbe240b7f" TYPE="ext4" 
/dev/sdb1: UUID="6b8347d5-563b-4984-b458-68d44d478cc9" TYPE="ext4" 
/dev/sdc1: UUID="e6cce926-934c-7508-bbe8-a6d8e87ded68" UUID_SUB="8878e310-03d4-10d1-e309-bd3c08f40f68" LABEL="ubuntu:0" TYPE="linux_raid_member" 
/dev/md0: UUID="8131dc6c-bde2-4b51-9d10-909d8a5cbf6d" TYPE="ext4" 
/dev/sdd2: UUID="10569d7e-d82a-4190-84e0-918f6938b742" TYPE="ext4" 
/dev/sdd5: UUID="1d6a2212-1610-49b6-a8c0-f3bdde36560c" TYPE="swap" 
/dev/sde1: UUID="e6cce926-934c-7508-bbe8-a6d8e87ded68" UUID_SUB="41b270df-2531-d80b-52a9-e6edbb588d3f" LABEL="ubuntu:0" TYPE="linux_raid_member" 
/dev/sdf1: UUID="e6cce926-934c-7508-bbe8-a6d8e87ded68" UUID_SUB="d012a9ce-ab8f-0816-54b8-fb1e9173032c" LABEL="ubuntu:0" TYPE="linux_raid_member" 
/dev/sdg5: UUID="43feea4f-4085-4c1b-a057-41d2e49d3bec" TYPE="ext3" 
```

---

### Post by motoaxe on 2012-12-31
More confusion ](*,)

I've tried playing with the order of the disks when re-creating the array... looks like there are ext2fs tags on two of the RAID member drives:

```

root@eric-desktop:~# mdadm --create /dev/md0 --level=5 --raid-devices=3 /dev/sde1 /dev/sdc1 /dev/sdf1
mdadm: /dev/sde1 appears to be part of a raid array:
    level=raid5 devices=3 ctime=Sun Dec 30 22:15:03 2012
mdadm: /dev/sdc1 appears to contain an ext2fs file system
    size=1953519872K  mtime=Thu Dec  6 22:09:43 2012
mdadm: /dev/sdc1 appears to be part of a raid array:
    level=raid5 devices=3 ctime=Sun Dec 30 22:15:03 2012
mdadm: /dev/sdf1 appears to contain an ext2fs file system
    size=2066766144K  mtime=Tue Dec 11 16:58:15 2029
mdadm: /dev/sdf1 appears to be part of a raid array:
    level=raid5 devices=3 ctime=Sun Dec 30 22:15:03 2012

```

I'm going to try using /dev/sdf1 as the first disk and doing another resize2fs -f on it to correct things?  Also, will I have to restore the dd image I took for each ordering?  If so I think I might be screwed because I took the image *after* the array was assembled in the wrong order.  That being said, I'm not sure I've done anything destructive... the data should still be there in some form.  Maybe try testdisk in each arrangement as well and see if it will recover the original FS.

---

### Post by motoaxe on 2013-01-02
I gave up :(

I have backups of about 3/4 of the data.  Don't mess with RAID 5 unless you have at least 5 disks to do it.  I'm only using mdadm for mirroring going forward.

---

