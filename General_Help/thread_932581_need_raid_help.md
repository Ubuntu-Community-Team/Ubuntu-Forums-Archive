---
title: "need raid help"
date: 2008-09-28
forum: General Help
---

### Post by eppo on 2008-09-28
ok, so i have a ubuntu server box set up. i have 5 sata hard drives.  i set up a raid5 at install. all worked fine till today. i'm running it as a mythbackend as well as other stuff. i was watching some recorded programing from my front end and the playback just stopped. server was unresponsive. after a reboot, i cant get the raid back up. in syslog i get these error msg regarding the raid:
```
Sep 28 15:06:06 ubuntuserver kernel: [   41.205558] md: md0 stopped.
Sep 28 15:06:06 ubuntuserver kernel: [   41.379969] md: bind<sde1>
Sep 28 15:06:06 ubuntuserver kernel: [   41.379990] md: could not bd_claim sde1.
Sep 28 15:06:06 ubuntuserver kernel: [   41.380023] md: md_import_device returned -16
Sep 28 15:06:06 ubuntuserver kernel: [   41.380045] md: could not bd_claim sde1.
Sep 28 15:06:06 ubuntuserver kernel: [   41.380075] md: md_import_device returned -16
Sep 28 15:06:06 ubuntuserver kernel: [   41.380080] md: could not bd_claim sde1.
Sep 28 15:06:06 ubuntuserver kernel: [   41.380109] md: md_import_device returned -16
Sep 28 15:06:06 ubuntuserver kernel: [   41.380114] md: could not bd_claim sde1.
Sep 28 15:06:06 ubuntuserver kernel: [   41.380143] md: md_import_device returned -16
Sep 28 15:06:06 ubuntuserver kernel: [   41.454998] md: md0 stopped.
Sep 28 15:06:06 ubuntuserver kernel: [   41.455010] md: unbind<sde1>
Sep 28 15:06:06 ubuntuserver kernel: [   41.455014] md: export_rdev(sde1)
Sep 28 15:06:06 ubuntuserver kernel: [   41.463245] md: bind<sdb1>
Sep 28 15:06:06 ubuntuserver kernel: [   41.463619] md: bind<sdc1>
Sep 28 15:06:06 ubuntuserver kernel: [   41.463923] md: bind<sdd1>
Sep 28 15:06:06 ubuntuserver kernel: [   41.464280] md: bind<sde1>
Sep 28 15:06:06 ubuntuserver kernel: [   41.464420] md: bind<sda3>
Sep 28 15:06:06 ubuntuserver kernel: [   41.499193] Attempting manual resume
Sep 28 15:06:06 ubuntuserver kernel: [   41.499196] swsusp: Resume From Partition 8:2
Sep 28 15:06:06 ubuntuserver kernel: [   41.499197] PM: Checking swsusp image.
Sep 28 15:06:06 ubuntuserver kernel: [   41.499612] PM: Resume from disk failed.

```
and i just noticed this, all the other drives look like this:

```

Sep 28 15:06:06 ubuntuserver kernel: [   41.055466]  sdd: sdd1
Sep 28 15:06:06 ubuntuserver kernel: [   41.068054] sd 1:0:1:0: [sdd] Attached SCSI disk
Sep 28 15:06:06 ubuntuserver kernel: [   41.068104] sd 2:0:0:0: [sde] 976773168 512-byte hardware sectors (500108 MB)
Sep 28 15:06:06 ubuntuserver kernel: [   41.068112] sd 2:0:0:0: [sde] Write Protect is off
Sep 28 15:06:06 ubuntuserver kernel: [   41.068113] sd 2:0:0:0: [sde] Mode Sense: 00 3a 00 00
Sep 28 15:06:06 ubuntuserver kernel: [   41.068124] sd 2:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 28 15:06:06 ubuntuserver kernel: [   41.068154] sd 2:0:0:0: [sde] 976773168 512-byte hardware sectors (500108 MB)
Sep 28 15:06:06 ubuntuserver kernel: [   41.068160] sd 2:0:0:0: [sde] Write Protect is off
Sep 28 15:06:06 ubuntuserver kernel: [   41.068162] sd 2:0:0:0: [sde] Mode Sense: 00 3a 00 00
Sep 28 15:06:06 ubuntuserver kernel: [   41.068173] sd 2:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

but the sde drive looks like this:

```

Sep 28 15:06:06 ubuntuserver kernel: [   41.068175]  sde: sde1
Sep 28 15:06:06 ubuntuserver kernel: [   41.080413] sd 2:0:0:0: [sde] Attached SCSI disk
Sep 28 15:06:06 ubuntuserver kernel: [   41.083630] sd 0:0:0:0: Attached scsi generic sg0 type 0
Sep 28 15:06:06 ubuntuserver kernel: [   41.083645] sd 0:0:1:0: Attached scsi generic sg1 type 0
Sep 28 15:06:06 ubuntuserver kernel: [   41.083659] sd 1:0:0:0: Attached scsi generic sg2 type 0
Sep 28 15:06:06 ubuntuserver kernel: [   41.083673] sd 1:0:1:0: Attached scsi generic sg3 type 0
Sep 28 15:06:06 ubuntuserver kernel: [   41.083685] sd 2:0:0:0: Attached scsi generic sg4 type 0

