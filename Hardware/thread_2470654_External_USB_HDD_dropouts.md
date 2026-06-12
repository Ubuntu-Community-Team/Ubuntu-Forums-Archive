---
title: "External USB HDD dropouts"
date: 2022-01-06
forum: Hardware
---

### Post by laggger164 on 2022-01-06
Running Ubuntu server 20.04

I am using external USB 3.0 HDD caddies with 2 slots on which 2 12TB Synology HDDs are mounted.
There is a problem with writing to and reading from these drives, but only sometimes as I was already able to write around a TB of data into them and sometimes they seem to work after a reboot.
I was thinking this was related to the Ryzen 5000 USB dropouts, but this still happens even after I updated to the newest BIOS and with C-states disabled and PCIE set to 3.0 everywhere (the recommended measures).

The data in these drives is not terribly important, so if a wipe is necessary so be it.

I was trying to figure out if the XFS filesystem was corrupted, and it might be, here is the output from xfs_repair:

sudo xfs_repair /dev/sdf
Phase 1 - find and verify superblock...
bad primary superblock - bad magic number !!!


attempting to find secondary superblock...
............................................................................................................................................................................................................................................................................................................................................................................................Sorry, could not find valid secondary superblock
Exiting now.


(there were a lot more dots though)

in dmesg | tail, this popped up

[  418.976996] XFS (sdf1): Unmounting Filesystem                // this is where I unmnounted the drive to repair it's filesystem
[  490.740386] sd 10:0:0:1: [sdf] tag#15 uas_eh_abort_handler 0 uas-tag 2 inflight: CMD IN           //and this is after a while of running xfs_repair
[  490.740389] sd 10:0:0:1: [sdf] tag#15 CDB: Read(16) 88 00 00 00 00 00 00 b9 94 00 00 00 04 00 00 00
[  490.772134] sd 10:0:0:1: [sdf] tag#14 uas_eh_abort_handler 0 uas-tag 1 inflight: CMD IN
[  490.772136] sd 10:0:0:1: [sdf] tag#14 CDB: Read(16) 88 00 00 00 00 00 00 b9 90 00 00 00 04 00 00 00
[  490.792383] scsi host10: uas_eh_device_reset_handler start
[  490.929574] usb 2-1: reset SuperSpeedPlus Gen 2 USB device number 2 using xhci_hcd

I checked again after trying to get data off another drive with the same symptoms and saw this:

[  556.150448] usb usb2-port1: attempt power cycle
[  556.633574] usb 2-1: new SuperSpeedPlus Gen 2 USB device number 6 using xhci_hcd
[  561.925893] usb 2-1: device descriptor read/8, error -110
[  562.030161] usb 2-1: new SuperSpeedPlus Gen 2 USB device number 6 using xhci_hcd
[  567.301908] usb 2-1: device descriptor read/8, error -110
[  567.613569] usb 2-1: new SuperSpeedPlus Gen 2 USB device number 7 using xhci_hcd
[  572.678083] usb 2-1: device descriptor read/8, error -110
[  572.782359] usb 2-1: new SuperSpeedPlus Gen 2 USB device number 7 using xhci_hcd
[  578.054084] usb 2-1: device descriptor read/8, error -110
[  578.166593] usb usb2-port1: unable to enumerate USB device



Sooo, any ideas? There were no dropouts on Windows I am sure of that.
Thank you for any and all help!

---

### Post by TheFu on 2022-01-07
The only times I've seen storage links fail was either with flaky USB drivers (from 10 yrs ago) or when a SAS connector was vibrated loose inside an array.  The fix for the 1st was to get a vendor provided firmware update and the fix for the 2nd was to change the SAS cables to 90deg connectors.  

Any dropouts should show up in system logs.

BTW, xfs isn't normally used with Ubuntu.  While it shouldn't matter, perhaps using ext4 or ZFS would be better?  Those file systems are well used on Ubuntu.

---

