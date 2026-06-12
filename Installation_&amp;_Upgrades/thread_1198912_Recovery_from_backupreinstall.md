---
title: "Recovery from backup/reinstall"
date: 2009-06-28
forum: Installation &amp; Upgrades
---

### Post by seanlano on 2009-06-28
I just reinstalled Jaunty on my desktop PC, after I screwed something up big-time (not really sure what, but anyway, it wouldn't login). Before I did so, I made a complete copy of the "/" partition to my "/home" partition (when booted from the LiveCD). 


I was wondering, can I copy back certain folders to restore: users and groups, downloaded updates, and icons? Obviously I don't want it all, because I'll just get whatever was causing the problem in the first place, and I'm changing the install from 64bit to 32bit anyway, so the hardware related stuff will be different. 

Also (more importantly), is there any way to retrieve a list of installed packages so I can reinstall them?

---

### Post by ridgeland on 2009-06-28
> Also (more importantly), is there any way to retrieve a list of installed packages so I can reinstall them? 
In Synaptic there are options for history and keeping packages. In Synaptics Settings -> Preferences open the tab "Files".  If you tell it to keep history you can view the history in Files -> History.  If you tell it to keep packages they will be in /var/cache/apt/archives.  If you copy those packages from an old install to the new install you will save the download step unless they are out-of-date or the wrong platform.  Most packages are not the same for x64 and i386.

You cannot truly copy "/" while in that partition.  Boot from the LiveCD or another partition and use "cp -a /oldpartition/* /backup/"  Look out for /etc/fstab and /boot/grub/menu.lst when cloning partitions but if all you were doing is /home this should not matter.

---

