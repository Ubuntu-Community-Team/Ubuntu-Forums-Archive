---
title: "Unable to partition my HD (New Install)"
date: 2008-08-26
forum: General Help
---

### Post by gonthrax on 2008-08-26
After running Ubuntu for a while on my Dell laptop I switched over to a Slax based distro, I am loving it so today I decided I would install Ubuntu Fiesty on my desktop.  I chose Ubuntu over Backtrack 3 for my desktop because well, I don't need all the security and testing tools BT3 has and being a noob it took me longer then usual to install some programs on BT3 because of having to get various dependencies etc.  The experience I had with Ubuntu on my laptop was very user friendly so I decided to give it a go on my desktop.

Anyway, down to the issue.  I backed up some of my favorite media from my windows install on a blue ray disk I had laying around and jumped in.  I WAS going to set up a dual boot system but after Windows wouldn't let me run defrag (due to some issue with "chkdsk being scheduled to run blah blah" and chkdsk never being able to actually work) I decided to nuke it.  Format the whole thing, start out fresh with 300gigs of space.  Sounds good right?  That's what I thought too...

So I fire up my live CD, had some display issues on my TV so I plugged in my old CRT, not a big deal I can get the display setup after the install.  So, up and running on liveCD, time to install.  I run the installer and start setting up my partitions.  The first issue I ran into in manual were errors of "cannot end before start" which kind of confused me because I tried a few different sizes, anyway I finaly got a setup that worked and I liked.  Onward to installation...  

When the installer starts setting up the file system I get an error.
"The creation of swap space in partition 3 of SCSI1 (0.0.0) (sda) failed.

So I tried guided auto install use all space.
"The creation of swap space in partition 2 of SCSI1 (0.0.0) (sda) failed.

I tried a few other partition setups with the same error just different partition numbers depending on how many others I had.

I tried installing with no swap (not great I know but I was desperate at the time and could set it up later)
"The ext3 file system creation in partition #1of SCSI1 (0.0.0)(sda) failed."
  
So I have restarted several times, same errors.  
Gparted shows my entire HD as unallocated, when I try to set a disk label it tells me "error while setting new disklabel"

Soooo, I start poking around with fdisk.

fdisk -l gives no output
fdisk -l /dev/sda1 gives "Cannot open /dev/sda1"
fdisk -l /dev/sda gives the same
fdisk -lu no output
fdisk -l /dev/sda2 or sda3 gives no output

I will copy and paste df output in a moment because I'm posting from my laptop.
**edit** here is the df output
```
ubuntu@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
tmpfs                  1037352     33788   1003564   4% /lib/modules/2.6.20-15-generic/volatile
tmpfs                  1037352     33788   1003564   4% /lib/modules/2.6.20-15-generic/volatile
varrun                 1037352        96   1037256   1% /var/run
varlock                1037352         4   1037348   1% /var/lock
udev                   1037352       136   1037216   1% /dev
devshm                 1037352         0   1037352   0% /dev/shm
tmpfs                  1037352        16   1037336   1% /tmp
```


At one point after I restarted neither gparted nor the installer detected my HD.  After another restart I started gparted and it showed file systems!!  I had a sda1 unformatted, a swap and another partition I do not remember the name of.  I tried formatting sda1 to ext3 but after an amount of time and HD led activity that led me to believe it was formatting it gave an error something along the lines of "You're screwed I can't create what you want me to create"
I restarted a few more times and saw the same file system in gparted but I didn't do anything with them, I jumped directly to the installer and tried to do an auto partition install.
After sitting at formatting partition #1 for quite some time I got the error "The attempt to mount a file system with type ext3 in SCSI1 (0.0.0) partition 1 (sda) at / failed"

So now I am frustrated, I tried booting a Gentoo live CD I had laying around, it does not detect my disk at all.

The desktop is:
Sony VAIO VGC-RC310G
Dual-core 3.2 GHz Intel Pentium D 940 processor, 300 GB hard drive, 2 GB RAM
300 GB (SATA) hard drive

If there is any additional info you need please ask and I will provide.  

As I said earlier I am pretty new to Linux but I do know my way around somewhat, I defiantly do not care about any data on the disk any more and would simply like a functional OS (not windows because A. Sony was nice enough to not include a Windows CD and B. Well, I want to run Xnix)

I have a feeling I have killed my MBR some how, perhaps formated the sector it is stored in?  I'm really not sure were to go from here so any help is appreciated, I like my computer to work not be a large paperweight.

Thanks,

---

### Post by gonthrax on 2008-08-26
Update
Tried running cfdisk

"FATAL ERROR: Cannot open disk drive"

Seems with no disk label it's hard to do anything, to bad gparted doesn't want to let me make one :<

---

### Post by gonthrax on 2008-08-26
Well I have no idea what the problem is/was but I think I'm on my way now.

I was trying several tools on a Gentoo rescue disk I had which made me restart after they failed to find my hard disk.  Anyway long story short one of the times I restarted I walked afk and booted into the normal kernel of the rescue disk (the same one that didn't see my HD before) so I fired up gparted just to see and it saw my disk.  I was able to format an ext3 partition and a swap partition.  I rebooted into Ubuntu liveCD and I'm now 59% of the way through copying files in the installation process, my main partition has been formated again so I think I'm golden.

Like I said I have no idea what the issue was, nor was I able to make any changes (to my knowledge) with the Gentoo disk before it saw my HD.

---