### Post by TheFu on 2022-01-07
BTW, did you really use the entire drive for a file system (/dev/sdf) - without any partition table?  That's NOT a best practice. ALWAYS use a partition table and put file systems on a partition or inside the volume managed objects - pools or logical volumes if you use LVM.

Or was the /dev/sdf just a typo and you meant to use /dev/sdf1 ... or /dev/sdf2, 3, 4, 5, 6, 7, 8, ...

---

### Post by laggger164 on 2022-01-07
I used XFS since the files I store are 100GB each, just made sense to pick that.
I might try ext4 though...
So this might be a driver issue then... great.
Maybe the new Ubuntu distro would fare better? How would I try that since there is no 22.04 yet?

---

### Post by laggger164 on 2022-01-07
> **TheFu said:**
> BTW, did you really use the entire drive for a file system (/dev/sdf) - without any partition table?  That's NOT a best practice. ALWAYS use a partition table and put file systems on a partition or inside the volume managed objects - pools or logical volumes if you use LVM.

Or was the /dev/sdf just a typo and you meant to use /dev/sdf1 ... or /dev/sdf2, 3, 4, 5, 6, 7, 8, ...

What? No, there is a GPT partition table on each one, then a partition on that set using parted from 0% to 100% with no name.
Although sdf1 didn't seem to work with xfs_repair command, using just sdf was what I was instructed to do.

---

### Post by TheFu on 2022-01-07
22.04 alpha is available for testing.
My opinion is that non-LTS isn't worth my time or the risk to my data.  6 real months of running an OS just isn't sufficient to touch, beyond play. Nothing serious would be on any non-LTS here, but perhaps my data is worth more to me than others?  To me, data is more important than any hardware too.  Computing is about the data, not the hardware.

---

### Post by TheFu on 2022-01-07
> **laggger164 said:**
> What? No, there is a GPT partition table on each one, then a partition on that set using parted from 0% to 100% with no name.
Although sdf1 didn't seem to work with xfs_repair command, that was what I was instructed to do.

If there is a partition table, the /dev/sdf is INCORRECT for any fsck.
Validate that with 
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```

---

### Post by laggger164 on 2022-01-07
[COLOR=#000000]```
[/COLOR]
(parted) select /dev/sdd1
Using /dev/sdd1
(parted) print
Model: Unknown (unknown)
Disk /dev/sdd1: 12.0TB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags:


Number  Start  End     Size    File system  Flags
 1      0.00B  12.0TB  12.0TB  xfs


