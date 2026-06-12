---
title: "Install Ubuntu NTFS GPT"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by trekkiencc74656 on 2009-05-04
I have 2 HD on my pc my main drive with the os died and now I want to install ubuntu on the second one that had all of my data. The second drive is 1.5TB and is using gpt. It has two partitions a 20GB ntfs partition with a nonworking copy of windows and the rest of the drive is a large ntfs partition. I wanted to install Ubuntu on the 20GB partition but the partitioner in the installer does not recognize any partitions it just shows an empty drive. I tried loading gparted and it showed unallocated for the whole disk. I know there is data on there because I am able to mount the partitions from the live cd and access the data. I think that the problem is a compatibility issue with gpt. I really didnt want to have to buy a new HD just yet so if anyone can help me that would be great.

---

### Post by wiznillyp on 2009-05-04
Once you mount the drive, why not use GParted via LiveCD?

---

### Post by trekkiencc74656 on 2009-05-04
update. I am able to mount the partitions but not the complete drive. I can use gparted with individual partitions like "gparted /dev/sda1" however if I try to run gparted with the entire drive it comes up and shows the drive as being empty and in the terminal I get
```
/dev/sda contains GPT signatures, indicating that it has a GPT table.  However, it
 does not have a valid fake msdos partition table, as it should.  Perhaps it was corrupted --
 possibly by a program that doesn't understand GPT partition tables.  Or perhaps you
 deleted the GPT table, and are now using an msdos partition table.  Is this a GPT 
partition table?
```I asume it wants me to respond with y or n however I do not know
 how to send y or n to it.

---

### Post by bilijoe on 2009-05-09
[SIZE=3][COLOR=Red]This is a bug in the partition manager. [/COLOR][/SIZE]If you switch the view so the Partition editor is looking at the OTHER HDD, and then switch back to the drive you want to edit, you will see all the partitions exactly as they are. 

This is a _**very**_ frustrating bug, because, unless you are very tenacious, and just won't let go of something until you figure it out (as I often am), very, very few people are going to figure this one out, and they'll be confused by a display (which just needs to be refreshed) that tells them something that is not true.

Try it. I'll bet it'll work for you, and you'll then be able to do whatever partitioning you need to do on that drive.:)

---

### Post by caljohnsmith on 2009-05-09
> **trekkiencc74656 said:**
> update. I am able to mount the partitions but not the complete drive. I can use gparted with individual partitions like "gparted /dev/sda1" however if I try to run gparted with the entire drive it comes up and shows the drive as being empty and in the terminal I get
> /dev/sda contains GPT signatures, indicating that it has a GPT table.  However, it
 does not have a valid fake msdos partition table, as it should.  Perhaps it was corrupted --
 possibly by a program that doesn't understand GPT partition tables.  Or perhaps you
 deleted the GPT table, and are now using an msdos partition table.  Is this a GPT 
partition table?I asume it wants me to respond with y or n however I do not know
 how to send y or n to it.
All drives with a GPT keep a standard MS-DOS partition table in the HDD MBR (Master Boot Record) for backward compatibility; from the error you got above, it sounds like the MBR of your sda GPT drive is corrupt. If I were in your shoes, I would copy over a valid MBR to your sda GPT drive, and maybe that would be enough to fix the problem. Does your other HDD have a standard MS-DOS partition table, or does it use a GPT too? How about posting the output of:
```
sudo fdisk -lu
```
And we can work from there if you want.

John

---