```
can anyone help me get this raid back up again?
thanks
Joe

---

### Post by fjgaude on 2008-09-28
Well, the first thing you can try is:

```
sudo mdadm --assemble -f --scan
```

and see what happens.

---

### Post by eppo on 2008-09-28
mdadm: /dev/md0 has been started with 4 drives (out of 5).

so that leads me to believe it is something with that sde drive?
what would be the best way to test it? or any other things you could come up with?

---

### Post by eppo on 2008-09-28
i just tried to mount /dev/md0 and it mounted. it wouldnt mount before, and i've just been sitting downstairs watching tv. shouldnt the msg above have said it was using all 5?

---

### Post by fjgaude on 2008-09-28
What does

```
sudo mdadm -D /dev/md0
```

show?

---

### Post by eppo on 2008-09-28
/dev/md0:
        Version : 00.90.03
  Creation Time : Sun Sep  7 14:39:47 2008
     Raid Level : raid5
     Array Size : 1793367808 (1710.29 GiB 1836.41 GB)
  Used Dev Size : 448341952 (427.57 GiB 459.10 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Sep 28 19:26:34 2008
          State : clean, degraded
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 69a2ea09:b978d90b:9c682ae7:cd63b594
         Events : 0.212396

    Number   Major   Minor   RaidDevice State
       0       8        3        0      active sync   /dev/sda3
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1
       4       0        0        4      removed

---

### Post by eppo on 2008-09-29
so does this mean that i should troubleshoot a hardware problem with /dev/sde1?

---

### Post by eppo on 2008-09-29
ok, i took out /dev/sde and put it in another computer it works fine.  so i dont think its the drive, do you think it might be configured wrong?

---

### Post by fjgaude on 2008-09-29
If /dev/sde was part of an array, and you physically took it out and put it into another computer, I don't see how it could work correctly. The drive would have a pattern of data that wouldn't be easy to read.

Can you think of anything that might have caused this drive to fall out of the array, leaving four working correctly?

Afte mounting degraded array, what does

```
sudo watch cat /proc/mdstat
```

show?

---

### Post by eppo on 2008-09-29
well, i just wanted to make sure the drive actually worked, i plugged it into a win box to make sure it would see it.



Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sda3[0](S) sde1[4](S) sdd1[3](S) sdc1[2](S) sdb1[1](S)
      2401877696 blocks

unused devices: <none>

---

### Post by fjgaude on 2008-09-29
You used the **watch cat /proc/mdstat** command on an unmounted array?

I wanted to see if the array was still syncing up with only four drives.

Well, if the array will not assemble with all five drives, one being inactive, or bad, the normal way to achieve success is to stop the array, unmount it and then fault the bad drive, zero its **superblock**, then add it back as a spare, then assemble the array, if in your case with four drives then as five.

I know this is tough. You have to know what you are doing to pull this off.

I can't understand why /dev/sde fell out of the array. There is a reason. Can't you think what it might be?

---

### Post by eppo on 2008-09-29
what commands would i use to achieve this? since that /dev/sde drive is essencially doing nothing, it should be worth a try.

tell you the truth, it may have not even worked from the begining, i've always had a total of 1.7 terabytes worth of space.

---

### Post by eppo on 2008-09-29
here is what it looks like mounted:

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sda3[0] sdd1[3] sdc1[2] sdb1[1]
      1793367808 blocks level 5, 64k chunk, algorithm 2 [5/4] [UUUU_]

unused devices: <none>

---

### Post by fjgaude on 2008-09-29
Before I attempt to tell you what to do, and believe me it will not be easy without truly knowing what has happened and why, how big is each partition of the five drives? You say 1.7TB total, for maybe three of the drives, for in raid5 you have the sum of each drive minus one. How would we get to the 1.7?

Also I take it you do not have a backup for what is on the present array?

---

### Post by eppo on 2008-09-29
i do have a backup, but it is a few weeks old, where i dont mind losing what i have on there, i would of course be happier to keep what is there.
what i have are 5 500 gig drives, all seagates. 
on sda, i have a 40 gig linux partition, and 1 gig swap, and the rest (sda3) is part of the raid.
the other 4 drives are 1 partition which is part of the raid.

---

### Post by fjgaude on 2008-09-29
The only thing I've never been able to do is use a multi-partition drive in an array. You seem to have done that.

So you have five drives that would end up using about 430GB of each for the array. Then three times 430 equals about 1.4TB, and four would be 1.72TB. So at one time you did have all five in the array working correctly.

Now tell me, you took the sbe drive out of the array, had the array auto re-sync?

The reason I ask is we have to know how to treat the sdb drive in putting it back in. Do we need to zero the superblock or not? Do we just add it to the array? Do we assemble the existing array using a stated four devices? Then after adding assemble it again using five? Get my drift?

Here's some stuff to study:

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)
 /usr/share/doc/mdadm/FAQ.gz  and md.txt.gz
 [http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)

Will get back soon, but maybe not until tomorrow morning.

---

### Post by eppo on 2008-09-30
thank you for the raid docs. i've always used raidtools in slack before, so using mdamd confused me. 
so, i should just mdadm /dev/md0 -r /dev/sde1
and then try and add it back using mdadm /dev/md0 -a /dev/sde1
before i do that, i'm going to take the drive out again, and start the raid up, and see if it starts without the drive in the system at all. if it does, my guess is it isn't using that drive at all, and it should be safe to remove.
i'd still like to know what this is about in dmesg: 
md: could not bd_claim sde1.
[   37.888624] md: md_import_device returned -16
[   37.888640] md: could not bd_claim sde1.
[   37.888670] md: md_import_device returned -16
[   37.888673] md: could not bd_claim sde1.
[   37.888701] md: md_import_device returned -16
[   37.888704] md: could not bd_claim sde1.
[   37.888736] md: md_import_device returned -16

---

### Post by eppo on 2008-09-30
so i figured i would give it a try and i did:
/sbin/mdadm /dev/md0 --add /dev/sde1
mdadm --assemble -f --scan
now in dmesg i got:
[75880.270452] md: bind<sde1>
[75880.307865] RAID5 conf printout:
[75880.307870]  --- rd:5 wd:4
[75880.307872]  disk 0, o:1, dev:sda3
[75880.307876]  disk 1, o:1, dev:sdb1
[75880.307878]  disk 2, o:1, dev:sdc1
[75880.307880]  disk 3, o:1, dev:sdd1
[75880.307883]  disk 4, o:1, dev:sde1
[75880.308001] md: recovery of RAID array md0
and in mdstat i get:
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sde1[5] sda3[0] sdd1[3] sdc1[2] sdb1[1]
      1793367808 blocks level 5, 64k chunk, algorithm 2 [5/4] [UUUU_]
      [>....................]  recovery =  3.2% (14383744/448341952) finish=199.1min speed=36320K/sec

unused devices: <none>



looking good?

---

### Post by fjgaude on 2008-09-30
I guess so... let us know how it goes, if it mounts, etc.

Don't forget the **man mdadm** pages as a source for info.

---

### Post by eppo on 2008-10-01
looks like it works. around 10:30am i vnc'd into the box and started up virtualbox, and started up 2 guest operating systems, win2003 server and XP. not long after that i stopped getting logs, and i woke up around 7pm and the system was unresponsive. when i rebooted the box, the array was still ok, but in dmesg i get this error:
```

