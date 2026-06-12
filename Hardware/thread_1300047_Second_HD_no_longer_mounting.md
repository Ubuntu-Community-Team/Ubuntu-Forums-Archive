---
title: "Second HD no longer mounting"
date: 2009-10-24
forum: Hardware
---

### Post by qneill on 2009-10-24
I have a second internal HD, [B]previously mounted and working.
[/B] This morning I find the PC unresponsive, doesn't answer pings, blank screen (was running gnome), nothing on the virtual terminals (Ctl-Alt-F1-6), so I powered it down and rebooted.

Now some partitions (the important ones) on the HD won't mount!  I believe the drive is functional, since /dev/sdb4 is mounted as swap and /dev/sdb3 is mounted as /mnt/ub7.10 - my old ubuntu partition).

I fear I pulled the plug on a "non-responsive PC" but it was running fsck or something.

Is the superblock corrupted?

Are the block id's (output from blkid) cached or stored on the disk?

What tools do I have at my disposal?

```

# mount /dev/sdb1
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

# blkid | grep sdb1
/dev/sdb1: UUID="3e4a975a-e771-4bd5-975b-bf27c019cac0" TYPE="jfs" 
# grep 3e4a /etc/fstab
UUID=3e4a975a-e771-4bd5-975b-bf27c019cac0 /z    jfs     relatime        0       2
# dmesg | grep sdb
[    1.937133] sd 0:0:1:0: [sdb] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    1.937154] sd 0:0:1:0: [sdb] Write Protect is off
[    1.937157] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.937192] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.937263] sd 0:0:1:0: [sdb] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    1.937282] sd 0:0:1:0: [sdb] Write Protect is off
[    1.937285] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.937319] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.937323]  sdb: sdb1 sdb2 sdb3 sdb4
[    1.985901] sd 0:0:1:0: [sdb] Attached SCSI disk
[   11.461397] Adding 1959920k swap on /dev/sdb4.  Priority:-1 extents:1 across:1959920k

```

-- 
Quentin :confused: and :scared:

---

### Post by qneill on 2009-10-24
Scared the crap out of me.
This must be a record for the following quotient
[FONT="Courier New"][CENTER]COST_OF_DATA_LOSS * FEAR_ANXIETY
--------------------------------
(SPEED_OF_SOLUTION + TIME_TO_FOLLOWUP_POST)
[/CENTER][/FONT]
Here's how I fixed it.  Let's try fsck, which if the superblock is hosed (in the old days) meant this is an act of desparation:
```

# fsck /dev/sdb1
fsck 1.41.4 (27-Jan-2009)
fsck: fsck.jfs: not found
fsck: Error 2 while executing fsck.jfs for /dev/sdb1

```
... [ do some googling here ] I guess I need jfsutils ...
```

# sudo apt-get install jfsutils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libavutil49
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  jfsutils
0 upgraded, 1 newly installed, 0 to remove and 10 not upgraded.
Need to get 262kB of archives.
After this operation, 1143kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com jaunty/main jfsutils 1.1.12-2 [262kB]
Fetched 262kB in 20s (12.6kB/s)                                                                                                                                                           
Selecting previously deselected package jfsutils.
(Reading database ... 108539 files and directories currently installed.)
Unpacking jfsutils (from .../jfsutils_1.1.12-2_i386.deb) ...
Processing triggers for man-db ...
Setting up jfsutils (1.1.12-2) ...
[CODE]
Okay try the desparate act again...

```
# sudo fsck /dev/sdb1
fsck 1.41.4 (27-Jan-2009)
fsck.jfs version 1.1.12, 24-Aug-2007
processing started: 10/24/2009 14.56.30
Using default parameter: -p
The current device is:  /dev/sdb1
Block size in bytes:  4096
Filesystem size in blocks:  14659304
**Phase 0 - Replay Journal Log
Filesystem is clean.
```

WTF? Is it that easy?

```
# sudo mount /dev/sdb1
# mount | grep sdb1
/dev/sdb1 on /z type jfs (rw,relatime)
[/CODE]

Holy crap!  Success in 3 minutes!

My only complaint is that when a **JFS partition is corrupted, why is reported as a bad superblock**?

Crisis averted, back to your regularly scheduled program.
-- 
Quentin :happy:

---

### Post by qneill on 2009-10-24
Can I change the thread title with a reply?
I guess technically only the JFS partitions weren't mounting.
-- 
Quentin

---

