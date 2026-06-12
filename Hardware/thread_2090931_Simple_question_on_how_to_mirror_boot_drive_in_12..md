---
title: "Simple question on how to mirror boot drive in 12.10 after installing"
date: 2012-12-03
forum: Hardware
---

### Post by rendyr on 2012-12-03
Hi all, I am new to this forum, and am happy to have found it!

I have been trying to find this all over and can't find a search, or other information on this.  I have good Solaris experience, and in Solaris this is easy to do, but for some reason I can't find the answer for Ubuntu:

I want to mirror my boot drive, how do I accomplish that, and have both be bootable in case one fails (true mirror).

I have two drives in the computer, both are the same model/size.  I installed Ubuntu 12.10 and desire to create an array, and mirror the two drives.  Anyone have ideas/pointers?

Things I have found, but not followed:
-"fake raid" through chipset - do not want a MB failure to hose all my data
-using 12.04 alternate installer to reinstall, then upgrade to 12.10 (can do this, but would lose all the data/work I have already done)

Thanks for any advice!

---

### Post by ahallubuntu on 2012-12-04
If you want to do it as a software RAID mirror, I'd probably do it this way:

[http://blog.neolocus.com/2012/04/ubuntu-12-04-lts-and-soft-raid-with-mdadm/](http://blog.neolocus.com/2012/04/ubuntu-12-04-lts-and-soft-raid-with-mdadm/)

I'm not a fan of RAID mirrors.  A RAID protects you only from hard drive failure and not from file system corruption or accidental erasure.  I do understand the need for it, but I prefer to make backups in other ways and monitor S.M.A.R.T. to check hard drive health.

Another way to do it is to create an LVM (Logical Volume Management) that allows snapshots of live filesystems.  You have to use the alternate install disc for this, too.  Anyway - make a separate small /boot as a non-LVM ext2 partition and put the rest in an LVM.

Then, create the same structure on your backup disk.  Then use the "dump" and "restore" commands to backup/restore your Ubuntu OS partition on the fly to your backup.  (You'll want to install Grub on the backup disk too, separately.).  If you are the type who makes separate partitions for OS and data, you can backup your data partition using rsync - more simple than dump (and no LVM required for that).

If you want more info for LVM in Ubuntu, google for it (LVM2 is actually what you want).

FYI, Ubuntu 12.04 LTS is a "Long Term Support" release that is supported until 2017.  Ubuntu 12.10 is supported only for 18 months until May 2014.  Unless you really need something in 12.10, I recommend you stick with 12.04 LTS if you plan to keep it for a couple of years.

---

### Post by rendyr on 2012-12-04
This is really great info, thank you for the thorough answer!  It sounds as if the best way to mirror the root drive is via initial install, since it does all of the work for you.  I will probably just do that and move my info off of the drive, reinstall the proper way using 12.04 and be done with it.  Frustrating, but then again I will probably save time, which will help the frustration pass quickly :)

Thanks!

---

### Post by irv on 2012-12-04
I am not sure, but maybe this will help. It helped others.
[http://ubuntuforums.org/showthread.php?t=238672]("http://ubuntuforums.org/showthread.php?t=238672")

---

