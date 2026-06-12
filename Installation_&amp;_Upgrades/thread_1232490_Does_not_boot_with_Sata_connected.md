---
title: "Does not boot with Sata connected"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by johanbach on 2009-08-05
Hi all.  I recently upgraded my board (ASUS M4A78 plus) and video card and reinstalled 9.04 to my IDE drive.  During the first install everything seemed fine as my SATA drives were recognized by the partitioner in the installer and even seen as a software raid (mdadm).  After I installed, I ran update manager and installed mdadm and was able to mount my raid.  I rebooted and the boot failed.  If I remove the SATA drives, I can boot into my system, but I backed up all my data on the raid, so I'd like to have both mounted.  I tried using a PCI SATA card I have, but the same thing happens.  I have even tried having 2 of the drives on the card and 2 onboard, same result.

I hope I haven't lost all my data, so I'm holding out for some kind soul with more mdadm knowledge than me to help me out.

As a side note, this happens both when the IDE drive is encrypted or not encrypted.  The point where the boot starts hanging is when the ubuntu splash screen comes up and where the encryption passphrase should be entered.

If there is a log or report that would be helpful in diagnosis please let me know and I'll run it.

Thanks!

---

### Post by johanbach on 2009-08-06
Okay, so it seems one of the drives from my raid is the culprit.  I disconnected it and the computer boots with the other three plugged in.  However, mdadm says that only two drives are present and the raid cannot be assembled.  fdisk shows that my ide drive and three sata drives are present.  The three sata drives are even marked as linux raid drives.  Does anyone have any ideas on how to rebuild my raid?

Thanks!

---

### Post by johanbach on 2009-08-07
Here is the output of some commands I thought would be helpful.  I noticed that sda1 which is part of the raid does not have a boot flag.  Would this be part of my problem?
 
sudo mdadm --assemble --scan

mdadm: /dev/md1 assembled from 2 drives - not enough to start the array.

*This shows mdadm seeing 2 drives (if I understand it correctly).*

 sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d9966

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24321   195358401   fd  Linux raid autodetect

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc1d76741

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24321   195358401   fd  Linux raid autodetect

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa1775890

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30401   244196001   fd  Linux raid autodetect

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       38350   308046343+  83  Linux
/dev/sdd2           38351       38913     4522297+   5  Extended
/dev/sdd5           38351       38913     4522266   82  Linux swap / Solaris

*This shows fdisk seeing one IDE drive and three sata drives that are linux raid.*

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
ARRAY /dev/md1 level=raid5 num-devices=4 UUID=adc01352:b88597ae:c9d9cdc5:04eea64d

# This file was auto-generated on Wed, 05 Aug 2009 17:12:12 -0500
# by mkconf $Id$

*This is the mdadm.conf file showing the raid consists of 4 drives, so three should be enough to run in degraded mode, right?*

---

