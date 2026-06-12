---
title: "External hard drive - Unnable to mount"
date: 2012-02-05
forum: Hardware
---

### Post by Hamani on 2012-02-05
Hey guys, 

I've had Ubuntu on my laptop for a while but my windows PC crashed last night so I booted Ubuntu 11.10 on it and fixed most of the small issues. I can't get my external hard drive to mount though, and have no idea where to start ...

This is the error message I get: 

Error mounting: mount exited with exit code 12: Failed to read last sector (976771119): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sdd1': Invalid argument
The device '/dev/sdd1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

I'm not a complete novice with computers but I've very little experience with Ubuntu past basic use. Any help greatly appreciated. 

- Gary.

---

### Post by ajgreeny on 2012-02-05
Was the external disk attached to your windows machine when it crashed?  If it was, try attaching it again to a windows machine where it may mount as usual, then make sure you "Safely remove" the disk.

It is possible that the disk may still be flagged up as in use to Ubuntu, as it was not unmounted properly in windows, though I thought that the error message was more explicit if that was the problem.  However, if the disk was being written to at the point when the crash happened, it could have corrupted the filesystem.

---

### Post by Hamani on 2012-02-05
Hey there, 

Thanks for the quick reply. 

I tried that, the windows machine picked it up right away and had no trouble reading from it. My Ubuntu machine came up with the same error even after I followed your advice though :(

Any idea's? 

- Gary.

---

### Post by ajgreeny on 2012-02-05
Sorry. No idea what to suggest.

---

### Post by gamesmad on 2012-02-05
I think the disc has become corrupt in some way.

Copy the contents of the hard drive to the Windows PC, then format the drive and and load your data back onto it.  If there is any corruption then this will solve it.

---

### Post by Hamani on 2012-02-05
The windows machine is only a small, old laptop ... There's no way I can really back up the contents of the drive. I actually dumped all my stuff on there to back it up while I sorted this machine out :(

---

### Post by coffeecat on 2012-02-05
@Hamani, try running a filesystem check on the drive in Windows. The command line utility is chkdsk, but there is a GUI utility in Windows which does the same thing. Then make sure you unmount the drive cleanly from Windows by right-clicking on the little icon down near bottom right on the panel.

---

### Post by aasdfasdfg on 2012-02-05
Here is how I would begin to troubleshoot:

```
parted /dev/sdd
```

This begins a parted session. If all is well, at the (parted) prompt type
```
print
```
to get some basic information about the drive.

If you prefer a GUI, you can use gparted alternatively.

Some basic questions:

[LIST]
[*]Have you ever been able to mount this drive on Linux?
[*]Does Linux report an NTFS partition?
[*]Can you mount any other partitions on this drive / is there unallocated space on this drive?
[/LIST]

---

### Post by Hamani on 2012-02-06
Hi coffeecat, tried that but it bombed out after 'stage 5' saying unable to complete? 

@aasdfasdfg, This is what happened:

gary@Lanister:~$ sudo parted /dev/sdd
[sudo] password for gary: 
GNU Parted 2.3
Using /dev/sdd
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Error: Cannot have a partition outside the disk!  

For the questions:

1) I've never tried mounting it on Linux before, so no. 
2) How would I find that out? I would assume yes by the error it comes up with but can I double check somehow?
3) As far as I'm aware it's all partitioned off as one big block. 

Thanks for all the input guys,

- Gary.

** Update **

Just loaded up GParted and the disk comes up as partition and file format 'unallocated.'

---

### Post by coffeecat on 2012-02-06
> **Hamani said:**
>                                                    
Error: Cannot have a partition outside the disk!  

<snip>

Just loaded up GParted and the disk comes up as partition and file format 'unallocated.'

Whether or not you've got a corrupted ntfs filesystem, you have a partition table problem. That *might* be the issue underlying the mount difficulty. Gparted always shows "unallocated" when there's a partition table illegality.

Post the output of this command with the drive plugged in:

```
sudo fdisk -lu
```

---

### Post by Hamani on 2012-02-06
This is the output: 

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bb075

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   146030591    73014272   83  Linux
/dev/sda2       146032638   156248063     5107713    5  Extended
/dev/sda5       146032640   156248063     5107712   82  Linux swap / Solaris

Disk /dev/sdd: 500.1 GB, 500105740288 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976769024 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00022bd7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048   976773167   488385560    7  HPFS/NTFS/exFAT


Cheers, 

- Gary.

---

### Post by coffeecat on 2012-02-06
Here's your partition table problem:

> **Hamani said:**
> 
Disk /dev/sdd: 500.1 GB, 500105740288 bytes
255 heads, 63 sectors/track, 60801 cylinders, total [COLOR="Red"]976769024[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00022bd7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048   [COLOR="Red"]976773167[/COLOR]   488385560    7  HPFS/NTFS/exFAT


Your single sdd1 primary partition is showing as having an end sector 4143 sectors beyond the physical end of the drive. That's equivalent to about 2MB.

You *should* be able to repair the partition table with fixparts:

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

I say "should" because the usual problem that fixparts deals with is with a mis-sized extended partition and you have a mis-sized primary partition, which is unusual to say the least. Since an extended partition is only a special type of primary then I'm hoping that fixparts will deal with this, but since I've never tried fixparts in this situation I can't be 100% sure.

I'll express another uncertainty. It could be that your problem with mounting the partition in Linux and running chkdsk successfully in Windows is down to a mismatch between the filesystem and the actual physical size of the partition rather than the spurious size given by the partition table. I say could be - I'm merely speculating here. All I can say is that fixparts may or may not make the situation regarding the filesystem better. If this was my system, I would run fixparts and then run chkdsk in Windows, but I really can't predict the outcome.

As always - back up what you can first, **if** you can.

Before you proceed, would you like me to pm another member who can certainly give a good second opinion and who might have another perspective on this?

---

### Post by Hamani on 2012-02-06
Hi again, 

Thanks for coming back to this again. 

I'm out of the house for the next 2 days now, but when I'm back I'll borrow my friends 16gb USB and start backing up the important stuff on the drive ... Then I'll give your advice a go, and let you know what happens. 

- Gary.

---

### Post by coffeecat on 2012-02-06
Since you won't be able to do anything for a couple of days, I'll pm the other member anyway when I see that they are online. We're in different time-zones.

---

### Post by oldfred on 2012-02-06
I think fixparts should work. Only if it does not then you can use sfdisk and the file from the backup below to manually correct it.

You can backup partition table with sfdisk.

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sdd > PTsdd.txt

---

