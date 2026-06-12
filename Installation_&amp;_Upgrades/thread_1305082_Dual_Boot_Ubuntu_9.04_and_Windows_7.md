---
title: "Dual Boot Ubuntu 9.04 and Windows 7"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by Lasering on 2009-10-29
Hi!!

I usually install windows first then ubuntu. I do this because after I install ubuntu, GRUB is correct and I dont have to fix it (well I really dont know how to fix it, yet).

I did the above for dual booting windows vista and ubuntu 9.04 and it worked correctly.

So I tried the same with windows 7. But it didn't work.

Right now I have the following partition scheme:
Primary partitions:
100MB    NTFS    Windows 7 bootloader is here. (Not by my choice)
75GB     NTFS    Windows 7
32MB     Ext2    /boot
Extended partitions:
700GB    NTFS    Data (mainly free space and some games right now)
15GB     Ext3    /
1GB      Swap    Swap
140GB    Ext3    /home

When I installed GRUB I didnt get any error, in other words the installation worked.

BUT when I turn on the computer GRUB doesnt come up, it goes strait to windows bootloader.

I installed ubuntu using the alternate CD because I have a fakeRAID (RAID0 2x500GB SATA HDDs). All the partitions are in the fakeraid.

I tried to use Super Grub Disk to reinstall GRUB to the mbr, no luck.

So any suggestions on how to make GRUB come up instead of windows bootloader (which everyone knows, sucks by nature as we would expect it to)

---

### Post by Lasering on 2009-10-30
Bump

---

### Post by alldunn on 2009-11-01
Any help on this would be appreciated.  I am having the exact same issue.  Everything I have found on the forums has not worked thus far.  I am trying to install 9.04 and then upgrade to 9.10 because of this bug: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/444639/](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/444639/)

---

### Post by afrauen on 2009-11-02
[SIZE=2]I also encountered the same issue installing Ubuntu 9.04, after Windows 7 (the alternate CD was used, because I am also using FakeRaid ICH8R).[/SIZE]
[SIZE=2]GRUB appeared to install correctly, no warnings or errors were displayed.[/SIZE]
 
[SIZE=2]After the installation completed, I rebooted the computer which launched straight into Windows.[/SIZE]
 
[SIZE=2]I tried booting off the LiveCD, and mounting the filesystem in order to install GRUB. [/SIZE]
[SIZE=2]The following tutorial was used:[/SIZE]
_[SIZE=2][COLOR=#810081][http://forums.linuxmint.com/viewtopic.php?f=42&t=20170&start=15](http://forums.linuxmint.com/viewtopic.php?f=42&t=20170&start=15)[/COLOR][/SIZE]_
 
[SIZE=2]which failed on the "setup (hd0,2)" command (hd0,2 is the ubuntu root partition).[/SIZE]
 
[SIZE=2]Error 17: Cannot mount selected partition[/SIZE]
 
[SIZE=2]After this point I gave up and used the WUBI installer - which is not ideal.[/SIZE]
 
[SIZE=2]Doing some research today I discovered the following, which may help:[/SIZE]
 
[[SIZE=2][COLOR=#800080]http://ubuntuforums.org/showthread.php?t=531754[/COLOR][/SIZE]]("http://ubuntuforums.org/showthread.php?t=531754")
[SIZE=2]-> The partition you are trying to modify with grub needs to have the boot flag set either using fdisk or gparted.[/SIZE]
 
[SIZE=2]I am not sure if this was set when I attempted it. [/SIZE]

---

### Post by Mustard on 2009-11-02
You could use gparted (on the live CD?) to examine the partition setup and that would confirm whether you had a boot flag enabled on the relevant partition.

Come to think of it, there is a simple console command for the output...fdisk I think it is.

Yep..

```
sudo fdisk -l 


#      -l     List  the  partition  tables  for the specified devices and then
#      exit.  If no devices are given, those mentioned in  /proc/parti&#8208;
#      tions (if that exists) are used.

```

This should show an asterisk in the 'boot' column for those partitions that are flagged.

---

### Post by afrauen on 2009-11-02
[SIZE=2]There does seem to be a bug installing grub using the Ubuntu 9.04 alternate install CD + FakeRaid (if Windows 7 exists).

This should possibly be raised as a bug in launchpad?

[/SIZE]

---

