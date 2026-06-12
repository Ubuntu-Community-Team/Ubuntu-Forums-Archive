---
title: "Vista + Ubuntu 9.04 Install Questions"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by jimc52 on 2009-04-25
I have a fairly good computer I rebuilt a few months ago.  I am going to detail some of the hardware here so that anyone who reads this and knows about specific problems can let me know.

My GOAL:  Dual boot Vista and Ubuntu

Past Problems:  I have tried unsuccessfully, on prior computer builds, to install prior Ubuntu editions.  I do NOT have an IDE drive...and for some reason, Ubuntu seems to have a big problem recognizing SATA drives.  What do I do to resolve any SATA drive issues so I can get Ubuntu to install and NOT destroy my Vista operating system?

1).  My hardware:  Intel Q9550, Asus P5QC motherboard, 8 Gigs PC3200 DDR2 800 Mhz RAM, nVidia 9800 GTX+ overclocked card.  I only have SATA drives, NO IDE types.  I have five hard disks, all disks only have ONE primary partition each.  My primary is a 1 teribyte (currently, I have 871 Gigs free).  Three other SATA's, 500 gigs each, and one older external USB drive for a backup I use only for Vista.  I also have two Pioneer CD/DVD burners.

2).  I currently have Vista Home Premium 64 bit installed on the Primary disk and I do NOT want to loose it.

3).  What do I do to prevent my Vista boot loader from being destroyed? I don't want LILO, I would prefer GRUB.  I don't want to screw this up.  I need your advice on how to do a correct install, including any pitfalls.

4).  Can I boot Ubuntu from OTHER THAN the primary hard drive?
I would prefer to leave my Vista hard disk alone.  I have plenty of hard disk space on at least 3 other mainly unused hard disks.
They are ALL SATA drives.  I would like to run Ubuntu on one of these.  How do I tell the installer to install on one of the other drives?  Does GRUB have to reside on the MBR of my primary drive even IF I want to install Ubuntu to a completely different hard disk?

5).  How many partitions must I have to install Ubuntu correctly, dedicated only to Linux?  Does one of the partitions HAVE to be on the primary drive (where I do not want it?).

6).  Does Ubuntu include the nVidia graphics drivers for my card
or do I have to mess with the driver from nVidia?  I especially do not want to have to mess with the graphics driver - I just want to set this up and get it done.

7).  Is CUPS the main driver for printers?

8).  I have prior Linux experience, with Fedora Core, SuSE...but its been a while. I really would like to try Ubuntu, but I am leery of screwing up my Vista operating system.  

Your help in this would be greatly appreciated, thank you.

---

### Post by lisati on 2009-04-25
2) If you're worried or nervous, make a backup, and make sure you know where your installation/recovery disks are. Keep an eye open for recovery partitions if they're there, and check out making a backup.... Can't say it too often: backups can be your friend.
3) Ubuntu uses Grub by default.
4) Yes: point the installer's partitioner at the drive/partition you want to use. *Be careful to read the options carefully before committing yourself.*
5) One option is to free up some disk space on one of your drives and tell the installer to use the "Guided: use largest continuous free space" option


7) Unless I'm mistaken, cups is the main printing system on my machines.

---

### Post by sloppyc on 2009-04-25
Here's what I do:

Install Vista first.

Google "EasyBCD".  Download and install it in Vista.

Install Ubuntu.  While installing Ubuntu, during the partitioning part, specify that you want separate / (root) and /boot partitions (I also have a separate /home partition, but that's another discussion).  

At the final step in the Ubuntu installation, you'll see an "Advanced" button. Click it.  You do not want to install the Ubuntu bootloader (GRUB) to the MBR (master boot record), instead, tell it to install GRUB on your /boot partition (eg. /dev/sda3).

Reboot.

You won't see an option for Ubuntu, just the standard Vista bootloader.  That's okay.  Remember EasyBCD?  Run it once you're logged into Vista.  In there, you can add an option to Vista's bootloader to load up Ubuntu's GRUB loader (you may have to user your intuition a little here to figure out which partition to select, but it's not too hard to work out if you paid attention to how your partitions are set up).  Add it, save it, you should be fine.  You'll have an Ubuntu option under Vista in Vista's bootloader.

I've had it running like this for well over a year now, it's great.

---

### Post by Euphorion on 2009-04-25
Hallo

I too have Ubuntu and Vista running on the one machine, I too did more of less the same as sloppyc. I have a laptop with 2 SATA disks each 500GB. On the first primary Disk Vista along with its recovery partition is installed, exactly as the machine was supplied, I did no changes to this disk at all.

I then installed Ubuntu on the second disk in 2 partitions a boot partition and a swap partition. During installation I made sure that Grub is installed on the second drive NOT on the primary Vista drive. After Ubuntu install and reboot, you see no Grub or Ubuntu, Vista Boots. Here Download and install Easy BCD, let Easy BCD detect Vista and Ubuntu and configure according to your needs. Thereafter you get a boot mananger in which you can select either Vista or Ubuntu. Works fine now for over 1 year with Hardy, Intrepid and since 12 Hours with Jaunty.

One small restriction, should you put Vista into Hibernate mode, then upon restart Vista will be immeadiatly booted, I do not get the boot menu.

In order to backup the whole lot in one foul swoop I use Acronis und Vista. I only use Vista in conjunction with my Video Camera because all the supplied software is windows only. Otherwise no real use for Vista.

Hope it works for you

---

### Post by pparks1 on 2009-04-25
I cannot say that I have experienced any problems with Ubuntu recognizing SATA drives for at least the last 4 releases....perhaps even more.

---

### Post by jimc52 on 2009-04-25
Thanks everyone for your contributions to my questions.

---

