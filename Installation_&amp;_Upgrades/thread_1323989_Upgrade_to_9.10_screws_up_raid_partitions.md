---
title: "Upgrade to 9.10 screws up raid partitions"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by scintilla on 2009-11-12
I upgraded from 9.04 to 9.10 with no reported problems.  However when I booted 9.10 kernel 2.6.31 for the first time, it hung after "waiting for root filesystem" - and then when I re-booted with the older kernel (2.6.28 ) all my raid1 drives were degraded, running with 1 device only out of 2.   After applying the change to allow booting with degraded raid drives (and repairing the raid arrays in 2.6.28 ), it now boots into 2.6.31 but still every time I boot it loses one of each pair of raid drives.

More worryingly, on re-boot into 2.6.28 some of the "lost" partitions are not recognised, so for example a raid1 partition on /dev/sda1 and /dev/sdb1 degrades to /dev/sdb1, and /dev/sda1 does not even show up as a valid device after re-booting.   GParted shows it as having an invalid superblock, and I had to re-format the partition from the liveCD to get it back into the array.

I can't find this problem reported on the forums so far, and I've no idea what's going on - can anyone help please?

I'm running the AMD64 kernel, disk configuration as follows

/dev/md0   = /dev/sda1, sdb1, currently unused  (all arrays are Raid1) 
/dev/md2  =  /dev/sda5, sdb5  mounted as /
/dev/md1  =  /dev/sda7, sdb7  used as LVM2  (including /home and /usr)
/dev/md2 = /dev/sda8, sdb8 also used as LVM2

fdisk -l output: 

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00008164

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  fd  Linux RAID autodetect
/dev/sda2               7      121601   976711837+   5  Extended
/dev/sda5   *           7        1830    14651248+  fd  Linux RAID autodetect
/dev/sda6            1831        2559     5855661   82  Linux swap / Solaris
/dev/sda7            2560       32953   244139773+  fd  Linux RAID autodetect
/dev/sda8           32954       77272   355992336   fd  Linux RAID autodetect

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00008164

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           6       48163+  fd  Linux RAID autodetect
/dev/sdb2               7      121601   976711837+   5  Extended
/dev/sdb5   *           7        1830    14651248+  fd  Linux RAID autodetect
/dev/sdb6            1831        2559     5855661   82  Linux swap / Solaris
/dev/sdb7            2560       32953   244139773+  fd  Linux RAID autodetect
/dev/sdb8           32954       77272   355992336   fd  Linux RAID autodetect

Disk /dev/md0: 49 MB, 49217536 bytes
2 heads, 4 sectors/track, 12016 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md2: 15.0 GB, 15002763264 bytes
2 heads, 4 sectors/track, 3662784 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md2 doesn't contain a valid partition table

