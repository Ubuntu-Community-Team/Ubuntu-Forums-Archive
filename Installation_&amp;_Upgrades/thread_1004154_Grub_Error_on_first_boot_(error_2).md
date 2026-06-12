---
title: "Grub Error on first boot (error 2)?"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by ukulele_ninja on 2008-12-06
I just got done installing ubuntu for the second time and have reached the same point both times.

After the installation is completed and the system restarts, I get 'Error 2' while the Grub is trying to load. Previously, I had LinuxMCE installed without any errors at the grub and installed Ubuntu over the same partition, could it be a hangup from the old linux install? 

Any ideas how to fix?

---

### Post by neverkn0wsb357 on 2008-12-06
ive gotten an error 2 in the past, if i'm not mistaken it means that supposedly theres no Linux installed. but if youre sure that it installed alright then the next thing i can think of is that you installed Grub on the standard partition and it isnt the partition where Linux is, the only case where i think that would occur is if you have two hard drives and you install linux on one and grub on the other

---

### Post by ukulele_ninja on 2008-12-06
Ill try it again but I was certain I had done it correctly, I do have multiple HDD's but I thought I had chosen the correct one.

Ive got the time, never hurts to give it another try I suppose lol

---

### Post by ukulele_ninja on 2008-12-07
Just reinstalled, rebooted and got the same error. What the heck is going on here??

---

### Post by ukulele_ninja on 2008-12-07
I can boot the livecd without issue (on it right now) but I cant get passed the grub error. Please anybody help me out on this one? :(

---

### Post by ukulele_ninja on 2008-12-07
Just to verify, I have followed the steps listed here > [https://answers.launchpad.net/ubuntu/+question/7137](https://answers.launchpad.net/ubuntu/+question/7137) to no avail. Also, I have used Gparted to delete everything on the hard drive and tried to ubuntu format the unallocated space.

Still no avail. Is it possible my MoBo is incompatable? I have the Asus M2N-Plus

---

### Post by falcon61102 on 2008-12-07
Could you post the end portion of your menu.lst?  You will need to mount the partition with Ubuntu on it and then go to /boot/grub/menu.lst on that partition.

Also, post the results of the following command:
```
sudo fdisk -lu
```

That will list your partitions.

---

### Post by ukulele_ninja on 2008-12-07
Literally just found a temporary fix for the grub issue. The motherboard I have had an option in the bios that enabled an 'ASAP' drive that has something to do with Vista ready Boost. I disabled that and it got past the Grub error, but now I have a screen that says: 

Posting this in a new thread as well-

'Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
     -Check rootdelay= (did the system wait long enough?)
     -Check root- (did the system wait for the right device?)
-Missing Modules (cat/proc/modules; 1s /dev)
ALERT! /dev/disk/by-uuid/0b74cbf5-f202-43cc-8484-7ea539dd0573 does not exist. Dropping to shell!


BusyBox ve1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built in commands.

(initramfs) _[prompt here]

I wouldnt even know where to begin addressing this one...

---

### Post by falcon61102 on 2008-12-07
It looks like your system is looking for a partition and can't find it.  Post the results of the following two commands:
```
sudo fdisk -lu
blkid
```

The first one is going to list info about your partitions, the second command will list the UUIDs for your partitions.

Also, if you could post the contents of your fstab by running:
```
gksudo gedit /media/disk/etc/fstab
```

EDIT: Need the fstab from the HD partition.  Updated code, be sure to replace /media/disk/ with the appropriate mount point for your root partition.

---

### Post by ukulele_ninja on 2008-12-07
> **falcon61102 said:**
> It looks like your system is looking for a partition and can't find it.  Post the results of the following two commands:
```
sudo fdisk -lu
blkid
```

The first one is going to list info about your partitions, the second command will list the UUIDs for your partitions.

Also, if you could post the contents of your fstab by running:
```
gksudo gedit /media/disk/etc/fstab
```

EDIT: Need the fstab from the HD partition.  Updated code, be sure to replace /media/disk/ with the appropriate mount point for your root partition.

Getting ready to do these, what is my mount point?

---

### Post by ukulele_ninja on 2008-12-07
ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="0b74cbf5-f202-43cc-8484-7ea539dd0573" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="2585d14b-5a2a-4781-b72c-2acb555dea13" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
ubuntu@ubuntu:~$ 

and

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdfbcdd0b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   299805029   149902483+  83  Linux
/dev/sda2       299805030   312576704     6385837+   5  Extended
/dev/sda5       299805093   312576704     6385806   82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by danlutz on 2008-12-21
Hey did you find out how to fix the problem. I have the issue with grub can't find the partition. 

All that I'e found that fixes the problem in ubuntu is to add rootdely=130 to it at boot time but I would like to fix the problem.

thanks

---

