---
title: "Making things worse  - serious problems with MBR"
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by rbrauns on 2009-03-11
I've been using Ununtu Intrepid for about a week but it was too unstable so I decided to install Hardy.  Due to my system constantly getting kernel panics, I decided to install Windows XP and let it run for a couple of days.  No system hangs so I know my hardware is OK.

Hardware is old. Abit IC7 with 3.4 GHz P4, 2 GB Ram and 3 HD. One on the SATA and 2 older ones with data on the IDE controller.

Intrepid was installed on the SATA drive, which was J: under Windows, dev/sdc1.  After installing XP, the SATA drive changed to E: and I couldn't boot into Ubuntu anymore.  XP also killed the logical partition on the second IDE drive.  NTFSFIX cured that and all was normal.

Under XP, that same drive was hidden so I used TESTDISK to change the filesystem to DATA from unknown.  BIG MISTAKE!

Then I booted to Ubuntu and could see the drives but can't mount them anymore.  Here is what fdisk -l reveals:

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2b952b94

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30402   244198583+  ee  EFI GPT

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2628e650

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1945    15623181    7  HPFS/NTFS
/dev/sdb2            1946       19453   140633010    f  W95 Ext'd (LBA)
/dev/sdb5            1946       19452   140624946    7  HPFS/NTFS

Disk /dev/sdc: 33.8 GB, 33820284928 bytes
255 heads, 63 sectors/track, 4111 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x444c544e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        4110    33013543+   7  HPFS/NTFS

Disk /dev/sdd: 131 MB, 131072000 bytes
1 heads, 32 sectors/track, 8000 cylinders
Units = cylinders of 32 * 512 = 16384 bytes
Disk identifier: 0xc39afbca

I can't boot at all now unless I use the Live CD option so before I muck up my system more, can someone tell me how to get my MBR back?

Thanks for your help.

---

### Post by martrn on 2009-03-11
The master-boot record just contains a boot-loader, to either load ubuntu or chain-load windows.  Ubuntu boot-loader is grub.

See [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") for installing grub to a master boot record on any drive.

At a terminal type:

> sudo lshw -C disk

to find out what order your hard-disks are installed as and then see the above URL (RecoveringUbuntu...) section 1 to 4 for re-installing grub to a master boot record.

Change 'setup (hd0)' to 'setup (hd1)' or 'setup (hd2)' depending on which master-boot record you wish to install grub to, and dependent on the hard drive shown from the results of 'sudo lshw -C disk'.  Change the bios setting to boot from a different hard-drive.  Eg if you need to boot hd1 change this in the BIOS.

*** EDIT *** :
Try to avoid editing / changing of partition tables, unless there is absolute any need or you are installing a new drive or changing the partitions of a drive eg. moving/adding/resising partitions and then use boot from an external cd using a tool such as [http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/") (or simular), otherwise your os (kernel) will write to the new partitions and will have problems.

---

### Post by rbrauns on 2009-03-12
@martrn,

Thank you for taking the time to help me.  The output of the lswh command was:

ubuntu@ubuntu:~$ sudo lshw -C disk
  *-disk:0                
       description: ATA Disk
       product: SAMSUNG SP2514N
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: VF10
       serial: S08BJ1SY905919
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-disk:1
       description: ATA Disk
       product: WDC WD1600JB-00F
       vendor: Western Digital
       physical id: 1
       bus info: scsi@2:0.1.0
       logical name: /dev/sdb
       version: 15.0
       serial: WD-WMAES1382719
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=2628e650

It is /dev/sda that can't be read.  I also booted my Knoppix CD and ran gpart on that drive.  It found 4 paritions all full of zeros (no start or end sector, 0 bytes, etc).  BUT there Were 4 paritions on that drive.  There was the boot partition and 2 partitions and a small 15 GB bit at the end.

I will try the link you sent.

---

### Post by martrn on 2009-03-12
> **rbrauns said:**
> @martrn,

Thank you for taking the time to help me.  The output of the lswh command was:

It is /dev/sda that can't be read.  I also booted my Knoppix CD and ran gpart on that drive.  It found 4 paritions all full of zeros (no start or end sector, 0 bytes, etc).  BUT there Were 4 paritions on that drive.  There was the boot partition and 2 partitions and a small 15 GB bit at the end.

I will try the link you sent.

Your logical disk 0 looks like its partition tables have been either altered or messed so that nothing can read the partition tables.  Effectively makeing disk 0 look like it is an un-partitioned disk.  Your logical disk 1 looks like it has three working bootable partitions NTFS, FAT32, and NTFS again.  I presume these all work OK.

I am guessing TESTDISK has edited your partition tables on disk 0.  Maybe it is possiable re-running TESTDISK can get your partitions on that disk back - do NOT edit your partition table of your logical disk 1, as it looks good.

I do not know how much data you had on logical disk 0.

If you had lots of data on it look for some disk recovery software or some way of re-storing your partition table if TESTDISK saves and restores your partition tables ?  (Errgh.)

If you had one weeks worth of data on the logical disk 0, re-install ubuntu hardy, and use the alternative cd to install or use gparted to partition your data before hand so you are aware of your partitions that you have.  You may have lost a weeks worth of data but put it down to gain knowledge about partitions and master-boot records.  Don't edit hard drive partition tables unless you have a backup copy of whats on your drive or it might be gone, if you enter incorrect values into it.

Don't give up on ubuntu, as it really is a brilliant GNU/Linux distribution.

---

