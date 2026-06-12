---
title: "No Partitions Detected on Installation of 9.10"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by Bhajun on 2009-11-05
Hi all,

I apologize if this has answered previously - I only found one unresolved topic which discusses the same problem I face ([http://ubuntuforums.org/showthread.php?t=1267532](http://ubuntuforums.org/showthread.php?t=1267532))

Currently I am dual-booting Windows XP and Ubuntu 9.04 on my system.  For various reasons, I wanted a clean install of Ubuntu now that 9.10 has come out and figured I would install it over my previous Ubuntu installation.

However, running the installation from CD, the partition manager fails to detect any operating systems or partitions.  It lists my 160gb harddisk as unpartitioned and prompts me to either format the entire drive and install, or to format and partition it before I continue.

Clearly neither of these options are ideal, and so I wondered if this was a known and/or resolved issue.  Any help would be appreciated.

Thanks.

---

### Post by lidex on 2009-11-05
Boot into ubuntu and run this command in terminal:
```
sudo fdisk -l
```
Post the output please. Also -- what do you see in partition manager?

---

### Post by Mark Phelps on 2009-11-05
> **lidex said:**
> Boot into ubuntu and run this command in terminal:
```
sudo fdisk -l
```
Post the output please. Also -- what do you see in partition manager?

+1 -- please note that's a lowercase "L", not a "one".

---

### Post by Bhajun on 2009-11-05
When booting up into 9.10 live mode, fdisk shows all of my partitions without issue, but gparted does not.

fdisk:
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           19196       19457     2104483+   c  W95 FAT32 (LBA)
/dev/sda2   *           7        7839    62918572+   7  HPFS/NTFS
/dev/sda3            7840       19457    93321585    f  W95 Ext'd (LBA)
/dev/sda5            7840       16062    66051216    7  HPFS/NTFS
/dev/sda6           16063       18673    20972826   83  Linux
/dev/sda7           18674       19195     4192933+  82  Linux swap / Solaris
/dev/sda8           19196       19457     2104483+   0  Empty

```

gparted:
[IMG]http://img694.imageshack.us/img694/2312/screenshotdevsdagparted.png[/IMG]


I have a similar issue when I boot into 9.04, which is currently installed.

Thanks.

---

### Post by lidex on 2009-11-05
Hmmm...take a look at [this]("http://www.linuxquestions.org/questions/linux-newbie-8/gparted-does-not-detect-partitions...-718673/")

---

### Post by Bhajun on 2009-11-06
That seems similar, but that's not exactly it.  So it seems that one of my partitions shows up twice in the fdisk listing (sda1 and sda8) for some odd reason.  I figure, though it may be possible to fix, it'll save me trouble now or in the future if I just wipe everything and start from scratch.

Thanks for your help though.

---

### Post by jasonaugustyn on 2009-11-06
I'm having the same problem trying to install 9.10 on a Dell XPS in dual boot with Vista. The partitioner claims "This computer has no operating systems on it", but of course Vista is already installed :confused:
 
Output of ```
sudo fdisk -l
``` is almost identical to that given above.
 
Suggestions? I've never had this problem with any other version of Ubuntu.

---

### Post by Joe Ker1086 on 2009-11-06
This isnt an ideal fix but it will work. If you are having trouble booting into your partitions it might make sense to install [This]("http://gag.sourceforge.net/index.html"). It is a graphical user interface that allows you to boot up to 9 partitions. And from what some other users say it can fix some unbootable partitions even when fixmbr doesnt work.

---

### Post by Joe Ker1086 on 2009-11-06
*side note* GAG can be run from a bootable disk so it is not necessary to install it if you don't want to :D

---

### Post by jasonaugustyn on 2009-11-08
Any other ideas? I've found several other posts describing the same problem, but nobody seems to have any answers. I could set up a new partition table and create the partitions manually, but that makes me nervous.

---

### Post by kyuubi777 on 2009-11-08
had issues w/ gparted as well, used Disk utility instead which read me errors every time i tried to modify partitions but completed the tasks successfully

---

### Post by lidex on 2009-11-09
Seems to be slightly epidemic. Some links:
[http://ubuntuforums.org/showthread.php?t=1290215](http://ubuntuforums.org/showthread.php?t=1290215)
[http://newyork.ubuntuforums.org/showthread.php?t=878204](http://newyork.ubuntuforums.org/showthread.php?t=878204)
[https://launchpad.net/bugs/bugtrackers/parted](https://launchpad.net/bugs/bugtrackers/parted)

---

