---
title: "No partitions detected by installer, partition table bad ... how to fix it?"
date: 2009-05-31
forum: Installation &amp; Upgrades
---

### Post by owkaye on 2009-05-31
The Ubuntu 9.04 installer fails to recognize the existing partitions on my internal SATA hard drive.  Instead it displays the drive as having no partitions, which means I cannot install Ubuntu to a specific ext3 partition that already exists on the drive.

After reviewing [another thread]("http://ubuntuforums.org/showthread.php?t=1147450") and seeing the same problem diagnosed as a bad partition table, I think I have the same problem.  Here is the information I collected so far:

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb6c759d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2         3662820    90847574    43592377+   7  HPFS/NTFS
/dev/sda3   *   295649280   312580095     8465408   17  Hidden HPFS/NTFS
/dev/sda4         3084480   295644194   146279857+   5  Extended
/dev/sda5         3084543     3662819      289138+  82  Linux swap / Solaris
/dev/sda6        90847638   254678444    81915403+  83  Linux
/dev/sda7       254678508   295644194    20482843+   b  W95 FAT32

Partition table entries are not in disk order


ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=  3072000, Id=27
/dev/sda2 : start=  3662820, size= 87184755, Id= 7
/dev/sda3 : start=295649280, size= 16930816, Id=17, bootable
/dev/sda4 : start=  3084480, size=292559715, Id= 5
/dev/sda5 : start=  3084543, size=   578277, Id=82
/dev/sda6 : start= 90847638, size=163830807, Id=83
/dev/sda7 : start=254678508, size= 40965687, Id= b


