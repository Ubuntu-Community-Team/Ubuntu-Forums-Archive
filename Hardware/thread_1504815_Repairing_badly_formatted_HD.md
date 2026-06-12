---
title: "Repairing badly formatted HD"
date: 2010-06-08
forum: Hardware
---

### Post by Daimonan on 2010-06-08
Hi everyone,

A friend of mine recently gave me their external USB HD, which no longer mounts properly on their Mac.  It sounds like they plugged the HD into a Windows box and attempted to partition the drive, and weren't successful.  From what they say, they then just attempted to format the drive.  All of this information has to be taken with a grain of salt - they aren't really a 'computer person'.

I'm trying to recover whatever I can using my linux box (Linux Mint Isadora).  When I plug it in, the HD doesn't auto-mount on my computer either.  After doing some reading, I tried to manually mount it; here's the results:

fdisk -l gave the following for the drive in question:

Disk /dev/sdb: 750.2 GB, 750156373504 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91202   732574521   af  HFS / HFS+
Note: sector size is 2048 (not 512)

when I tried to mount, I got the following error:

sudo mount -t hfs /dev/sdb1 /media/external
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Further reading advised me to check (as the above error says) dmesg or tail.  These didn't show any obvious problems.  Here's the dmesg after I plugged in the drive:


[ 2355.710068] usb 1-3: new high speed USB device using ehci_hcd and address 7
[ 2355.861684] usb 1-3: configuration #1 chosen from 1 choice
[ 2355.867336] scsi6 : SCSI emulation for USB Mass Storage devices
[ 2355.887260] usb-storage: device found at 7
[ 2355.887266] usb-storage: waiting for device to settle before scanning
[ 2360.880361] usb-storage: device scan complete
[ 2360.880871] scsi 6:0:0:0: Direct-Access     STECH    Simple Drive     8.59 PQ: 0 ANSI: 0
[ 2360.884866] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 2360.888483] sd 6:0:0:0: [sdb] 1465149167 512-byte logical blocks: (750 GB/698 GiB)
[ 2360.896322] sd 6:0:0:0: [sdb] Write Protect is off
[ 2360.896334] sd 6:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 2360.896339] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2360.901236] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2360.901249]  sdb: sdb1
[ 2360.919706] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2360.919720] sd 6:0:0:0: [sdb] Attached SCSI disk

I don't see any obvious errors here.  In short, I'm confused, and don't really know where to start.  If a full format was completed on the windows machine, wouldn't fdisk -l display an ntfs file system?  Or potentially two partitions?  This leads me to think the 'format' on the windows box didn't go through.  Could this be a bad boot sector issue?

How would you tackle an issue like this?

Thanks!

---

### Post by srs5694 on 2010-06-08
Try either omitting the type specification ("-t hfs") or changing it to hfsplus ("-t hfsplus") in the mount command. I make no promises that this will help, but it might.

If you're trying to recover specific files, you might try [PhotoRec,](http://www.cgsecurity.org/wiki/PhotoRec) which can recover files from filesystems that are so badly damaged that they won't mount. I can also make no promises that this will work, but it's certainly worth trying.

If you just want to use the disk in Linux without recovering any files, you can use mkfs on the partition and change its type in Linux fdisk. Given the 2048-byte sector size, it's possible that GNU Parted, GParted, and similar tools will flake out on the disk.

---

### Post by dabl on 2010-06-08
If you are attempting to do "data recovery", then you'll have to get the low-level tools for that.

If you just want to restore the hard drive to usable condition, I would go with the "dd" command, in a terminal.  First run ```
sudo fdisk -lu
```

and note the device number for your target hdd.  Be sure it's the right device!

Then:

```
dd if=/dev/zero of=/dev/sdx bs=512 count=1
```

where "x" is, of course, the letter designation for the hdd as shown by fdisk.

Then, when you run GParted, the first question will be the partition table type.  Choose "MS DOS" unless you know what you are doing with a different table type.  This will write the new partition table in the MBR.  Then you're ready to partition it and format the partitions.

---

### Post by Daimonan on 2010-06-08
I've been playing around with TestDisk, and I've come across some more info:

When I select the drive, 'Apple Partition Map', and 'Analyse', I get the following message:

Bad MAC partition, invalid block0 signature
read_part_mac: bad DPME signature

If I continue and run a quick search I'm shown a small and a large HFS partition.  Continuing and trying to 'Write' the large partition gives the following:

Function write_part_mac not implemented
Use pdisk to recreate the missing partition
using values displayed by TestDisk

My only option then is to abort.

I'm asuming pdisk is a utility available on the mac for rewriting partitions.  What is a suitable equivalent in Ubuntu?  From this information, do you have any idea exactly what's happening?

---

### Post by srs5694 on 2010-06-09
I hadn't considered the possibility that the disk used the Apple Partition Map (APM) partitioning scheme, probably because your fdisk output shows a valid MBR partition in place. Background: MBR is used on most x86 and x86-64 computers, APM was used on 680x0- and PowerPC-based Macs, and a third system, the GUID Partition Table (GPT) is used on modern Intel-based Macs and some other systems.

What sort of Mac does your friend have? If it was a PowerPC system, then there's a good chance that the disk used APM originally, but the APM table has clearly been overwritten by an MBR (maybe in the attempt to fix it in Windows to which you referred). The fdisk output you posted didn't mention discovering any GPT data, which it would have if such data had been present, so chances are the disk either didn't use GPT or the GPT data have been completely obliterated. Both PowerPC- and Intel-based Macs can use both APM and MBR (and some can use GPT), so it's conceivable the disk used MBR originally.

If data on the disk are important, you should first do a complete low-level backup (as in "sudo dd if=/dev/sdb of=/dev/sdc" to back up /dev/sdb to another disk, /dev/sdc). You can then try using testdisk or other tools with reduced danger of making matters worse; if something goes wrong, you'll still have the backup.

Once you've got a backup made, you could try using testdisk again, but instead of telling it to use APM, tell it to use MBR. If the partitions on the disk are valid, it may be able to recover them as MBR partitions, even if they originated as APM partitions. Partitions are, after all, just contiguous blocks of sectors, and you can describe a partition in MBR terms as well as you can do so in APM terms. My thought is that testdisk may be flaking out on you because of the damaged/nonexistent APM data rather than because of damaged internal partition data, so telling it to use MBR may work around the problem. You might need to delete the existing partition in MBR by using fdisk first, though.

The pdisk utility, incidentally, is a cross-platform (including Linux) tool for editing APM partition tables. I don't see it in the APT repositories I've got configured for my Ubuntu 9.10 system, but check the [project's Web page](http://www.cfcl.com/eryk/linux/pdisk/index.html) or do a Google search to download source code or find a Debian binary package. I don't think using pdisk would be very helpful, though; as I said, testdisk should be able to recover the partitions in MBR form even if they were originally in APM form.

---

