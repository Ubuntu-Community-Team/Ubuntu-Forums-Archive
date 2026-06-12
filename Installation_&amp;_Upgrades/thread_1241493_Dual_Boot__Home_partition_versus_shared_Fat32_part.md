---
title: "Dual Boot:  Home partition versus shared Fat32 partition"
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by sanford55 on 2009-08-16
**SOLVED**  Hi.  I am planning out my partitions for dual booting Ubuntu and XP.  Discussions of dual booting differ over whether there should be a shared Fat32 partition or a special Ubuntu Home partition.  It seems to me that a shared Fat32 partition makes sense since it makes it possible to share common email and so on, but I am wondering about the advantages and disadvantages of each option.  In the past, I have dual booted without having either of these extra partitions, but it seems a lot of people like them.  My understanding is that the main advantage of a separate home partition is that it is easy to maintain when upgrading to a new version of Ubuntu, or if the old version becomes corrupted, but the disadvantage is that it is easy to get the relative size of the home partition and the OS partition wrong so that space gets scarce in one or the other.  Any advice would be much appreciated!  Sanford.

---

### Post by Support the 2nd on 2009-08-16
If you are going back and forth between XP and ubuntu a lot, it makes sense to have a very large Fat partition and use that.

---

### Post by meindian523 on 2009-08-16
If you aren't going to be doing too much installation of applications in Ubuntu,IMHO,10GB is more than enough for the system partition as you say(/)I would say keep aside as much space as you think you will need for the files you plan to share between Ubuntu and XP for a shared data FAT32 partition(or even NTFS) and use whatever is left after allocating enough to XP(which you will install first anyway) to /home,which would be either ext3 or ext4 (my preference)

EDIT:FAT32 doesn't support permissions,so you should not make your /home partition FAT32.Therefore I recommended a shared data partition separate from /home.

---

### Post by presence1960 on 2009-08-16
I recommend an NTFS partition for shared data between windows and Ubuntu. Use [gparted Live CD]("http://gparted.sourceforge.net/livecd.php") to create the NTFS partition and all your partitions prior to installation. The boot the Ubuntu Live CD and proceed with the install. FAT 32 has a limit of 4 GB on file size and Ubuntu reads/writes to NTFS very well. Go with NTFS.

---

### Post by g160689 on 2009-08-16
you can have different partition for xp(ntfs) & ubuntu(ext3) and still access the files of xp just by mounting the drive (provided that xp is installed first followed by ubuntu)

---

### Post by presence1960 on 2009-08-16
> **g160689 said:**
> you can have different partition for xp(ntfs) & ubuntu(ext3) and still access the files of xp just by mounting the drive (provided that xp is installed first followed by ubuntu)

You can mount the partition in ubuntu whether it was installed first, second, third or any order. I installed windows 7 RC after Ubuntu 9.04, Sabayon 4.1 & Mint 5. I can mount the windows partition & the NTFS data partition from Ubuntu at any time.

Why do a lot of us have this "windows first" mentality? That is a myth. Although I will say this a new twist on the "Windows must be installed first" myth. I have never heard this one before : that in order to mount a windows partition windows needs to be installed first. Not true!

---

