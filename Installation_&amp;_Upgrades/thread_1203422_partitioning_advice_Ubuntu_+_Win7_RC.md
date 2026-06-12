---
title: "partitioning advice: Ubuntu + Win7 RC"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by Denis on 2009-07-03
Hi

I would like to do a clean install of Ubuntu 9.04 and Windows 7 RC. I've got two hard drives: a WD 320GB and a brand new Samsung 1000GB. 

In my new configuration I'd like to get rid of the /boot partition and have a separate /home partition instead. Filesharing between Ubuntu and windows can be done on the Windows NTFS partition. 

In addition I have [read]("http://www.ubuntu.com/testing/karmic/alpha2#ext4%20by%20default") that Karmic will have EXT4 by default. I would like to start using EXT4, as there seem to be little trouble and I'm not editing any critical files at the moment. 

I have worked out a partitioning scheme, with the following characteristics:
[LIST]
[*]Partitions that need to be fast are positioned closer to the end of the drive. **[edit: the first partition is placed at the outer tracks of the disk!]**
[*]/home and Ubuntu (root) are put on separate disks to minimize hard disk head movement
[/LIST]

Is this a good partitioning layout? Have you got any advice?

Thanks in advance. 

[IMG]http://users.telenet.be/dionos/suggestion_layout.jpg[/IMG]

---

### Post by raymondh on 2009-07-03
> **Denis said:**
> Hi

I would like to do a clean install of Ubuntu 9.04 and Windows 7 RC. I've got two hard drives: a WD 320GB and a brand new Samsung 1000GB. 

In my new configuration I'd like to get rid of the /boot partition and have a separate /home partition instead. Filesharing between Ubuntu and windows can be done on the Windows NTFS partition. 

In addition I have [read]("http://www.ubuntu.com/testing/karmic/alpha2#ext4%20by%20default") that Karmic will have EXT4 by default. I would like to start using EXT4, as there seem to be little trouble and I'm not editing any critical files at the moment. 

I have worked out a partitioning scheme, with the following characteristics:
[LIST]
[*]Partitions that need to be fast are positioned closer to the end of the drive.
[*]/home and Ubuntu (root) are put on separate disks to minimize hard disk head movement
[/LIST]

Is this a good partitioning layout? Have you got any advice?

Thanks in advance. 

[IMG]http://users.telenet.be/dionos/suggestion_layout.jpg[/IMG]

A thread that may help you (for reference)

