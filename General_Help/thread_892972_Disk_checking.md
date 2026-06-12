---
title: "Disk checking"
date: 2008-08-17
forum: General Help
---

### Post by killerdragon on 2008-08-17
Is there an application in the repositories somewhere that can do a disk check similar to scandisk ("error checking" under XP) for windows. The reason why I mention scandisk is because it can check a disk "hot" (while its in use). I dislike the autochecking after so many mounts or days...that kinda functionality is kinda annoying especially if it hits one error it will freak out and drop you to "busy box". I understand the idea behind it, but when you have 4 HDs in a server, you would rather plan to replace a HD than scramble to replace (and find out which one to replace!) ASAP. I know there are disk checking utilities for linux but they all require the HD to be unmounted (though they say you can do it mounted...they don't recommend it).

P.S. At least I am under the assumption that "Error checking" is scan disk...just renamed; do correct me if I am wrong.

---

### Post by jpkotta on 2008-08-17
You can change the max time between checks and the max number of mounts between checks, but AFAIK, you can't check the filesystem while the disk is mounted.  To increase the thresholds, use tune2fs:

```

       -c max-mount-counts
              Adjust  the  number  of  mounts after which the filesystem will be checked by e2fsck(8).  If max-mount-
              counts is 0 or -1, the number of times the filesystem is mounted will be disregarded by  e2fsck(8)  and
              the kernel.

              Staggering  the mount-counts at which filesystems are forcibly checked will avoid all filesystems being
              checked at one time when using journaled filesystems.

              You should strongly consider the consequences of  disabling  mount-count-dependent  checking  entirely.
              Bad  disk  drives,  cables,  memory, and kernel bugs could all corrupt a filesystem without marking the
              filesystem dirty or in error.  If you are using journaling on your  filesystem,  your  filesystem  will
              never  be  marked dirty, so it will not normally be checked.  A filesystem error detected by the kernel
              will still force an fsck on the next reboot, but it may already be too late to  prevent  data  loss  at
              that point.

              See also the -i option for time-dependent checking.
...
       -i  interval-between-checks[d|m|w]
              Adjust  the  maximal  time between two filesystem checks.  No postfix or d result in days, m in months,
              and w in weeks.  A value of zero will disable the time-dependent checking.

              It is strongly recommended that either -c (mount-count-dependent) or -i  (time-dependent)  checking  be
              enabled  to  force  periodic  full  e2fsck(8) checking of the filesystem.  Failure to do so may lead to
              filesystem corruption (due to bad disks, cables, memory, or kernel bugs)  going  unnoticed,  ultimately
              resulting in data loss or corruption.

```

BTW, I completely agree, fsck happens at the worst times.  I wish it would have an option to check on shutdown, and only if you allow it.

---

### Post by killerdragon on 2008-08-17
> **jpkotta said:**
> BTW, I completely agree, fsck happens at the worst times.  I wish it would have an option to check on shutdown, and only if you allow it.
Thing is, I think you can do this. I think it has to do something with messing with the values at the end of each mounted volume in fstab.
What I do know for sure, I have mine 0ed out and fsck never bothers me. 
This sounds kinda stupid right? Well, its a server running IDE drives (save the "upgrade to SATA" speech for another thread) and I know they WILL eventually go bad...but I would rather it be "flakey" and get my data off sensibly than fsck kick me to a minimal bash shell where I have very little tools at my disposal. And then I would have to scramble for a IDE - USB adapter and hook it up to another ubuntu box just to get the data off.

Imho, a more "friendly" way to do this is if fsck detects problems then don't mount that partition and just go onto the next mount point in fstab. But, log that the mount failed in syslog and let the user decide if they dare to mount the failing partition - so then at least they have all the tools at their disposal (smbclient, ftp client, nfs client...ect) to get the data off. Now, of course this "approach" wont work too well for boot partitions, but at least for those who work with servers with multiple drives it will at least give them some sort of breathing room when it comes to recovering the data off the drive.

Sorry for the long post, this totally isn't a rant just something that could improve an already great OS ;).

---

### Post by az on 2008-08-17
You are confusing CHKDSK with SCANDISK.

Chkdsk is like fsck - it checks and fixes the filesystem on the disk.  You run this when your filesystem has suffered a problem, but the hardware is intact.

Scandisk is more like badblocks - it searches the disk for bad blocks.  If it finds a bad block scandisk can modify the filesystem to try to move data out of the way.  When it works it's great, but when it doesn't, it usually leaves your data unrecoverable.  Badblocks only reports bad blocks.

Nowadays, S.M.A.R.T. is a much better way to assess hard disk problems.

See here:
[https://help.ubuntu.com/community/FaultyHardware](https://help.ubuntu.com/community/FaultyHardware)

---

### Post by killerdragon on 2008-08-17
> **az said:**
> You are confusing CHKDSK with SCANDISK.

Chkdsk is like fsck - it checks and fixes the filesystem on the disk.  You run this when your filesystem has suffered a problem, but the hardware is intact.

Scandisk is more like badblocks - it searches the disk for bad blocks.  If it finds a bad block scandisk can modify the filesystem to try to move data out of the way.  When it works it's great, but when it doesn't, it usually leaves your data unrecoverable.  Badblocks only reports bad blocks.

Nowadays, S.M.A.R.T. is a much better way to assess hard disk problems.

See here:
[https://help.ubuntu.com/community/FaultyHardware](https://help.ubuntu.com/community/FaultyHardware)
Is smartctl "selftest" safe to run on mounted and in use drives?

---

### Post by az on 2008-08-18
> **killerdragon said:**
> Is smartctl "selftest" safe to run on mounted and in use drives?

Yes, it runs in the background.

---

### Post by jpkotta on 2008-08-19
> **killerdragon said:**
> Thing is, I think you can do this. I think it has to do something with messing with the values at the end of each mounted volume in fstab.
What I do know for sure, I have mine 0ed out and fsck never bothers me. 
This sounds kinda stupid right? Well, its a server running IDE drives (save the "upgrade to SATA" speech for another thread) and I know they WILL eventually go bad...but I would rather it be "flakey" and get my data off sensibly than fsck kick me to a minimal bash shell where I have very little tools at my disposal. And then I would have to scramble for a IDE - USB adapter and hook it up to another ubuntu box just to get the data off.


No, setting those to zero doesn't prevent fscks.  From fstab manpage:
```
       The fifth field, (fs_freq), is used for these filesystems by the dump(8) command to determine  which  filesys&#8208;
       tems  need  to be dumped.  If the fifth field is not present, a value of zero is returned and dump will assume
       that the filesystem does not need to be dumped.

       The sixth field, (fs_passno), is used by the fsck(8) program to determine the order in which filesystem checks
       are done at reboot time.  The root filesystem should be specified with a fs_passno of 1, and other filesystems
       should have a fs_passno of 2.  Filesystems within a drive will be checked  sequentially,  but  filesystems  on
       different  drives  will  be checked at the same time to utilize parallelism available in the hardware.  If the
       sixth field is not present or zero, a value of zero is returned and fsck will assume that the filesystem  does
       not need to be checked.

```

---

