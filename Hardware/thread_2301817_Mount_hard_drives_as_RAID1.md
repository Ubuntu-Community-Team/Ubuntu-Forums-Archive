---
title: "Mount hard drives as RAID1"
date: 2015-11-05
forum: Hardware
---

### Post by asb3 on 2015-11-05
I recently lost a lot of data and code due to a hard drive failure.  To avoid future data loss, I bought 2 2TB hard drives that I want to mount as a RAID1 system.  The drives haven't yet been formatted, and in gparted they are displayed as /dev/sdc and /dev/sdd.
I have mdadm installed on my system.  What do I have to do to setup and mount my new hard drives as a RAID1?  All the documentation I've found on the net seems to involve adding an additional drive to supply RADI1 redundancy to a drive that contains a /boot partitian, which is not what I want to do.

---

### Post by weatherman2 on 2015-11-05
I haven't set up a RAID in Ubuntu in a while, but I'll chime in a little.  If you mean that you already have the OS installed on another drive(?) and that these two new drives are for data only, then you should be able to create new partitions on each drive (choose "Do not format" or "unformatted").  Then create an array with mdadm - probably the partitions to add will be /dev/sdc1 and /dev/sdd1 .

Then, format the new array as, for example, ext4.

Finally, you'll have to add it to your /etc/fstab file to mount the array at startup.

FYI, RAID mirrors are great to protect against hard drive failure, but RAID doesn't protect against accidental erasure, file system corruption, or (if your data is ever say exposed on a network to a Windows machine) destruction of data by malware.  You still need a good backup solution in addition to RAID to protect your data.  This is why I don't bother with RAID anymore - I simply use rsync occasionally to backup my data to a different device.  But my important data doesn't change that often.  If I did have a server where the data was constantly changing faster than I could make reasonable backups, then I would setup a RAID.

S.M.A.R.T. is also another great tool to monitor the status of your hard drives.  I use GSmartControl and smartmontools in Ubuntu to check up on my hard drives.

---

### Post by SeijiSensei on 2015-11-05
1) Create a single partition that spans each drive and mark it as Linux RAID, type "fd".  I use fdisk for this, but parted or gparted should work as well.  When you're finished each drive should have a partition named /dev/sdc1 and /dev/sdd1.

2) Build the array with
```
sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdc1 /dev/sdd1
```

3) Format the array with 
```
sudo mkfs -t ext4 /dev/md0
```

Then mount the array wherever you want.  In /etc/fstab you can have an entry like
```
/dev/md0     /data     ext4     defaults     0 0
```
which will mount the array at boot as /data.

The mdadm program has pretty extensive help.  Use "mdadm --help" to begin.

Remember the "golden rule," RAID is not a substitute for backups.

---

### Post by asb3 on 2015-11-07
I'm not sure how to do step 1.  I'm using gparted to partition the drive. 
The Dialog box comes up with the following defaults:
Free space preceding (miB): 1
New size(Mib):                   1907728
Free space following:           0
Align to:                            MiB  (other choices are "cylinder" and "none")
Create as:                         Primary partition (other choice is "Extended partition")
File system:                      ext4  (Many other choices)
Label:                              

What settings should I use?

---

### Post by SeijiSensei on 2015-11-07
Try using fdisk instead.  Start with "sudo fdisk /dev/sdc".  All the commands are single letters.  Use "p" to list the current partitions, if any, then "d" as many times as necessary to delete what's there.  Next use "n" (new), "p" (primary), "1" to choose the starting cylinder, then hit enter to incorporate the entire device.  Finally, type "t" to enter the partition's type and "fd" when prompted to choose Linux RAID.  Use "p" again to make sure you have done things correctly, then "w" to write the partition table to the disk.  Follow the identical procedure on /dev/sdd.  You can type "m" at the prompt in fdisk to see a list of available commands.

---

### Post by weatherman2 on 2015-11-07
> **asb3 said:**
> I'm not sure how to do step 1.  I'm using gparted to partition the drive. 
The Dialog box comes up with the following defaults:
Free space preceding (miB): 1
New size(Mib):                   1907728
Free space following:           0
Align to:                            MiB  (other choices are "cylinder" and "none")
Create as:                         Primary partition (other choice is "Extended partition")
File system:                      ext4  (Many other choices)
Label:                              

What settings should I use?

Again - don't use ext4 or format in Gparted - choose "unformatted" or "do not format."  You'll format / create the file system later after you've built the array.

There are two different types of partition tables on a modern consumer hard drive.  For a 2TB drive, you can use the old MSDOS-style partition table or the newer GPT.  If you use MSDOS (the default still in Gparted?) you are limited to four primary partitions on a single drive...or three primary partitions and one "extended" which is a way to add more than four.  You create logical partitions inside the extended partition, which is kind of a fake "container" partition for logical partitions.  It's a hack added decades ago to allow for more than four partitions.

If you will ONLY ever have four or fewer partitions on a drive, you can feel safe using a primary partition.  Someday if you have four primaries and want to add a fifth partition, you're stuck unless you've made one of them an extended + logicals inside.

Or...use the newer GPT-style partition table (required for drives larger than about 2TB) and you can make as many primary partitions as you want.  GPT is probably more robust anyway but may have issues only on very old computers.

Leave the other Gparted options as defaults if you aren't sure.

---

### Post by asb3 on 2015-11-07
I tried fdisk, and got the following warning:

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.

Now what?

---

### Post by weatherman2 on 2015-11-07
Use Gparted, which does support gpt.

---

### Post by asb3 on 2015-11-09
I successfully set up the RAID. Thank you all for your help.

---

