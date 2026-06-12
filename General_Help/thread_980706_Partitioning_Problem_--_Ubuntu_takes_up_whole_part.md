---
title: "Partitioning Problem -- Ubuntu takes up whole partition"
date: 2008-11-13
forum: General Help
---

### Post by fin7710 on 2008-11-13
I've been following a dual-boot tutorial for dual booting vista and ubuntu, and everything was going smoothly until I got to partitioning.  I have a 450 GB hard drive on my desktop, and I partitioned 100 GBs on my C: drive for linux in vista.  When I rebooted and went to install Ubuntu, I selected the "Guided Partitioning: Use Largest Contiguous Space"(or something like that) choice.  I expected this to assign the 100GB partition I made to Ubuntu, but instead, the chart at the top of the page shows Ubuntu taking up the entire drive, and not leaving room for Vista.  If I choose the Guided Partition option that leaves room for Vista, it only leaves 60GB for Vista and assigns the rest to Ubuntu.  Why doesn't the Ubuntu installer recognize the logical partition that I made on my C: drive?

---

### Post by alwez_loner on 2008-11-13
> **fin7710 said:**
> I've been following a dual-boot tutorial for dual booting vista and ubuntu, and everything was going smoothly until I got to partitioning.  I have a 450 GB hard drive on my desktop, and I partitioned 100 GBs on my C: drive for linux in vista.  When I rebooted and went to install Ubuntu, I selected the "Guided Partitioning: Use Largest Contiguous Space"(or something like that) choice.  I expected this to assign the 100GB partition I made to Ubuntu, but instead, the chart at the top of the page shows Ubuntu taking up the entire drive, and not leaving room for Vista.  If I choose the Guided Partition option that leaves room for Vista, it only leaves 60GB for Vista and assigns the rest to Ubuntu.  Why doesn't the Ubuntu installer recognize the logical partition that I made on my C: drive?

I faced the same problem when i started of. So i have to start all over again and did a manual partition. 

Then you can direct and specify the amount of space for linux. 

So try the manual way it would work better.

---

### Post by Quarkrad on 2008-11-13
I'm probably not qualified to answer you - I've only been with Linux/Ubuntu a few weeks.  However, I have been in your position -although I dual boot Ubuntu and winxp.  I had a new HD and did the following:

1. Installed Ubuntu using the whole HD
2. Put the CD back in and chose the 'try' option rather than install  (forget the exact words)
3. When the Try option boots up, under System, Admin there is a partition app (think its gpart) - you can use this to reduce the size of your Ubuntu partition. That is from the whole HD to something like 50G or 100G.  You can even format the remaining space/partition on your hd as NTFS ready for Vista.

When I did it I created a number of partitions as I have two winxp specific partitions.  (So I have one Ubuntu and thee Winxp partitions).

This was how I did it first time. Another time I re-installed I chose the manual option in the Ubuntu install process and manually set the size of the first partition.  It took a little getting use to, for me, because I am so use to (dam) windows - however, if you are confident with partitioning hard disks it is easy, just different.  I found a very good web page with instructions for all sorts of dual boot options with Ubuntu -this may be useful.  It certainly helped me out.

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

You will find the option you want (linux/Vista or Vista/linux) a little further down this page.

Hope this helps.

---

### Post by TeXtonyx on 2008-11-13
Install Vista to the whole drive delete what you have.
Then use the Vista tool to shrink the Vista partition.
That leaves you with unallocated space to install Ubuntu into.
I haven't use the 8.10 installation yet. But in the 8.04 live cd,
it says something more like 'use largest free space (unguided) '
That used the unallocated space and saves Vista from being overwritten.
Free space doesn't mean unused space within an already created
partition, in this context; it means the just made unallocated space.
Do not format some unallocated space with ext 3 and make it a
partition and try to install Ubuntu to it. Leave the space unallocated 
as described above. Use the above method if you have doubts about 
manual partitioning. I don't think the Ubuntu live cd says "contiguous",
as a default install option.

[http://thinkdigit.com/forum/showthread.php?t=96132&page=2#57](http://thinkdigit.com/forum/showthread.php?t=96132&page=2#57) 8.10

or [http://ubuntuforums.org/showthread.php?t=899222](http://ubuntuforums.org/showthread.php?t=899222) same idea
for manual partitioning with pictures.

---

### Post by mcduck on 2008-11-13
The "Use largest continuous space" means it sues the largest **free, unpartitioned**, space on the disk. It doesn't use any ready-made partition you might have.

In your case the installer couldn't find any usable space, so it went back to the only reasonable option (as it can't possibly know what parttion you'd want it to use) to se the entire disk.

So, if you really want to do parttioning beforehand your best bet is to leave the space you want for ubuntu unpartittioned. Then that option will detect it and things work like they should.

---

