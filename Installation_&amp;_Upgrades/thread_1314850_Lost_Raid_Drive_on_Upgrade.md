---
title: "Lost Raid Drive on Upgrade"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by p314i on 2009-11-04
If memory serves me correct, I lost the same mounted drives last time I upgraded.

The situation is this, I have two physical drives in a mirrored array (md0, md1, md2 for /, swap, and /home) that mount fine after upgrade.  I have two additional physical drives in a mirrored array (md3) that are not mounting after upgrade.

A two part question, what do I need to change to get them to mount on boot?  And second, how do I set things up so that I don't have to go through this everytime I upgrade?

Best.

Edit:  After some additional searching I found a post that suggested the nodmraid flag to the grub options on boot.  My raid is back.  It is, more or less, solved.  Now, if I can fix the other minor problems - internet connectivity being high priority....

---

### Post by p314i on 2009-11-05
Some additional information.

It seems my /etc/mdadm/mdadm.conf file was altered.  After the upgrade I have this:

```
rob@Ubuntu:~$ sudo more /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=ed6328ea:6d0415a7:5c63eca1:21758821
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=7851030e:d37f7db4:d6a60d57:67baf657
ARRAY /dev/md2 level=raid1 num-devices=2 UUID=6b00fc3f:49db5cdd:eaa9c022:e33e0eb6
ARRAY /dev/md/d3 level=raid1 num-devices=2 metadata=00.90 UUID=dd80dd73:a6bbbcb6:ca66c3a1:f2e4c2cd

# This file was auto-generated on Fri, 19 Sep 2008 06:19:10 +0000
# by mkconf $Id$

```

I have tried commenting out the line that has "/dev/md/d3" since that seems out of place and replacing it with the same line with "/dev/md3" which would be consistent with the others.  No change.  I also tried removing the "metadata=00.90", again, no change.

Running blkid gives the following:

```
rob@Ubuntu:~$ sudo blkid
[sudo] password for rob: 
/dev/sda1: UUID="ed6328ea-6d04-15a7-5c63-eca121758821" TYPE="linux_raid_member" 
/dev/sda2: UUID="7851030e-d37f-7db4-d6a6-0d5767baf657" TYPE="linux_raid_member" 
/dev/sda3: UUID="6b00fc3f-49db-5cdd-eaa9-c022e33e0eb6" TYPE="linux_raid_member" 
/dev/sdb1: UUID="ed6328ea-6d04-15a7-5c63-eca121758821" TYPE="linux_raid_member" 
/dev/sdb2: UUID="7851030e-d37f-7db4-d6a6-0d5767baf657" TYPE="linux_raid_member" 
/dev/sdb3: UUID="6b00fc3f-49db-5cdd-eaa9-c022e33e0eb6" TYPE="linux_raid_member" 
/dev/sdc: TYPE="promise_fasttrack_raid_member" 
/dev/sdd: TYPE="promise_fasttrack_raid_member" 
/dev/sde1: UUID="66dc5b4b-af90-40fc-91ff-31a4bb3282e4" TYPE="ext3" 
/dev/md0: UUID="399c3bcd-5919-4f92-ab60-0340c6ed89f1" TYPE="ext3" 
/dev/md1: UUID="6382644c-16aa-4eeb-b04a-964149bfb40d" TYPE="swap" 
/dev/md2: UUID="0c469aa8-1384-4499-8dda-63b15ef17231" TYPE="ext3"
```

The two lost drives that make up md3 are in slots /sdc and /sdd.

Finally, if I open gparted I see the following drives:

/dev/mapper/pdc_bdgfhji (465.66 GiB) - I have no idea what this is.  It says it is unallocated.
/dev/sda and /dev/sdb are fine
/dev/sdc lists the following under information:
```

File System: ext3
Size: 465.76 GiB
Flags: raid

Path: /dev/sdc1
Status: Not mounted
Label:
UUID:

First Sector: 63
Last Sector: 976768064
Total Sectors: 976768002

Warning:
e2label: No such file or directory while trying to open /dev/sdc1
Couldn't find valid filesystem superblock.

Couldn't find valid filesystem superblock.

dumpe2fs 1.41.9 (22-Aug-2009)
dumpe2fs: No such file or
directory with trying to open /dev/
sdc1

Unable to read the contents of this file system!
Because of this some operations may be unavailable.

```
/dev/sdd lists similar info.

I could use some insight if anyone has any.

Thanks.

---

