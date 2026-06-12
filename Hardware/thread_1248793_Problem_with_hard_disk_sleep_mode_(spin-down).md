---
title: "Problem with hard disk sleep mode (spin-down)"
date: 2009-08-24
forum: Hardware
---

### Post by topas on 2009-08-24
Hello,

I have Problems to get a hard disk to sleep mode. This disk is normaly not used. It is a fast and loud Western Digital WD740ADFD. I Tried several steps:

1. $ hdparm -S2 /dev/sdb
There was no effect

2. $ hdparm -Y /dev/sdb
The disk spins down but it stars again after a while.

3.  Not to mount the disk at all. After boot I tried:
$ hdparm -Y /dev/sdb
The disk spins down but it stars again after two minutes, even it is not mounted!

I tried some configurations in /etc/hdparm.conf but I had the same effects as with the command line.
I have no Idea why a even not mounted disk will spin up after two minutes?

My System is a:
$ uname -a
Linux lalu 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux

The Kernel gives the following messages before spin up:
[ 4520.908380] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[ 4520.908387] ata2.00: waking up from sleep
[ 4520.908401] ata2: hard resetting link
[ 4521.789303] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 4521.812661] ata2.00: configured for UDMA/133
[ 4521.812708] ata2: EH complete
[ 4521.812869] sd 1:0:0:0: [sdb] 145226112 512-byte hardware sectors: (74.3 GB/69.2 GiB)
[ 4521.812897] sd 1:0:0:0: [sdb] Write Protect is off
[ 4521.812902] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[ 4521.812943] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

Thanks for help

---

### Post by pathorn on 2009-09-04
I've been having the same issue with a 160GB Western Digital disk. As in your case, the drive is not mounted (I was intending to spin up/mount it for periodical backups, but nothing else).

When I use "sdparm --command=stop /dev/sdb" I get the same message as you.

When I use "hdparm -Y /dev/sdb" I get nothing... but a few seconds later I see about 100 blocks being read in "iostat" and the disk spins back up.

When I use "hdparm -C /dev/sdb" when it should be in the sleep state, it helpfully spins up the drive and then reports "active/idle"

Is there no way to put this drive into power saving mode without physically shutting of the computer and unplugging it?  Is there a way of entirely disabling access until the next reboot so that it cannot spin back up--like simulating a fatal error and turning off the drive?

---

### Post by brycenesbitt on 2009-10-14
I'm having the same issue with two similar Western Digital drives:

Model=WDC WD2500AAJS-57B4A0
, FwRev=01.03A01, SerialNo=WD-WCAT14752165 

Issuing a manual "-y" command puts the drive to sleep

```

# hdparm -S1 /dev/sg0
/dev/sg0: setting standby to 1 (5 seconds)

# hdparm -C /dev/sg0
/dev/sg0: drive state is:  active/idle

# hdparm -y /dev/sg0
/dev/sg0: issuing standby command

# hdparm -C /dev/sg0
/dev/sg0: drive state is:  standby

```But the automatic timer does not work.  Crud!
Several other drives work fine.

---

