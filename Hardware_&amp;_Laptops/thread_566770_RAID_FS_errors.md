---
title: "RAID FS errors"
date: 2007-10-03
forum: Hardware &amp; Laptops
---

### Post by Ndyanabo on 2007-10-03
I set up a simple software mirroring RAID a couple of months ago. Worked fine for a while. Then I kept having problems with it -- when I'd boot up, I see that it was having trouble mounting. I'd constantly run fsck, just about every time I started up.

Finally, it stopped mounting. Now I'm not sure, but in any event  it just wasn't appearing on my desktop. However, when I got to its shortcut in Places, though Media, or in the command line, the directory opens up. However, many files that were on it no longer appear to be, including the Lost + Found.

I have no idea what I'm doing. Here's what I tried.

```
$ sudo mount -t ext3 /dev/md0 /media/mombasa
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

```
$ dmesg | tail 
[   83.604292] Bluetooth: L2CAP socket layer initialized
[   83.912269] Bluetooth: RFCOMM socket layer initialized
[   83.912289] Bluetooth: RFCOMM TTY layer initialized
[   83.912292] Bluetooth: RFCOMM ver 1.8
[10866.840731] usb 3-4.4: new full speed USB device using ehci_hcd and address 3
[10866.942800] usb 3-4.4: configuration #1 chosen from 1 choice
[11202.728842] ppdev0: registered pardevice
[11202.767916] ppdev0: unregistered pardevice
[12460.216589] usb 3-4.4: USB disconnect, address 3
[48277.040871] ext3: No journal on filesystem on md0
```

```
$ sudo fsck -t ext3 /dev/md0
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
/dev/md0 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Group 2's block bitmap (65536) is bad.  Relocate<y>? yes

Group 2's inode bitmap (65537) is bad.  Relocate<y>? yes

 Error allocating 1 contiguous block(s) in block group 2 for block bitmap: Could not allocate block in ext2 filesystem
Error allocating 1 contiguous block(s) in block group 2 for inode bitmap: Could not allocate block in ext2 filesystem
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/md0: ********** WARNING: Filesystem still has errors **********

/dev/md0: 34393/48840704 files (11.0% non-contiguous), 66845621/97677184 blocks

```

These are the two drives:

```
$ sudo lshw -C disk
Password:
  *-disk:0                
       description: SCSI Disk
       product: ST3400833NS
       vendor: ATA
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       version: 3.AE
       serial: 5NF25L4C
       size: 372GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume
          description: Linux filesystem partition
          physical id: 1
          bus info: scsi@2:0.0.0,1
          logical name: /dev/sdb1
          capacity: 372GB
          capabilities: primary
...

  *-disk:2
       description: SCSI Disk
       product: SAMSUNG HD403LJ
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/sdd
       version: CT10
       serial: S0NFJ1GP404026
       size: 372GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume
          description: Linux filesystem partition
          physical id: 1
          bus info: scsi@5:0.0.0,1
          logical name: /dev/sdd1
          capacity: 372GB
          capabilities: primary

```

any suggestions for how to get it working properly, and/or find my lost stuff?

---

### Post by Ndyanabo on 2007-10-03
please help me out, even if it's to tell me that my files are gone.

forgot to say that it doesn't seem to be mounted, even though I can access the array:

```
$ umount /media/mombasa
umount: /media/mombasa is not mounted (according to mtab)

```

fstab looks normal.

---

### Post by MrHippocampus on 2007-10-04
first check the output of the command below, that will tell you if the disks in the raid are up and running (You should have as many U's as there are disks in your raid).

> cat /proc/mdstat

To check your data you could try making two new raid nodes each created with only one disk from the existing raid (make sure you stop the existing one first), this way you can check each disk individually to see if one is ok and the other is causing problems.

Or you can try checking the raid for errors and repairing them by following this part of the gentoo wiki page on raid [here]("http://gentoo-wiki.com/HOWTO_Install_on_Software_RAID#Data_Scrubbing") (be sure to read about the caveat of doing this).

---

### Post by Ndyanabo on 2007-10-04
Thanks for the help.

Two 'U's.

How do I do this?

> To check your data you could try making two new raid nodes each created with only one disk from the existing raid (make sure you stop the existing one first), this way you can check each disk individually to see if one is ok and the other is causing problems.

---

### Post by MrHippocampus on 2007-10-04
Ive just remembered a program which may help, its called testdisk (in the repo's) and it can rebuild various filesystems after problems, I've never used it myself but ive heard good things about it. Google should yield some info on how to use it.

---

### Post by Ndyanabo on 2007-10-06
progress.

I noticed in gparted that the file system is listed as ext2. Very odd, because I had built it as ext3.

So, I did
```
$ sudo mount -t ext2 /dev/md0 /media/mombasa

```
It mounted, but there's only a lost+found folder, showing even less than what was there previously. Anyway, looking in the lost+found, I see that some, but not all, or my data is there, but the directories have been renamed with numbers. It appears that that's not a big deal, but should I try to recover it in some sort of sophisticated way, on the assumption that I could get a full recovery?

haven't been able to make sense of testdisk yet.

Does the following suggest anything about the disk problem?

```
$ sudo fdisk -ls
Password:

Disk /dev/sdd: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       48641   390708801   83  Linux

Disk /dev/md0: 400.0 GB, 400085745664 bytes
2 heads, 4 sectors/track, 97677184 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md0 doesn't contain a valid partition table

```

---

