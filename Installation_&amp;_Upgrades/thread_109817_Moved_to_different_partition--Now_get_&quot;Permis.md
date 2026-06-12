---
title: "Moved to different partition--Now get &quot;Permission denied&quot; during boot process."
date: 2005-12-29
forum: Installation &amp; Upgrades
---

### Post by yababom on 2005-12-29
When I installed Kubuntu, I thought I told the installer to only use half of the available space on my second SATA drive. Somehow it didn't understand and used up virtually all my free space (200 gigs) on that drive.

To correct this, I wanted to move the installation to a smaller partition on my Primary hard disk so that I could wipe the large partition and get it re-partitoned the way I intended.

Being a Linux newb, I searched for some help on the internet and found the command "find / -xdev -print0 | cpio -pa0V /mnt/temp" on the following site: [http://www.greenfly.org/tips/filesystem_migration.html](http://www.greenfly.org/tips/filesystem_migration.html). I executed the command, adjusted my boot files to point to the new partition, and after disconnecting the old disk (external SATA), the system failed to boot.

The reason seems to be that some of the permissions didn't get copied over correctly--I get repeated "Permission Denied" errors, starting with the system disk check (is that the first process in Runlvl 5?). The boot process finally halts with a message that reads something like "There are no more processes to start in Run Level 5"  at which point my only option is to do a hard shutdown and restart the machine.

So, I'm sure that there a process that I can use in combination with the Breezy Badger boot DVD to reset the permissions and get the system back to normal, but I haven't been able to find it. Can someone point me in the right direction? Also, would anyone like to set me straight as to why the command above didn't work in the first place?

Thanks.

---

### Post by d11wtq on 2005-12-29
If you've done that without a full backup I reckon your quickest and easiest option is to reinstall.

The correct way to copy all files to another partition is to use the -a flag on cp.  You'd be best doing this from a Live Booted CD in a chroot environment.  I've done this a few times.

I'll assume that you want to move from hdc3 to hdc1 in this example.

```

#Boot your Live CD
mkdir /mnt/hdc3 #Create some mount points
mkdir /mnt/hdc1
mount /dev/hdc3 /mnt/hdc3 #Mount both partitions
mount /dev/hdc1 /mnt/hdc1
cp -av /mnt/hdc3/* /mnt/hdc1 #Copy the data (verbose for reassurance it's working)
#The -a means preserve all file attributes (backup identical)

```

Once you've done that you should edit your grub configuration to point to the new location... pretty simple but you can post back for help if needed :)

---

### Post by yababom on 2005-12-29
[QUOTE=d11wtq]If you've done that without a full backup I reckon your quickest and easiest option is to reinstall.

The correct way to copy all files to another partition is to use the -a flag on cp.  You'd be best doing this from a Live Booted CD in a chroot environment.  I've done this a few times.

I'll assume that you want to move from hdc3 to hdc1 in this example.

```

#Boot your Live CD
mkdir /mnt/hdc3 #Create some mount points
mkdir /mnt/hdc1
mount /dev/hdc3 /mnt/hdc3 #Mount both partitions
mount /dev/hdc1 /mnt/hdc1
cp -av /mnt/hdc3/* /mnt/hdc1 #Copy the data (verbose for reassurance it's working)
#The -a means preserve all file attributes (backup identical)

```

Once you've done that you should edit your grub configuration to point to the new location... pretty simple but you can post back for help if needed :)[/QUOTE]
If I do a re-install, will I need to wipe the partion first, or can I re-install "on top of" the corrupted install?

---

### Post by d11wtq on 2005-12-29
[QUOTE=yababom]If I do a re-install, will I need to wipe the partion first, or can I re-install "on top of" the corrupted install?[/QUOTE]

I don't see why you can't install over the top :)  It will just clobber any files that are there with it's own version.

Good luck! ;)

---

### Post by cjm5229 on 2006-01-01
If you are using the install DVD, it should also have the live version on it. If you run live and go to Applications>System Tools You will find Gparted. Use that to delete the partitions you want to use and then set up your partition you want to install Ubuntu onto. Then do your install and do the manual partition option and choose the partition you wish to use from there. While you are using the partioner notice that there is an option to "Copy data from another partition" Next time you want to make a copy of your partition try that. Hope this helps. 
Carl

---