Disk /dev/md1: 250.0 GB, 249998999552 bytes
2 heads, 4 sectors/track, 61034912 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md3: 364.5 GB, 364536070144 bytes
2 heads, 4 sectors/track, 88998064 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md3 doesn't contain a valid partition table
```


Syslog from 2.6.31 boot
```
Nov 11 22:23:00 gracix kernel: [    1.000026] ata4: SATA link down (SStatus 0 SControl 300)
Nov 11 22:23:00 gracix kernel: [    1.000054] ata6: SATA link down (SStatus 0 SControl 300)
Nov 11 22:23:00 gracix kernel: [    1.000066] ata5: SATA link down (SStatus 0 SControl 300)
Nov 11 22:23:00 gracix kernel: [    1.180015] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov 11 22:23:00 gracix kernel: [    1.180026] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 11 22:23:00 gracix kernel: [    1.180034] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 11 22:23:00 gracix kernel: [    1.180851] ata2.00: ATAPI: TSSTcorp CDDVDW SH-S223Q, SB01, max UDMA/100, ATAPI AN
Nov 11 22:23:00 gracix kernel: [    1.181802] ata2.00: configured for UDMA/100
Nov 11 22:23:00 gracix kernel: [    1.186334] ata3.00: ATA-7: SAMSUNG HD103UJ, 1AA01113, max UDMA7
Nov 11 22:23:00 gracix kernel: [    1.186338] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Nov 11 22:23:00 gracix kernel: [    1.186356] ata1.00: ATA-7: SAMSUNG HD103UJ, 1AA01113, max UDMA7
Nov 11 22:23:00 gracix kernel: [    1.186360] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Nov 11 22:23:00 gracix kernel: [    1.192714] ata3.00: configured for UDMA/133
Nov 11 22:23:00 gracix kernel: [    1.192734] ata1.00: configured for UDMA/133
Nov 11 22:23:00 gracix kernel: [    1.192810] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD103UJ  1AA0 PQ: 0 ANSI: 5
Nov 11 22:23:00 gracix kernel: [    1.192897] sd 0:0:0:0: Attached scsi generic sg0 type 0
Nov 11 22:23:00 gracix kernel: [    1.192925] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Nov 11 22:23:00 gracix kernel: [    1.192960] sd 0:0:0:0: [sda] Write Protect is off
Nov 11 22:23:00 gracix kernel: [    1.192965] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov 11 22:23:00 gracix kernel: [    1.192980] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 11 22:23:00 gracix kernel: [    1.193079]  sda:
Nov 11 22:23:00 gracix kernel: [    1.193580] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223Q  SB01 PQ: 0 ANSI: 5
Nov 11 22:23:00 gracix kernel: [    1.198042]  sda1 sda2 <sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Nov 11 22:23:00 gracix kernel: [    1.198096] Uniform CD-ROM driver Revision: 3.20
Nov 11 22:23:00 gracix kernel: [    1.198160] sr 1:0:0:0: Attached scsi CD-ROM sr0
Nov 11 22:23:00 gracix kernel: [    1.198186] sr 1:0:0:0: Attached scsi generic sg1 type 5
Nov 11 22:23:00 gracix kernel: [    1.198229] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD103UJ  1AA0 PQ: 0 ANSI: 5
Nov 11 22:23:00 gracix kernel: [    1.198299] sd 2:0:0:0: Attached scsi generic sg2 type 0
Nov 11 22:23:00 gracix kernel: [    1.198322] sd 2:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Nov 11 22:23:00 gracix kernel: [    1.198352] sd 2:0:0:0: [sdb] Write Protect is off
Nov 11 22:23:00 gracix kernel: [    1.198356] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Nov 11 22:23:00 gracix kernel: [    1.198370] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 11 22:23:00 gracix kernel: [    1.198443]  sdb:
Nov 11 22:23:00 gracix kernel: [    1.198492] ata8: port disabled. ignoring.
Nov 11 22:23:00 gracix kernel: [    1.200568]  sda5 sdb1 sdb2 < sdb5 sda6 sdb6 sda7 sdb7 sda8 >
Nov 11 22:23:00 gracix kernel: [    1.233921] sd 0:0:0:0: [sda] Attached SCSI disk
Nov 11 22:23:00 gracix kernel: [    1.242692]  sdb8 >
Nov 11 22:23:00 gracix kernel: [    1.242896] sd 2:0:0:0: [sdb] Attached SCSI disk
```

In the syslog I was surprised to see under sdb:  what looks like a mixed-up list of partitions - is something going wrong here?

Thanks in advance for any advice...

---

### Post by finni on 2009-11-12
> **scintilla said:**
> 
Syslog from 2.6.31 boot
[CODE]Nov 11 22:23:00 gracix kernel: [    1.000026] ata4: SATA link down (SStatus 0 SControl 300)
Nov 11 22:23:00 gracix kernel: [    1.000054] ata6: SATA link down (SStatus 0 SControl 300)
Nov 11 22:23:00 gracix kernel: [    1.000066] ata5: SATA link down (SStatus 0 SControl 300)
Nov 11 22:23:00 gracix kernel: [    1.180015] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov 11 22:23:00 gracix kernel: [    1.180026] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 11 22:23:00 gracix kernel: [    1.180034] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)


You seem to have more than two hdd's? It's possible that hdd's have changed their layout because kernel has changed (For.ex. sda have changed to sdd, etc.) Can you post your /etc/mdadm/mdadm.conf file?

---

### Post by scintilla on 2009-11-12
Finni,
Thanks for your reply.    I only have 2 drives (sata2 is a DVDROM drive) but you are right the change of kernel did something strange with the devices:   when I did ls /dev/sd* in 2.6.31 it only showed /dev/sda and /dev/sdb/ - no partitions at all.   Some of the partitions showed up by a different name when I did mdadm --detail /dev/md0: (see the last line)

```
/dev/md0:
        Version : 00.90
  Creation Time : Sun Feb 22 14:09:49 2009
     Raid Level : raid1
     Array Size : 48064 (46.95 MiB 49.22 MB)
  Used Dev Size : 48064 (46.95 MiB 49.22 MB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Nov 11 22:30:58 2009
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : cc1da503:27320695:b6f1b3ee:a6610b0d (local to host gracix)
         Events : 0.348

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1     252        1        1      active sync   /dev/block/252:1
```

The device showing here should have been /dev/sda1 or /dev/sdb1, not dev/block/252:1

my mdadm.conf was a truncated version with just the arrays listed:

```
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=cc1da503:27320695:b6f1b3ee:a6610b0d
ARRAY /dev/md2 level=raid1 num-devices=2 UUID=18f5f177:de988c6a:b6f1b3ee:a6610b0d
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=f007ee54:43090971:b6f1b3ee:a6610b0d
ARRAY /dev/md3 level=raid1 num-devices=2 UUID=2ed21adb:b6925599:b6f1b3ee:a6610b0d
MAILADDR root
```

The above version works fine with 2.6.28.  I have now pasted the array lines into the original mdadm.conf and rebuilt the initramfs but I've not yet tried to reboot with this.

What seems most strange to me is that /dev/sda<n> is not even recognised in 2.6.31

---

### Post by finni on 2009-11-12
What does "mdadm --auto-detect" do? It should automagically detect raid arrays.

---

### Post by scintilla on 2009-11-12
Okay .. more pieces of the jigsaw ...  Rebooted into 2.6.31 with full mdadm.conf - same result - degraded arrays, not running on /dev/sda<n> & /dev/sdb<n> but running on 1 instance of /dev/block/252:<n> which turns out to be mapped to /dev/mapper/nvidia-something.

Tried mdadm --auto-detect which says it couldn't claim all the devices /dev/sda1 etc used in the arrays. 

md: could not bd_claim sda1.
ditto for all 8 devices

mdadm.conf is 
```
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
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=cc1da503:27320695:b6f1b3ee:a6610b0d
ARRAY /dev/md2 level=raid1 num-devices=2 UUID=18f5f177:de988c6a:b6f1b3ee:a6610b0d
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=f007ee54:43090971:b6f1b3ee:a6610b0d
ARRAY /dev/md3 level=raid1 num-devices=2 UUID=2ed21adb:b6925599:b6f1b3ee:a6610b0d

# This file was auto-generated on Sun, 22 Feb 2009 13:47:27 +0000
# by mkconf $Id$
```

same output from mdadm --detail /dev/md0 as above .. degraded array on dev/block/252:1

If I do ls /dev/block:252* I get the following
```
lrwxrwxrwx 1 root root 25 2009-11-12 20:10 /dev/block/252:0 -> ../mapper/nvidia_hbccgjgc
lrwxrwxrwx 1 root root 26 2009-11-12 20:10 /dev/block/252:1 -> ../mapper/nvidia_hbccgjgc1
lrwxrwxrwx 1 root root 17 2009-11-12 20:10 /dev/block/252:10 -> ../mapper/vg1-usr
lrwxrwxrwx 1 root root 21 2009-11-12 20:10 /dev/block/252:11 -> ../mapper/vg1-backups
lrwxrwxrwx 1 root root 20 2009-11-12 20:10 /dev/block/252:12 -> ../mapper/vg1-videos
lrwxrwxrwx 1 root root 26 2009-11-12 20:10 /dev/block/252:2 -> ../mapper/nvidia_hbccgjgc5
lrwxrwxrwx 1 root root 26 2009-11-12 20:10 /dev/block/252:3 -> ../mapper/nvidia_hbccgjgc6
lrwxrwxrwx 1 root root 26 2009-11-12 20:10 /dev/block/252:4 -> ../mapper/nvidia_hbccgjgc7
lrwxrwxrwx 1 root root 26 2009-11-12 20:10 /dev/block/252:5 -> ../mapper/nvidia_hbccgjgc8
lrwxrwxrwx 1 root root 19 2009-11-12 20:10 /dev/block/252:6 -> ../mapper/vg1-homes
lrwxrwxrwx 1 root root 19 2009-11-12 20:10 /dev/block/252:7 -> ../mapper/vg1-winxp
lrwxrwxrwx 1 root root 19 2009-11-12 20:10 /dev/block/252:8 -> ../mapper/vg1-share
lrwxrwxrwx 1 root root 20 2009-11-12 20:10 /dev/block/252:9 -> ../mapper/vg1-share2
```

This time however all the raw /dev/sda<n> and /dev/sdb<n> devices are present, they are just not being used.

Maybe mdadm is picking up the raid arrays via the mapper, instead of directly through the sda<n> devices, and this is screwing up the arrays.  I'm going to try and restrict the devices scanned in mdadm.conf and see what happens...

---

### Post by scintilla on 2009-11-12
Re-booted again with 2.6.31 again (without repairing the arrays) and similar results
- even with restricted mdadm.conf (DEVICE /dev/sda* /dev/sdb*), it still picks up 1 device per array and mdadm --detail shows the device as /dev/block/252:<n>

- this time there are no numbered /dev/sda<n> or /dev/sdb<n> partitions listed.
ls /dev/sd* just shows /dev/sda and /dev/sdb

- so if the arrays are synchronised on boot, then it will find /dev/sda1,2,4,5,6,..., if they're not, it will not find any of them  ???

EDIT:
What's worse - when I re-boot back into 2.6.28 to try to repair the arrays, /dev/sda1 and /dev/sda5 are not there.  Gparted shows them as having invalid superblocks.  So the only way I've found to recover this is to re-format the partitions from Gparted, running from the live CD, and then they reappear and I can repair the array.   /dev/sda7 and /dev/sda8 are still shown as there, maybe because they are used for LVM2 volumes?  What a mess.

EDIT2:
Trying to understand the status of the array components:  mdadm --query gives the following

```
simon@gracix:~$ sudo mdadm --query /dev/sdb7
/dev/sdb7: is not an md array
/dev/sdb7: device 1 in 2 device active raid1 /dev/md1.  Use mdadm --examine for more detail.
simon@gracix:~$ sudo mdadm --query /dev/sda7
/dev/sda7: is not an md array
/dev/sda7: device 1 in 2 device mismatch raid1 /dev/md1.  Use mdadm --examine for more detail.
```

mdadm --examine seems to show that both devices are clean and identical - so why can't they both be in the array?

```
simon@gracix:~$ sudo mdadm --examine /dev/sda7
/dev/sda7:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : f007ee54:43090971:b6f1b3ee:a6610b0d (local to host gracix)
  Creation Time : Sun Feb 22 14:10:12 2009
     Raid Level : raid1
  Used Dev Size : 244139648 (232.83 GiB 250.00 GB)
     Array Size : 244139648 (232.83 GiB 250.00 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 1

    Update Time : Thu Nov 12 20:47:13 2009
          State : clean
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0
       Checksum : dcba47ce - correct
         Events : 5120


      Number   Major   Minor   RaidDevice State
this     1     252        4        1      active sync   /dev/vg1/usr

   0     0       0        0        0      removed
   1     1     252        4        1      active sync   /dev/vg1/usr
simon@gracix:~$ sudo mdadm --examine /dev/sdb7
/dev/sdb7:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : f007ee54:43090971:b6f1b3ee:a6610b0d (local to host gracix)
  Creation Time : Sun Feb 22 14:10:12 2009
     Raid Level : raid1
  Used Dev Size : 244139648 (232.83 GiB 250.00 GB)
     Array Size : 244139648 (232.83 GiB 250.00 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 1

    Update Time : Thu Nov 12 20:54:06 2009
          State : clean
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0
       Checksum : dcba48a5 - correct
         Events : 5246


      Number   Major   Minor   RaidDevice State
this     1       8       23        1      active sync   /dev/sdb7

   0     0       0        0        0      removed
   1     1       8       23        1      active sync   /dev/sdb7
```


Any ideas?

---

### Post by scintilla on 2009-11-13
Solved!   
The problem even happened when booting the live CD (9.10 amd64).
My disk partitions sda1,2,5,6,7,8 and sdb1,2,5,6,7,8 were not recognised, only sda and sdb

However when I booted with boot option nodmraid - all the partitions were recognised.
I added this to the boot options of my 9.10 kernel in /boot/grub/menu.lst - and it's now working....  hope this helps someone else...:D

---

### Post by santhony on 2009-11-17
I just found and fixed my problems after 3 days of scrubbing.....

My MDADM Raid 5 partitions, on two of the member disks, just mysterously disappeared.

I have a 7 disk Raid 5 Array.  After system updates and a reboot.  Two of my drives no longer had their partitions showing.  

GParted did show the two drives as intact, that they were members of a raid array.  

fdisk -l also showed the drives correctly with their partitions.

BUT, the disk Utility, Palimpseset showed the two drives with no partition table.

The FIXX:  REMOVE DMRAID.

After unistalling DMRAID using the Synaptic Package Manager... The drives all of a sudden showed up correctly and assembled all on their own..

Wall Lah..  

I hope this helps anyone with the same situation.

Good Luck and please post any tricks or tips you find!!

---

### Post by whiskybar on 2009-12-07
It sure helped! Thank you so much. I have been having this problem since 9.04. I could not find a solution until now. You can as well

```
apt-get autoremove dmraid
``` 

to get rid of the offender completely -- your solution in a disguise.

---

### Post by fiaschetta on 2010-01-25
It helped me too! 
Thank you very much. 

I have been having this problem since 9.04 too, and it was driving me crazy. 

I can confirm that after simply uninstalling dmraid the problem has disappeared.

Thank again.

---

### Post by mDuo13 on 2010-04-06
THANK YOU!

I had the same problem when upgrading my Linux Mint from 7 (Gloria) to 8 (Helena). My RAID1 refused to mount both disks, etc.etc. A simple uninstall of dmraid followed by a reboot... and BAM, my array is back where it belongs.

I'm just sad that it took me so long to find this thread, after searching for so many other threads about mdadm and md0's not rebuilding, etc.

What a relief that the solution was so fast and easy!

---

### Post by leespa on 2011-05-17
AWESOME!

Did a quick upgrade 9.04 --> 9.10 nothing worked.

Removed dmraid and all is well.

Thanks all! ;-)

---