ubuntu@ubuntu:~$ sudo parted /dev/sda print
Error: Can't have overlapping partitions.
```From what I've read in other threads, the partitions must be listed in disk order, they should start and end on cylinder boundaries, and they must not overlap.  Unfortunately I don't know how to create and install a valid partition table that fixes all these problems.  

Can anyone help me?  Thanks in advance.

P.S.  I asked for support in the other thread but after 24+ hours no one responded, so maybe I should have posted my support request in this new thread  from the beginning.  I apologize if I've broken the proper protocol here.  From now on I will create a new thread with my own support issues instead of posting in other people's threads.

---

### Post by merlinus on 2009-05-31
Are you running windows?  Which version?  And which version of ubuntu are you wanting to install?

It may be best to start over, though.  Backup important data, install windows, then shrink its partition, and install ubuntu into remaining space.

You can make a separate partition for /home if you so desire during the ubuntu install.

---

### Post by owkaye on 2009-05-31
> Are you running windows?The computer came with Windows Vista Home Premium pre-installed on its internal drive.

> Which version of ubuntu are you wanting to install?9.04 desktop

> It may be best to start over, though.  Backup important data, install windows ...I have several data backups so the data is not the problem, but thanks for the safety warning ... :)  Actually it is virtually impossible for me to re-install Windows at this point anyways because no CD's came with the computer, so I have to work with what I have now on the internal hard drive. 

And since the Windows OS works fine there is really no need to reinstall it anyways.  From what I can tell, the only real problem is the corrupted partition table which prevents Ubuntu's installer from seeing the partition I want to install it in.

>  ... then shrink its partition, and install ubuntu into remaining space.That's what I did in the beginning, and this may be what screwed up the partition table in the first place, although this is only conjecture on my part ...

Apparently some other folks have used the "shrink" feature of Windows to make space on the drive for other operating systems. I didn't know about this feature until later so I used the same Linux tool I've always used to resize partitions -- gparted -- and it appeared to work when I installed PCLinuxOS onto the new partition, after which I had a perfectly functional dual-boot system with Windows and PCLinuxOS.

Then later I decided to get rid of PCLinuxOS and replace it with Ubuntu, and that's when I learned that the Ubuntu installer could not see the ext3 partition PCLinuxOS was installed in.  So I could not get Ubuntu installed.  I thought this was rather strange because PCLinuxOS installed without any problem in the same new ext3 partition, so for a follow-up test I tried to install PCLinuxOS again -- and it successfully installed again just like the first time.

But when I tried the Ubuntu installer again for the second time it failed again, just like the first time.  That's when I got online and started learning that this is a frequent problem with the Ubuntu installer ...

Apparently the Ubuntu installer (I think it's called 'ubiquity') does not have the same capabilities as the PCLinuxOS installer (which is based on Mandriva).  In simple terms, it seems the Ubuntu installer cannot "see" existing partitions when something is wrong with the partition table, so instead of posting an error message the Ubuntu installer displays a picture of the hard drive that shows no partitions whatsoever.

This is deceiving / misleading when there are most definitely several partitions on the drive.  I think this may tempt some people to install onto what looks like a 'blank' or unpartitioned drive, possibly overwriting important files and other OS's on the drive -- not a good thing in my opinion.

--------------------------------------

The bottom line here is that I have the same problem others reported in the thread I linked to in my first post, so I'm pretty sure a properly written partition table will fix it.  I'm just waiting and hoping that the support tech (John) who helped others with similar problems can help me too ... 

:)

---

### Post by merlinus on 2009-05-31
This may help:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by lisati on 2009-05-31
If you manage to get Vista up and running, you might want to see if it came with software that will let you make a backup of your recovery partition just as a precaution - if present it's probably called something like "recovery disc creator".

Good luck.

---

### Post by owkaye on 2009-06-01
Hoping someone can help me with this ...

---

### Post by owkaye on 2009-06-02
Well, after waiting 3+ days with no answer from caljohnsmith to my partition table replacement request (either in this thread or in the other thread I mentioned earlier) I realized that I was probably not going to get a new partition table from him any time soon.  Given the fact that I need to get this computer back into working condition ASAP, I decided to stop waiting and just wipe the drive clean, then try to reinstall from scratch.

But first I needed a set of Recovery Disks so I burned them as suggested by lisati.  It took 3 DVD's and hours to create the disks and then reinstall Vista HP to the hard drive, but fortunately the new installation gave me a choice of creating a much smaller partition than what came with this laptop ...

Instead of forcing me to use the entire disk I installed the OS into a new 30 GB partition -- the smallest Vista would let me create.  I could have reinstalled the Recovery Partition but I already have the DVD disks so I don't need that data on the hard drive now anyways.

My disks apparently burned properly because I was able to fully restore the original OS, and because I didn't partition the whole drive there was LOTS of unallocated space left for Ubuntu ... which installed properly with no problem whatsoever in a 10 GB / partition and a 50 GB /home partition, both formatted ext3.  

I put a 2 GB swap partition at the very end of the drive too, and this left me with close to 60 GB still unallocated in between /home and swap -- which means I can easily expand my /home partition in the future if necessary, without moving anything else around.  

Yay, success!

Although I did not achieve the solution I first set out to achieve, I am convinced that this solution is far better ... so thanks to everyone who made suggestions because you folks provided the important information I really needed to solve this problem in the BEST possible manner.

:)

---

### Post by alexwyu on 2009-11-14
I just want to share my experience with others having the same issue.

Coincidentally, this also happen to me.  And somehow I do not think it is something to do with Ubuntu installer.  I had my test harddrive installed with 5 distros of linux, with 2 of them being Ubuntu (9.04 and 9.10); and Ubuntu 9.04 is the last of the 5.  After the installation, I had no problem seeing the partitions from GParted.

But after I install PCLinux OS, the problem appeared.  During the PCLinux installation, I noticed PCLinux proced rather aggressively, as it did not even confirm with the user about the operation.

Later, I found that PCLinux has it own facility to manage local disk.  And even it also complained about the partition table is corrupted, it manage to show the partition table in a rather different arrangement, with all the partitions present.  Also, I tried "sfdisk -l" command and it shows all partitions (but fdisk command failed to detect the partitions)

So I doubt there might be something to do with the partitioning process from other distros that GParted does not recognise and report and issue.  I hope someone would have a solution to rearrange partitions safely to recover the problem.

Thanks for your attention.

---