[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

You're very generous with /home :)  Nice to have the options with that size ;)  Just some thoughts ....

Why not just put /home inside the extended and beside root (/)?  

I have 20GB for root (as I do grow my system fat) but now realize that is overkill.   

If you want (in an extended partition) 20 GB for root, 30GB for /usr and 100GB for /home.  

I think 100GB is plenty for /home .. but then again, you may have a reason for  needing 400GB.

That way, you can dedicate all the 1TB for heavy media and critical data.

PS:  I have always believed that partitions that produce the fastest (in read and write) are in the center of the HD as that location minimizes the travel of the head.  Again, we may be splitting hairs here.

[http://www.ranish.com/part/primer.htm](http://www.ranish.com/part/primer.htm)
[http://www.tldp.org/HOWTO/Multi-Disk-HOWTO.html#toc3](http://www.tldp.org/HOWTO/Multi-Disk-HOWTO.html#toc3)

Good luck.  Again, this was just my .02 worth of thoughts.

---

### Post by milton1 on 2009-07-03
Don't forget that windows 7 will want a small boot partition to hold BOOTMGR.

---

### Post by michaelzap on 2009-07-03
Personally I would just give Windows the entire smaller drive and Ubuntu the entire larger drive (with separate home and swap partitions). That way you don't even have to mess with grub, since you can boot from either drivey choosing it from your BIOS boot menu. Then when you want to try Koala or your Windows 7 RC runs out, the transition is simple.

---

### Post by Denis on 2009-07-04
Thanks for your advice already. 

> Don't forget that windows 7 will want a small boot partition to hold BOOTMGR.  I looked this up and it seems Windows 7 installs the boot manager in MBR, just like XP. As the Main Boot Record (MBR) is located [before any partitions]("http://en.wikipedia.org/wiki/Mbr"), I don't think it is necessary to make a partition for it. If I install Ubuntu after Windows 7, GRUB should be added and given priority. 

> Why not just put /home inside the extended and beside root (/)?

I have 20GB for root (as I do grow my system fat) but now realize that is overkill. 
You did make me realize that my root is only about 4 GB at the moment. So 150GB would indeed be overkill. 

My /home contains 94GB now and I would like to have at least two times this amount of space. So fitting it on the first disk is rather tight. I could provide 200GB and limit Win7 to 100GB. 

I still like the idea of having /home and root on separate disks. Both drives could be accessed at the same time ([Drive parallelising]("http://www.tldp.org/HOWTO/Multi-Disk-HOWTO-11.html#ss11.4")) and take advantage of the [faster outer sectors]("http://partition.radified.com/partitioning_2.htm"). Maybe it's more useful to have a 50GB root partition at the end of the 1Tb drive, with /home on the first drive instead...

Anyway, do give me your thoughts. I still need some time to think about it ;)

---

### Post by Denis on 2009-07-08
Taking into account your feedback, I've made some changes to the scheme. 

One thing I got wrong is the position of the fastest partition. The first partition will be placed on the outside of the disk. this means **the first partition is the fastest** (not the last). 

As mentioned 150GB would be too much for the root partition. I limited it to 20GB. Home and Windows could also do with slightly less space. 

As there are reports of [some important bugs]("https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/317781?comments=all") in EXT4, I figured it would be safer to use EXT3 for my /home. 

The resulting partitioning scheme is displayed below. It has: 

**Western Digital 320GB**
[LIST]
[*]Home (EXT3, 300GB)
[/LIST]

**Samsung 1000GB**
[LIST]
[*]Ubuntu root (EXT4, 20GB)
[*]swap (2GB)
[*]Windows 7 RC (NTFS, 130GB)
[*]Data (EXT3, 800GB)
[/LIST]

[IMG]http://users.telenet.be/dionos/suggestion_layout_improved.jpg[/IMG]

---

### Post by raymondh on 2009-07-08
Looks good Dennis.

Remember that windows likes to 'think' it is first on the drive.  If you find that you are not able to boot into windows, the workaround is just a "re-mapping-edit-to-the-menu.lst"  away :)

BTW, which is master and which is slave?  You may have to change the BIOS order to make sure the HD that has the MBR/GRUB boot's up first.

Happy Ubuntu-ing.

---

### Post by Mark Phelps on 2009-07-08
Already running a multi-OS setup (including MS Vista and Seven, and several different Linuxes) I would second the recommendation to give each OS its own drive.

Consider that if you ever have file corruption or other problems with Seven that require a Startup Repair, presuming you are booting from the big drive, you will have to reinstall GRUB all over again because Seven will automatically overwrite the MBR on its drive and wipe out the GRUB entry in the process.

If you don't like the idea of giving Seven the entire smaller drive, then create a shared NTFS partition for most of it to hold data that you want to share between Seven and Ubuntu.

---

### Post by Denis on 2009-07-09
> **raymondhenson said:**
> BTW, which is master and which is slave?  You may have to change the BIOS order to make sure the HD that has the MBR/GRUB boot's up first.

The disks are both SATA, so I guess it doesn't matter. The 1TB Samsung will be SATA1, the other SATA2. Shouldn't cause any problems this way.  

> **Mark Phelps said:**
> Already running a multi-OS setup (including MS Vista and Seven, and several different Linuxes) I would second the recommendation to give each OS its own drive.

I considered your point. The MBR will indeed be overwritten if I ever want to reinstall Windows. On the other hand, restoring GRUB isn't that hard. Taking this into account, I'll chose for the layout that was posted here. In terms of disk space, it just suits my needs best. (I did check out how to select a boot disk through the BIOS. It's an interesting feature to know about). 

Thanks for all your advice. Tomorrow I'll be installing Windows 7 RC and Ubuntu 9.04. I'm quite excited about it ;)

---

