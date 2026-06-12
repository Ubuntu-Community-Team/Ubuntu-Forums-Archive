---
title: "Strange drive problems - new install, new box"
date: 2009-02-15
forum: Installation &amp; Upgrades
---

### Post by LoungeLizard on 2009-02-15
I recently built a new machine with a 500Gb PATA HD primary, IDE DVD R/W on a Mobo having a nVidia SATA RAID controller using AMD64x2 processor and 4Gb RAM.  I added 4 320Gb SATA drives and configed in BIOS as RAID5 giving me a little over 900Gb storage space.  I installed Intrepid 64-bit partitioning the primary drive to have 5 Gb SWAP and all the rest as root.  Then, I had to apt-get install gParted and dm-raid - my install didn't automagically recognize the RAID as a single drive and manually configure these drives - so I was left to my wits and my friend google to figure it out how to do the 'fakeRAID' thaing.  After I got dmraid to map the drives and gParted to create one giant partition I called "data" and mounted it in the root tree as /data, I setup SAMBA and created a share for the raid folder.  Then, I upgraded everything to the latest and greatest with synaptic and within a total time of about 6 hours, I had my jammin' fileserver with a future database ready to rock.  I was happy, all seemed fine and dandy. ...this was yesterday...

Late last night, I started a file transfer job from a winders box that has an old maxtor drive that's down to 19% according to the health monitor (it has developed a number of bad sectors and really needs to be decommisioned, failure is imminent).  I got up this morning, the task had crapped out at some point on the winders side complaining of a CRC issue and I started it up again.  It went on a few more hours and then the Interpid machine froze and locked up - no keyboard or mouse movement possible, gKrellm monitor frozen.  WTF...  I waited a short time (~20 minutes or so) and cut power after no change and response to any keyboard attempt.

