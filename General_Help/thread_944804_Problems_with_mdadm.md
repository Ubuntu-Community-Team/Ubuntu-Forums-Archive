---
title: "Problems with mdadm"
date: 2008-10-11
forum: General Help
---

### Post by christo16 on 2008-10-11
Hi,
I'm trying to setup raid 5 with 5 x 500GB drives.  Using this guide ([http://bfish.xaedalus.net/?p=188](http://bfish.xaedalus.net/?p=188)) I've been trying to set it up.  But when I issued the 
```
sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=5 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1
```
It is successful and when checking its status, this is what comes up
```
Personalities : [raid6] [raid5] [raid4] 
md0 : active raid5 sdf1[5] sde1[3] sdd1[6](F) sdc1[1] sdb1[0]
      1953535744 blocks level 5, 64k chunk, algorithm 2 [5/3] [UU_U_]
      [>....................]  recovery =  0.1% (560896/488383936) finish=3130.9min speed=2596K/sec

```
Then it completes, after only building the array for a minutes.  The raid shows up in GParted but cannot be formatted or mounted.

Any help would be appreciated!

---

### Post by christo16 on 2008-10-12
Up!

---

### Post by fjgaude on 2008-10-12
After the array finishes building you need to put a filesystem onto it:

```
sudo mkfs -t ext3 /dev/md0
```

Then you can mount it. GParted doesn't undestand raid arrays.

Let us know how you are doing.

---

### Post by christo16 on 2008-10-12
> **fjgaude said:**
> After the array finishes building you need to put a filesystem onto it:

```
sudo mkfs -t ext3 /dev/md0
```

Then you can mount it. GParted doesn't undestand raid arrays.

Let us know how you are doing.

Hi fjgaude,

Thanks for your help.  I tried that and received this:
```
hris@ubuntubox:~$ sudo mkfs -t ext3 /dev/md0
mke2fs 1.40.8 (13-Mar-2008)
Could not stat /dev/md0 --- No such file or directory

The device apparently does not exist; did you specify it correctly?

```

What doesn't make sense is how when I run --complete, it finishes in a couple minutes. I thought building a large raid 5 takes hours to build?  This is what I get when I run "cat /proc/mdstat" after a couple minutes:
```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid5 sdf1[5](S) sde1[3] sdd1[6](F) sdc1[1] sdb1[0]
      1953535744 blocks level 5, 64k chunk, algorithm 2 [5/3] [UU_U_]
      
unused devices: <none>

```

Any other thoughts?  I've tried building a 4 drive raid 5 and it did the same thing.

---

### Post by fjgaude on 2008-10-12
That /sdd1 with the (F) I think means "failure"... not sure.

Your /md0 didn't get created... if you cannot install a filesystem to it.

Have you read, studied:

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)
 /usr/share/doc/mdadm/FAQ.gz  and md.txt.gz
 [http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)

yet?

I don't know what to suggest... your array is not being built for some reason. What does

```
sudo fdisk -l
```

show?

You may messed the drives up with GParted, if you tried to partition or put in a filesystem with it.

As last resort you can --zero-superblock each drive and start over.

---

### Post by christo16 on 2008-10-12
Hi fjgaude, here is the contents of the fdisk list.
```

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d7b6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       35725   286961031   83  Linux
/dev/sda2           35726       36481     6072570    5  Extended
/dev/sda5           35726       36481     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00045d76

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00098118

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000680ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dda66

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00012288

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       60801   488384001   fd  Linux raid autodetect

```

I might try the zero-superblock, is that something I do in fdisk?

---

### Post by fjgaude on 2008-10-12
Your fdisk -l looks as it should.

You zero superblocks, drive-by-drive, like so:

```
sudo mdadm --zero-superblock /dev/sd[nn]
```

If your array is assembled, you have to umount it, then stop it, else the drives will show being busy.

Time for some reading, study, eh?

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)
 /usr/share/doc/mdadm/FAQ.gz  and md.txt.gz
 [http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)

---

### Post by christo16 on 2008-10-15
Hi fjgaude,
Thanks for all your help, I'll read up on those docs.  I just have one more question, it would seem to me that its a software problem not a hardware problem with one of the drives or the 5 bay drive enclosure I'm using right?

Thanks!

---

### Post by fjgaude on 2008-10-15
Well, if you can't create an array, one that is degraded, and then have the ability to issue the --display **mdadm** command, I can't say what it is.

I just don't know what to suggest if you can't create.

---

### Post by christo16 on 2008-10-19
Hi fjgaude,

Just wanted to post a follow up, if any one else has a similar issue.  Taking your advice that "sdd1[6](F)" was some sort of error, I created a 4 drive array without sdd and it created the array.  I then tried to zero the drive and got an input/output error, probably is a hardware (with the drive) issue.

Thanks!

---

### Post by fjgaude on 2008-10-20
That's good to know, one drive in an array that is bad doesn't permit mdadm to create. Wow! would never have thought such. Thanks!

---