[   42.363550] md: bind<sde1>
[   42.363581] md: could not bd_claim sde1.
[   42.363614] md: md_import_device returned -16
[   42.363636] md: could not bd_claim sde1.
[   42.363669] md: md_import_device returned -16
[   42.363672] md: could not bd_claim sde1.
[   42.363699] md: md_import_device returned -16
[   42.363702] md: could not bd_claim sde1.
[   42.363728] md: md_import_device returned -16
[   42.431882] md: md0 stopped.
[   42.431892] md: unbind<sde1>
[   42.431897] md: export_rdev(sde1)
[   42.441612] md: bind<sdb1>
[   42.441999] md: bind<sdc1>
[   42.442383] md: bind<sdd1>
[   42.442766] md: bind<sde1>
[   42.442920] md: bind<sda3>
[   42.449619] raid5: device sda3 operational as raid disk 0
[   42.449622] raid5: device sde1 operational as raid disk 4
[   42.449624] raid5: device sdd1 operational as raid disk 3
[   42.449627] raid5: device sdc1 operational as raid disk 2
[   42.449630] raid5: device sdb1 operational as raid disk 1
[   42.450116] raid5: allocated 5324kB for md0
[   42.450118] raid5: raid level 5 set md0 active with 5 out of 5 devices, algorithm 2
[   42.450120] RAID5 conf printout:
[   42.450121]  --- rd:5 wd:5
[   42.450122]  disk 0, o:1, dev:sda3
[   42.450123]  disk 1, o:1, dev:sdb1
[   42.450124]  disk 2, o:1, dev:sdc1
[   42.450125]  disk 3, o:1, dev:sdd1
[   42.450127]  disk 4, o:1, dev:sde1

```
i think i'll set up the crash question in a new thread.

---

