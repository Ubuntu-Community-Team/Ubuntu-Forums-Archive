---
title: "How to make a partition on ubuntu of windows.?"
date: 2011-11-19
forum: Hardware
---

### Post by RaptorJay on 2011-11-19
How to Make a partition on ubuntu.?
Um I recently installed Ubuntu because my Windows Vista was changed to Windows 7 and I had no key for this. (Computer was given to me with Windows 7 cracked key) So i deleted the Windows OS and installed Ubuntu 11.10. Now I need to get my Windows Vista back which I have the iso for and a key, but I have no way to make a partition with Ubuntu I have tried everything. My computer is compaq Presario CQ50 , AMD, NVIDIA. Can anyone help please.?

---

### Post by Basher101 on 2011-11-19
The normal install does not come with a partitioning tool, now you have two choices to use one:

1. install Gnome Partition Editor (Gparted) with ```
sudo apt-get install Gparted
```
or
2. use the live CD/USB as that one comes with Gparted.

edit: also ***where*** is your linux partition now? you can make a screenshot once when you opened Gparted and upload it with your next post.

---

### Post by RaptorJay on 2011-11-19
> **Basher101 said:**
> The normal install does not come with a partitioning tool, now you have two choices to use one:

1. install Gnome Partition Editor (Gparted) with ```
sudo apt-get install Gparted
```
or
2. use the live CD/USB as that one comes with Gparted.

edit: also ***where*** is your linux partition now? you can make a screenshot once when you opened Gparted and upload it with your next post.

The computer is running Ubuntu there is no partition. I have gparted and I have no idea on using it. Windows no longer exist on this computer.

---

### Post by Basher101 on 2011-11-19
it is quite easily to use Gparted.

When i asked about where your partition is, thats only to verify that its at the beginning, assuming you wiped windows and everything. For windows it is crucial to be at the beginning of the disk, so if you haven't done much configuring and installing on linux, just delete the partition, install windows and reinstall linux so there are no problems with grub afterwards.

edit: before installing linux you should then check on windows how much fragmented your disk is and defrag before shrinking partitions in windows to free up space for *linux.

*note: the windows disk management tool only lets you free up approx ~50% of the total disk space you have (example, you have a 100gb HDD, you will be able only to free up 50gb and if you want more you must use Gparted for more adjustments).

---

### Post by RaptorJay on 2011-11-19
> **Basher101 said:**
> it is quite easily to use Gparted.

When i asked about where your partition is, thats only to verify that its at the beginning, assuming you wiped windows and everything. For windows it is crucial to be at the beginning of the disk, so if you haven't done much configuring and installing on linux, just delete the partition, install windows and reinstall linux so there are no problems with grub afterwards.

edit: before installing linux you should then check on windows how much fragmented your disk is and defrag before shrinking partitions in windows to free up space for *linux.

*note: the windows disk management tool only lets you free up approx ~50% of the total disk space you have (example, you have a 100gb HDD, you will be able only to free up 50gb and if you want more you must use Gparted for more adjustments).

Thanks bro, do you have any kind of tutorial which I can follow on ow to to delete my Linux.? I don't wish to mess up..

---

### Post by oldfred on 2011-11-19
Some info on gparted:
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

You can install Windows after Ubuntu, but you have to install it to a primary NTFS partition with the boot flag.

These are really old instructions. After any Windows install, you have to reinstall the grub2 boot loader to the MBR.

Older but discusses the issues, reinstall grub2, not other alternatives:
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)
[https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu)


How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

