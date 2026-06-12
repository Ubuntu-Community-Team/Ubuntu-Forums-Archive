---
title: "Installer does not detect existing partitions"
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by geekity2 on 2009-07-20
Hi all,

I'm having a minor conundrum installing ubuntu on a friend's computer. Basically, the laptop is a Dell XPS (live cd runs fine, so the specs should be grand), currently with three partitions (C, D and a small partition at the beginning, I'm not sure why but probably due to windows) on it, and windows XP installed (although the XP didn't come with it originally). 

When the ubuntu installer gets to the partitioning, it detects the hard drive as a full blank continuous space. Ideally, I would have liked to either use the D partition or shrink D and use the empty space for the linux, but I'm a bit worried about the whole thing since when I tried resizing D with gparted, it was detected as only continuous space as well. Any suggestions on how to get the partitioning done would be greatly appreciated.

---

### Post by komputes on 2009-07-20
Which version of ubuntu is this? I've never seen anything like this. Can you take a screenshot. You can also open System > Administration > Partition editor from the LiveCD and take a screenshot from there.

---

### Post by geekity2 on 2009-07-20
Hi komputes. I'm trying to install ubuntu 9.04 desktop edition. The computer is Dell XPS M1530. Here's the screen shots of gparted and from the installer.

---

### Post by raymondh on 2009-07-20
Sometimes, when there are overlapping/overflowing partitions, libparted goes 'crazy' and will not read the disk. Or when partition tables are not in order.

Sometimes, the newer version of gparted seems to be better ... although in this case, I think 9.04 has the newest version.

Have you partitioned any?  Using the liveCD, and from terminal, what's the output of

```
fdisk -l
``` ?  (small L, not 1 nor i)

Regards,

---

### Post by komputes on 2009-07-20
That looks pretty messed up if you actually have partitions on that drive. I would report a bug against libparted as both gparted and ubiquity (partitioning stage of installer) use it.

---

### Post by merlinus on 2009-07-20
The current version of gparted live is newer than the one on the ubuntu install cd.  You might try that before doing anything else.

[http://sourceforge.net/projects/gparted/files/](http://sourceforge.net/projects/gparted/files/)

---

### Post by raymondh on 2009-07-20
> **merlinus said:**
> The current version of gparted live is newer than the one on the ubuntu install cd.  

Thanks Merlin, 'did not know that.  Time to re-download and make a standalone gparted disk for me :)

---

### Post by geekity2 on 2009-07-21
> **raymondhenson said:**
> Sometimes, when there are overlapping/overflowing partitions, libparted goes 'crazy' and will not read the disk. Or when partition tables are not in order.

Sometimes, the newer version of gparted seems to be better ... although in this case, I think 9.04 has the newest version.

Have you partitioned any?  Using the liveCD, and from terminal, what's the output of

```
fdisk -l
``` ?  (small L, not 1 nor i)

Regards,

Hi raymondhenson,

the output was

```
ubuntu@ubuntu:~$ fdisk -l

Disk /dev/sdb: 4005 MB, 4005527552 bytes
250 heads, 19 sectors/track, 1647 cylinders
Units = cylinders of 4750 * 512 = 2432000 bytes
Disk identifier: 0x0006dc46

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1648     3911647+   c  W95 FAT32 (LBA)

```

Merlinus, I'll give the new gparted a shot. 

Thanks for the help, I'll keep you posted.

--------

So I tried using a live gparted cd (0.4.5-3), and it, too, doesn't detect any existing partitions. A workmate reckons this may be due to the windows partitions having been made using partition magic in some restricted fashion. Is there any open source or free partitioner which can deal with partition magic made partitions, or what would be my best course of action?

---

