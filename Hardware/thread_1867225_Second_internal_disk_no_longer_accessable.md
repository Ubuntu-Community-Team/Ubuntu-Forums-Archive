---
title: "Second internal disk no longer accessable"
date: 2011-10-22
forum: Hardware
---

### Post by Batch2 on 2011-10-22
Hey There, 
I have a laptop running 11.10 exclusively (no dual-boot) that I just switched over from Windows Vista. This computer has two internal hard disks, one on which the operating system is installed and another that I use as a data drive. Both of these drives were functional when the computer was running Windows and appeared to function properly when I booted Ubuntu from a USB. However, when I installed the fully version of Ubuntu and eliminated Vista I must have done someting wrong because now my data drive does not show up on my system and it doesn't look like it's showing up in my BIOS. I may have deleted a partition or un-mounted the disk somehow, I don't really know. 

I know enough to take directions and operate the terminal as long as directions are clear and concise. However, I am just enough of a noob to kill this computer if I try to fix this on my own. 

If anyone has any idea how I might recover/re-mount my data drive I would really appreciate the help. Let me know if you need additional info.

Thanks

---

### Post by ajgreeny on 2011-10-22
Can you open a terminal and run the command ```
sudo fdisk -l
```(lower case L at the end) then copy back here the output of that command.

---

### Post by Batch2 on 2011-10-23
Apologies for the slow reply: 

Here's the output:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009ae92

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   308533247   154265600   83  Linux
/dev/sda2       308535294   312580095     2022401    5  Extended
/dev/sda5       308535296   312580095     2022400   82  Linux swap / Solaris

---

### Post by ajgreeny on 2011-10-24
Are you sure the "disks" were physical disks and not just partitions?

What were their sizes in windows compared with the current 160GB disk showing in Ubuntu?

---

### Post by dougalkerr on 2011-10-24
I would tend to agree with aigreeny, it sounds like when you went for the install, what was formerly seen as two disks may in fact have been one disk with two partitions. 
Can you confirm you have two physical disks?

The system may well have deleted both partitions (if this is the original setup) and installed as per one disk. If so you haven't lost anything.

---

### Post by Batch2 on 2011-10-24
You may be correct. I didn't physically look to see if there are separate physical drives. I assumed that was the case because I've done a fresh install of windows on this machine twice and not lost any of the files from the "Data" drive. However, I'll confirm this shortly. 

If there is only one drive, I'm guessing that deleting the partition also deleted all of the files previously one the drive. Would that be correct?

---

### Post by ajgreeny on 2011-10-24
> **Batch2 said:**
> You may be correct. I didn't physically look to see if there are separate physical drives. I assumed that was the case because I've done a fresh install of windows on this machine twice and not lost any of the files from the "Data" drive. However, I'll confirm this shortly. 

If there is only one drive, I'm guessing that deleting the partition also deleted all of the files previously one the drive. Would that be correct?
Yes, that would be so.

How big were the two windows "drives"?  If they were 160GB in total, then it was just a single drive and all your data is now gone, though might be recoverable using testdisk from a live CD.

Beware.  The more you use the current hard drive the worse the chances of recovery will be.

---

### Post by Batch2 on 2011-10-24
Hey There, 

Looks like there's one 160 gig HD inside. I can't for the life of me remember what it was originally split into, but it appears that the single drive was just partitioned. Thanks for troubleshooting this with me, turned out to be simpler than I originally thought. 

I did run a system backup before wiping Vista off of my machine so I have all of my stuff, but now I have to either wade through the mountains of .zip files in the backup folder or find a Windows computer and use backup assistant.,, Unless there's some program fur Ubuntu that will read a windows backup file. 

Anyway, thanks again for your help.

---

