---
title: "Need help installing ubuntu. (read post for issue)"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by paskowitz on 2009-05-06
In short I think I need help installing ubuntu to access my HDD because Vista got corrupted on my PC. Long version:

Sit rep: (vista 32bit) Installing game, screen froze, turned off PC, gets to MS loading bar, blue screen flickers, startup repair does not work, does not recognize OS (even with disc), did HDD check, HDD is ok, [Dell]("http://forum.notebookreview.com/autolink.php?id=168&script=showthread&forumid=1049") thinks the OS is corrupt[IMG]http://forum.notebookreview.com/images/smilies/eek.gif[/IMG] . Now I know I can just wipe my computer and reinstall the OS but I really need all my data because a lot of it relates to school work and finals are coming up and my external HDD is also bust not to mention the 100gb of music.

Dell wants to charge me $120 to do a parallel installation of Vista and then back my data to an external HDD (I feel like just breaking my computer and sending it to Dell... ugh!). My dad's PC guy says this is stupid and wants to charge me "a couple hundred $'s" to get all my data off with a better method. My friend says they are both clowns and I should just do a dual boot with linux and, back up my files from linux and then wipe my PC. My dad's PC guy then says that this is not guaranteed and that his "special software" is garenteed to work. (I feel like he just wants my money... which he probably does.)

Who is right? I know there are a lot of undefined variables here that may affect my situation but I am no tech wiz but my friend sounds like he is making the most sense thus my being here.

If I install linux will I be able to access my HDD? Is there a thread that details how to do a dual boot with linux (ubuntu)? More specifically how to do it from a CD/flash drive/ What are the risks involved?

Thanks for your support.

---

### Post by rocketwings on 2009-05-06
i'm no expert, someone please correct me if i'm wrong

just get a live cd and run ubuntu off of that 
use ubuntu to copy the files onto an external storage device
i would avoid messing with vista

just my common sense

---

### Post by Mark Phelps on 2009-05-07
OK, here's a typical sequence for dual-boot:
1) Launch Vista, use Disk Management tool to shrink OS partition
2) Insert LiveCD, selected unpartitioned space, install Ubuntu
3) Install GRUB to MBR -- will add stanza to GRUB for Vista
4) Reboot and have menu for both OSs now.

Problem is ... you can't boot into Vista to do 1), so you'll have to boot from a Linux CD (Ubuntu or GParted) to use the partition manager to shrink the Vista OS partition.  That runs the risk of corrupting the Vista OS, which could very well prevent you from mounting it once you're in Ubuntu.

So, if you really want to replace Vista with Ubuntu, what I would advise is that you do the following:
1) Boot from Ubuntu LiveCD
2) Ensure that the ntfs-3g package is installed in Ubuntu, if not, install it through Synaptic.
3) If the external drive you'll be using to save the data is NTFS, install the package ntfsprogs from Synaptic.
4) Plugin an external drive.  Icon should appear on desktop
5) Mount the Vista OS drive using a terminal
6) Copy the files you need from the Vista OS drive to the external drive
7) When done, unmount the external drive by right-clicking on the desktop icon.
8) Unmount the Vista OS drive through a terminal
9) Reboot the machine using a GParted LiveCD (this ensures no partitions are mounted)
10) Remove all the partitions from the drive
11) Reboot using the Ubuntu LiveCD and install Ubuntu to the whole drive

---