(parted) select /dev/sdd
Using /dev/sdd
(parted) print
Model: Synology  HAT5300-12T (scsi)
Disk /dev/sdd: 12.0TB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  12.0TB  12.0TB  xfs
[COLOR=#000000]
```
[/COLOR]
This is from a different drive since that one is not responding, should show up after a reboot though.
And with the lsblk:
[COLOR=#000000]```
[/COLOR]
lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME          SIZE TYPE FSTYPE MOUNTPOINT
sda          10.9T disk
&#9492;&#9472;sda1       10.9T part xfs    /mnt/syn12tb6
sdb          10.9T disk
&#9492;&#9472;sdb1       10.9T part xfs    /mnt/syn12tb4
sdc          10.9T disk
&#9492;&#9472;sdc1       10.9T part xfs    /mnt/syn12tb7
sdd          10.9T disk
&#9492;&#9472;sdd1       10.9T part xfs    /mnt/syn12tb5
sdg         223.6G disk
&#9500;&#9472;sdg1        512M part vfat   /boot/efi
&#9500;&#9472;sdg2          8G part swap   [SWAP]
&#9492;&#9472;sdg3      215.1G part ext4   /
sdh          10.9T disk
&#9492;&#9472;sdh1       10.9T part xfs    /mnt/syn12tb10
sdi          10.9T disk
&#9492;&#9472;sdi1       10.9T part xfs    /mnt/syn12tb11
sdj          10.9T disk
&#9492;&#9472;sdj1       10.9T part xfs    /mnt/syn12tb2
sdk          10.9T disk
&#9492;&#9472;sdk1       10.9T part xfs    /mnt/syn12tb1
sdl          10.9T disk
&#9492;&#9472;sdl1       10.9T part xfs    /mnt/syn12tb3
nvme1n1       1.8T disk
&#9492;&#9472;nvme1n1p1   1.8T part xfs    /mnt/tmpssd1
nvme0n1       1.8T disk
&#9492;&#9472;nvme0n1p1   1.8T part xfs    /mnt/tmpssd2
[COLOR=#000000]
```[/COLOR]
Not sure what would be wrong here.

Also, some of the drives are on different USB caddies, I don't remember which but those are new, reminds me to check if those are the ones making trouble.
But all of them were having problems except the ones connected through SATA.

---

### Post by TheFu on 2022-01-07
Please edit the post above to use 'code tags' - too hard to read when the columns aren't lined up.
How to: [Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code)

---

### Post by laggger164 on 2022-01-07
Right, sorry about that.

---

### Post by TheFu on 2022-01-07
Well, looked like sdf doesn't exist.  Bad cable or did the device name change?  Just because something is new, that doesn't mean it is good.  Cheap cables often are shipped with other equipment. That's common for everything - ethernet, coax, sata, sas ... USB.

Best to use LABEL or UUID to mount those anyways in the /etc/fstab.
Check the connections too.

These are all externally powered, right?  Avoid using only USB powered devices whenever possible.

---

### Post by laggger164 on 2022-01-08
Indeed they are all externally powered.
All drives are mounted using UUIDs in /etc/fstab, but once a drive drops out, it doesn't go back, even mount -a doesn't see it, says its not connected.
I guess I will have to find out if the caddies are working properly. It still could be a driver issue since there are 2 different units by different manufacturers, one of them might be the culprit...

---

### Post by TheFu on 2022-01-08
> **laggger164 said:**
> Indeed they are all externally powered.
All drives are mounted using UUIDs in /etc/fstab, but once a drive drops out, it doesn't go back, even mount -a doesn't see it, says its not connected.
I guess I will have to find out if the caddies are working properly. It still could be a driver issue since there are 2 different units by different manufacturers, one of them might be the culprit...

I've learned over the decades ... avoid USB for anything important.  Go with SATA, eSATA, Infiniband for stuff that matters.  The USB command set for storage is very lacking. Those other methods provide good connections an more commands which can help diagnose issues.

Did you look at the SMART data for the disks?  Some USB controllers don't support SMART, so you might need to use a different connection method to test then get the reports from each drive involved.

---

### Post by laggger164 on 2022-01-08
Didn't really think of that, I will check for SMART data.
But yeah, I will probably buy a proper RAID card and box.

---

### Post by TheFu on 2022-01-08
> **laggger164 said:**
> Didn't really think of that, I will check for SMART data.
But yeah, I will probably buy a proper RAID card and box.

With Linux, you don't want hardware RAID.  Use SoftwareRAID or better, use ZFS.  Then you'll want a quality LSI JBOD adapter (HP, Dell rebrand some).  If you need expansion, get a SAS JBOD HBA - each SAS connection supports 4 SATA connections.  Expect to spend $100-$300. 
Don't get HW-RAID.  You probably won't be able to use it and unless it has onboard battery backup, what's the point?  ZFS addresses all but the battery backup for why we like RAID.  Use an SSD for a cache device for ZFS and it will be crazy fast.

As for exact models of LSI JBOD SAS controllers, check the BSD NAS support forums for what is currently recommended.  Watch out of cheap JBOD controllers. They tend to have terrible performance, which is fine for after home users running Windows with HDDs.  I have a Maxell crap JBOD controller. Got it for eSATA support - it is only SATA-I, which is more than fast enough for the purpose - spinning disks won't come close to SATA-I bandwidth.

Good luck.

---

