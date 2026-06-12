---
title: "Redoing disk partitions"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by yelloguy on 2009-10-07
I installed Karmic Beta yesterday and managed to get Mythtv backend running.  I made the mistake of installing it on a small 20 GB partition just to see how I like it.  But now that I have decided to keep it, I am stuck with the problem of redoing the disk partitions.

Primary disk is a 160GB Windows XP bootable disk.  Secondary 160 GB disk has a 140 GB partition (extended) and 20 GB for Ubuntu (with 1GB swap and 19 GB root).

I am going to get rid of Windows and I almost formatted the primary HDD.  But then I realized that it is the boot drive and my PC will not boot without the correct grub files.

So, what would be the correct way to #1 format it, #2 re-install grub on it and #3 assign it to mythtv backend for storage?

Thanks in advance for any and all of the help.

---

### Post by oldfred on 2009-10-08
It may be heresy to say it but are you sure you want to totally remove windows?   Karmic is just into beta and I see lots of issues still being resolved. You might not be able to boot Karmic? I like to have more than one operating system and at least one per hard drive. You should be able to houseclean windows, defrag a couple of times and get it down to 20-30 GB depending on what you have left on it, which still gives lots of space for you new partition. 

I would use Gparted to change partitions and format any new partitions.
Grub is in the MBR and changing partitions should not change the boot.
Only if you change partitions on the Ubuntu drive so ubuntu's partiion number changes would you have to reinstall Grub, edit menu.lst and fstab to update partition data. You can edit menu.lst to remove the windows entry if you delete windows.

For you new partition you will have to make a temp mount point and then copy all your data over to it. Then unmount it and your current mythtv mount and remount the new partition as the mythtv one. To make it permanent you edit fstab.

---

### Post by drs305 on 2009-10-08
If you decide just to resize your existing / partition here is a post that might help. It was designed for users who messed up the initial install but the principles apply regardless of the partition size.

[Expanding an Ubuntu System Partition ]("http://ubuntuforums.org/showthread.php?t=1219270")

Note that expanding or contracting a partition can take a looooong time.

---

### Post by yelloguy on 2009-10-08
Thanks both for the help.  I would keep Windows but only if I can shrink it (it is less than 20 GB filled).  The Disk Utility in Ubuntu is useless.  You mentioned Gparted so I installed it and it looks way better.  But it still does not let me shrink my Windows partition.  I have unmounted the only partition before starting Gparted but that does not help.  Delete is my only choice.

On reformatting, I am pretty sure Grub is installed on the first hard drive with one Windows partition on it.  The second hard drive with a data partition (extended NTFS) and two ext3 partitions (swap and root) is not bootable.  I could be wrong about this but I can't figure out how to confirm that with grub.  I just skimmed through the big grub tutorial linked in drs305's post.

---

### Post by oldfred on 2009-10-08
Did you defrag your windows at least twice, it does help, before trying to shrink it.

It is difficult to tell where grub is installed but this script will tell you everything about how your system is configured and where grub is. We suggest is for debugging boot issues, but I ran it myself just to understand my system.

Boot Info Script 0.32 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions
[http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3)
cd to directory saved to:
chmod 755 boot_info_script032.sh
sudo ./boot_info_script032.sh
or  as example if on desktop
sudo bash ~/Desktop/boot_info_script*.sh
This will create a RESULTS.txt file in the same directory.

---

### Post by yelloguy on 2009-10-08
Looks like gparted needs ntfsprogs to be installed for resizing ntfs partitions.  I am resizing it now.

---

