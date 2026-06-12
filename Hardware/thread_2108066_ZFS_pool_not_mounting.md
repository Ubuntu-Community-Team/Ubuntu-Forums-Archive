---
title: "ZFS pool not mounting"
date: 2013-01-23
forum: Hardware
---

### Post by jonnier on 2013-01-23
I have a setup using 12.04 server, with zfs kernel support added via the zfsonlinux ppa.

I used zpool to create two separate pools but the second one has stopped mounting, it will only mount when I run the mountall command.

Upon googling I found a page which suggested adding 'sleep 60' directly above the wait_for_udev line in/usr/share/initramfs-tools/scripts/functions however this doesn't seem to have helped.

The zpool is created and online i can scrub it, export and reimport etc. but it won't auto mount.

Has any one else come across this??

TIA

Jon

---

### Post by tgalati4 on 2013-01-23
Output the following:

```
sudo fdisk -l
zpool status
zpool status -v
zpool history zpooldevice1
zpool history zpooldevice2
```

---

### Post by jonnier on 2013-01-25
Sorry for the delay, been driving all over the UK since I posted, but hey it's nearly the weekend now :)

I have run the commands as requested and sent the output to text files which are attached.

---

### Post by tgalati4 on 2013-01-25
You have a lot going on here:

tgalati4@Dell600m-mint14 /tmp $ grep GB fdisk.txt 
Disk /dev/sda: 60.0 GB, 60022480896 bytes
Disk /dev/sdc: 3000.6 GB, 3000592982016 bytes
Disk /dev/sdd: 3000.6 GB, 3000592982016 bytes
Disk /dev/sde: 3000.6 GB, 3000592982016 bytes
Disk /dev/sdb: 3000.6 GB, 3000592982016 bytes
Disk /dev/sdf: 3000.6 GB, 3000592982016 bytes
Disk /dev/sdg: 3000.6 GB, 3000592982016 bytes

So you have 6 x 3TB drives or 18 TB of storage.  How much RAM on this machine?

So *engohome* is 3 x 3TB and *engomedia* is 3 x 3TB and the data looks OK according to zpool status.

History for 'engohomes':
2013-01-18.13:21:10 zpool create engohomes raidz /dev/sdb /dev/sdc /dev/sdd
2013-01-18.13:22:03 zpool export engohomes
2013-01-18.13:22:50 zpool import -d /dev/disk/by-id engohomes
2013-01-18.16:29:40 zpool scrub engohomes
2013-01-20.11:07:58 zpool scrub engohomes

History for 'engomedia':
2013-01-21.13:49:39 zpool create engomedia raidz /dev/sde /dev/sdf /dev/sdg
2013-01-21.13:50:40 zpool export engomedia
2013-01-21.13:51:49 zpool import -d /dev/disk/by-id engomedia
2013-01-23.13:24:34 zpool scrub engomedia
2013-01-23.18:26:09 zpool export engomedia
2013-01-23.18:28:29 zpool import -d /dev/disk/by-id engomedia
2013-01-23.18:32:25 zpool export engomedia
2013-01-23.18:32:35 zpool import -d /dev/disk/by-id engomedia

Now run your system monitor right after boot--or start it before shutdown so it pops up for next boot and watch your RAM.  It's possible there is a RAM or CPU performance issue that is causing a timeout before the next pool is mounted.

```
free
dmesg | more
```

I run zfs on a freenas server, so it may behave differently, but mounting errors should show up in dmesg.  You might check /var/log for any other logs that may capture zfs errors.

How much space is used in each pool?  

```
df -h
```

Because there are no obvious errors, this looks like an edge case.  Try 180 or 300 seconds for your udev mount delay.  ZFS does an md5sum check on files and compares them with the md5sums stored in the directory headers.  This takes both RAM and CPU.  This is how silent data corruption is detected.  If your first pool is large, then the processing and RAM required for such checking may interfere with the mounting of the second pool.

Normally such large data pools are stored on a separate, commercial NAS, not a home-grown, ZFS-on-linux, do-it-yourself boxen.  I would use a dedicated NAS operating system such as freenas to run ZFS.  Are you running other services on this machine, or is it simply a linux storage NAS?

Although not explicitly stated in your original post, it looks like the pools mounted OK in the beginning and then after you added some data (or a lot of data) the pool stopped automounting.  The theory of data checking I proposed fits this scenario.

If this is the case, then I would write a script to check the status of the first pool and if OK, then go ahead and mount the second pool, and if that is OK, send a notifyer to wall.

Presumably you would have this server running 24/7 so you wouldn't have to boot very often.  But it would be good to have the zpool status checked every so often.  I'm not sure how often it is done, once at boot-time?  And when at other times?

---

### Post by jonnier on 2013-01-26
Thanks again for the replies.

There is 18Tb of storage across two pools, leaving 5.4Tb in each pool once the parity is taken into account.

The machine is running an AMD quad core processor clocked at 3.6GHz, with a 60Gb SSD as the boot device.  I had intended to increase the memory as when I copied data to the zpools I noticed it was maxxing out.  I only 2Gb in to get the machine up and running, so I will go to and purchase some more today, put that in and see what happens.  I'm going to add 16Gb seeing as it is cheap enough.

Currently I am setting up the unit and testing it and yes everything did work fine first off, until like you said about adding data.  engomedia currently has nearly 400Gb on it whilst engohomes only has 24Gb.

The two pools are split for usage, engohome is for mail and ftp activities, whilst engomedia is for media sharing to my tv etc as I have my office at home, so though I'd make use of it.


In the long run I intend to run cron jobs to check status and scrub the pools, I am just trying to get reacquainted with Linux after being away from it for 3 or 4 years.

If the memory update doesn't help I'll delve further into dmesg, but thanks for your help so far.

---

### Post by cousins on 2013-04-01
Any luck figuring this out? I see something similar. Two pools. The second pool I made mounts automatically but I need to use the mountall command to get the first one (also much larger) to start up. The first one (the one that now doesn't mount on boot) is a 20 TB raidz2 pool with 13x2 TB drives plus a hot spare. The second one (the one that mounts automatically) is a 5.4 TB stripe of two 3.0 TB drives.   

Thanks,

Steve

> **jonnier said:**
> Thanks again for the replies.

There is 18Tb of storage across two pools, leaving 5.4Tb in each pool once the parity is taken into account.

The machine is running an AMD quad core processor clocked at 3.6GHz, with a 60Gb SSD as the boot device.  I had intended to increase the memory as when I copied data to the zpools I noticed it was maxxing out.  I only 2Gb in to get the machine up and running, so I will go to and purchase some more today, put that in and see what happens.  I'm going to add 16Gb seeing as it is cheap enough.

Currently I am setting up the unit and testing it and yes everything did work fine first off, until like you said about adding data.  engomedia currently has nearly 400Gb on it whilst engohomes only has 24Gb.

The two pools are split for usage, engohome is for mail and ftp activities, whilst engomedia is for media sharing to my tv etc as I have my office at home, so though I'd make use of it.


In the long run I intend to run cron jobs to check status and scrub the pools, I am just trying to get reacquainted with Linux after being away from it for 3 or 4 years.

If the memory update doesn't help I'll delve further into dmesg, but thanks for your help so far.

---

### Post by jonnier on 2013-04-01
Unfortunately not.  Haven't had a good look at as I moved and the server build has temporarily stopped while my home office gets sorted out.

I upgraded memory and put in a delay but still no solution.  I'll be getting it running again this week to have a play with it again.



Jon

---

### Post by muzzamo on 2013-12-16
Any luck with this? I am getting the same problem (second pool not auto mounting). Not really sure what to try next.

---