restored power, and rebooted to find my primary drive missing in the POST.  Went into BIOS, looked around, drive wasn't showing up... then exited, and magically the drive appeared at the subsequent POST.  This is not a good sign, all the hardware is brand-spanking new.  I went to continue reboot, it found GRUB and entered stage 1.5 - but choked and got the dreaded "no init found" and dropped into the BusyBox shell.  I reloaded, thinking that my primary drive's UUID got corrupt somehow, intercepted GRUB and forced a plain no UUID boot, and was able to successfully boot.  But, I noticed (I removed quiet and splash - so I can see what's happening) that a lot of error messages concerning the RAID drives during the boot process.  Going into syslog I found some of this```
[   21.827569]  ata1.00:  cmd 25/00:a8:5f:13:c0/00:00:00:1c:00:00/e0 tag 0 dma 86016 in
[   21.827570]            res 51/40:00:eb:13:c0/40:00:00:1c:00:00/e0 Emask 0x9 (media error)
[   21.827640]  ata1.00:  status:  { DRDY ERR }
[   21.827675]  ata1.00:  error:  { UNC }
[   24.284803]  ata1.00:  exception Emask 0x0 Sact 0x0 Serr 0x0 action 0x0
[   24.284838]  ata1.00:  BDMA stat 0x65
[   24.284874]  ata1.00:  cmd 25/00:a8:5f:13:c0/00:00:00:1c:00:00/e0 tag 0 dma 86016 in
[   24.284875]            res 51/40:00:eb:13:c0/40:00:00:1c:00:00/e0 Emask 0x9 (media error)
[   24.284945]  ata1.00:  status:  { DRDY ERR }
[   24.284979]  ata1.00:  error:  { UNC }
[   24.419032]  end-request:  I/O error, dev sda, sector 482350059
[   24.419264]  JDB: Failed to read block at offset 32336
[   24.419299]  JDB: I/O error -5 recovering block 32336 in log
[   24.419335]  JDB: Failed to read block at offset 32337
[   24.419369]  JDB: I/O error -5 recovering block 32337 in log
[   24.419405]  JDB: Failed to read block at offset 32338
[   24.419439]  JDB: I/O error -5 recovering block 32338 in log
[   24.419475]  JDB: Failed to read block at offset 32339
[   24.419509]  JDB: I/O error -5 recovering block 32339 in log
[   62.048847]  EXT3-fs: error loading journal
```
While digging through the logs, I got another freeze of the system.  and I did another waiting of 20 minutes or so, periodically checking if it released itself... Rebooted the neaderthal method and got a forced fsck```
/dev/sda1 contains a file system with errors, check forced.
/dev/sda1:
Inode 18326805 has illegal block(s).

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
          (i.e., without –a or –p options)
Fsck died with exit status 4
                                                                                 [fail]
   * An automatic file system check (fsck) of the root filesystem failed.
A manual fsck must be performed, then the system reSTARTED.
The fsck should be performed in maintenance mode with the 
Root filesystem mounted in read-only mode.
   * The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started.
After performing system maintenance, press CONTROL-D 
to terminate the maintenance shell and restart the system.
Give root password for maintenance
(or type Control-D to continue):
```I went through the complete manual fsck, it found a TON of issues, repaired all of them.  Now, we're back...

Got a clean reboot, things appear to work; but there's a problem.  Opening the system monitor, I only see a single drive there.  Opening up gParted, I can see the nVidia RAID and the huge partition - BUT, now it's showing that about 80% of the space is occupied???  So, all the files I've been porting from the other machine are visible and accesible, but I'm suspecting they aren't getting placed where they need to be and that the RAID array is NOT working correctly.  I need some assistance...

Where did I go wrong?  Do I need to try and remove the files I've moved from that other drive (gosh, I'm gonna have to go and buy another HD... just so I can get this data off of here)?  Do I need to start all over?

da Lizard

---

### Post by LoungeLizard on 2009-02-16
I am suspecting the problem is my haste in the installation and config of the array. I found this: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) which gives a really good explanation as to what's going on with the kind of RAID I got (and I'm somewhat dismayed by it all and will rather change the way I'm doing this, methinks). I know how I went about the install and run of the dmRAID and gParted utils - I was following a consensus of about 5 suggestions in other forums in similar situations. I never did edit anything in the startup stuff and I betcha (a Palin-ism) therein lies the issue at what I see in the syslog - the errors I'm interpreting is the kernal seeing 4 drives and not knowing that dmraid has them mapped as a single drive.

One purpose of my new machine is as a file server and I have an immediate need to remove data from a failing drive. So, I'm going to have to perforn another intermediary set of tasks after purchasing another hard drive - moving the existing data from the new file server onto there so I can rebuild the file server correctly. I don't think I want to risk loss of the files trying to do an in-place fix of a botched setup of my system. I know I can access the files currently placed on the file server and I think I'll only risk moving them again to a different drive (there are thousands of files - a few hundred Gigs - and it will take quite a few hours transferring them).

What I was hoping to get from here was assistance in where I went wrong and perhaps a second set of eyes to peruse my log records to determine if my interpretation is correct. And, I was hoping for assistance determining how I should go about fixing or re-engineering my drives so I can maximize their capacity for my purposes. As I mentioned, I have a single 500Gb PATA drive and 4 - 320Gb SATA drives that I bought over a year ago - none have ever been used.

Just for grins, so I can see what's up, I just ran ```
sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8671c7a5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60051   482359626   83  Linux
/dev/sda2           60052       60801     6024375    5  Extended
/dev/sda5           60052       60801     6024343+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b9b5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      116739   937705986   83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/sde: 320.0 GB, 320072933376 bytes
251 heads, 63 sectors/track, 39533 cylinders
Units = cylinders of 15813 * 512 = 8096256 bytes
Disk identifier: 0x000b9b5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      118600   937705474   83  Linux
/dev/sde3               1           1         512    0  Empty
Partition 3 does not end on cylinder boundary.
```OMG... no wonder I'm having such issues!!! How in hell did things get so crapped out??? It appears as if 2 of the drives in the RAID aren't even properly set up. Yeah... I need some help in resolving this. Any suggestions on the steps I'll need to take?

- da Lizard

---

### Post by LoungeLizard on 2009-02-16
Here's some more information...

I have another machine in which I created a RAID long time ago using the mdadm facility. This was configured into a pseudo (another sudo - nyuk, nyuk) RAID 5; actually more of a RAID 0+1. To see what that looks like with fdisk, I remoted over to that machine which has 4 - 300Gb hdds:```
Disk /dev/hde: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/hde doesn't contain a valid partition table

Disk /dev/hdf: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/hdf doesn't contain a valid partition table

Disk /dev/hdg: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/hdg doesn't contain a valid partition table

Disk /dev/hdh: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/hdh doesn't contain a valid partition table

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2330    18715693+  83  Linux
/dev/hda2            2331        2434      835380    5  Extended
/dev/hda5            2331        2434      835348+  82  Linux swap / Solaris

Disk /dev/md0: 600.1 GB, 600181309440 bytes
2 heads, 4 sectors/track, 146528640 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md1: 600.1 GB, 600181309440 bytes
2 heads, 4 sectors/track, 146528640 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md2: 600.1 GB, 600181243904 bytes
2 heads, 4 sectors/track, 146528624 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md2 doesn't contain a valid partition table
```So, my initial shock of seeing all those invalid partition tables is not as shocking as I thought it to be. Nevertheless, if you note above, none of the devices involved in the md software RAID are seen by fdisk as having a partition. Yet, on that machine, /dev/md2 is a valid drive mounted as "/data" having a total capacity of 550Gb.

Yet, on my new fileserver, when I perform```
> sudo dmraid -ay
RAID set "nvidia_aafjfffa" already active
RAID set "nvidia_aafjfffa1" already active

> sudo fdisk /dev/mapper/nvidia_aafjfffa

The number of cylinders for this disk is set to 116379.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
    (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/mapper/nvidia_aafjfffa: 960.2 GB, 960218726400 bytes
255 heads, 63 sectors/track, 116739 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b9b5d

                       Device Boot  Start    End      Blocks   Id   System
/dev/mapper/nvidia_aafjfffa1            1  116739  937705986   83  Linux
```So this tells me that at least the RAID5 array is there and has a filesystem. In the GUI system monitor, though, it does not show up as a separate drive like the **md-RAID** does on my other machine.

da Lizard --> needs some sleep now...

---

