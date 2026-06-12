---
title: "Vista disappeared on dual boot system"
date: 2008-11-03
forum: General Help
---

### Post by sharondenscabbia on 2008-11-03
Hello

I'll start off with a bit of background. I've used vista ultimate for some considerable time on my laptop. A while ago, I decided I'd set it up so that it dual boots vista/Ubuntu 8.4 using the standard GRUB bootloader. To do so, I shrunk my main (C:\) partition by 4.58GiB (all it would let me at the time) to install Ubuntu on the now empty space. I was then using Ubuntu and occasionally vista with no problems for well over a month. I then noticed that Ubuntu 8.10 came out. Upon trying to update, I was told I didn't have enough space. 

I went back into vista, moved some data to another partition and defragged my C:\ drive, which allowed me to shrink the C:\ volume by a further 10GiB. I then intended to extend the Ubuntu partition by said amount, enabling me to update to 8.10!

Heres where the stupid bit comes...

As I am largely unfamiliar with Ubuntu, I downloaded the GParted partition editor. Messing around, trying to learn my way around, I seem to have set an MS-DOS disklabel. I've no idea what the HELL that means. However, the result of which, was the apparent disappearance of my vista partitions from the list on GParted. Upon bouncing my laptop, I got the infamous GRUB error 22, which I have previously encountered.

Last time, what I did to fix it, was re-install Ubuntu from the LiveCD on the "largest continuous free space" or something to that effect, so I repeated my action. On the plus side, I could then get onto Ubuntu. However, vista seems to have entirely disappeared from view. 

I used the vista boot disk to run bootrec /fixmbr on the command line (which should have fixed the boot sector so that it pointed at vista, I would have sorted out Ubuntu later). When I bounced it, I instead got a MISSING OPERATING SYSTEM error. I then went back into the vista command line, entered bootrec /fixboot. This then said it couldn't find vista. I ran bootrec /scanOs which returned 0 windows operating systems. 

So, yeah, it seems like my vista Os has gone, which isn't such a problem. Just reinstall, or do without, I'm more than happy with Ubuntu and Wine. However, it also seems like the contents of those partitions have gone too. I don't believe I wrote over them in re-installing Ubuntu, as GParted now says that the Ubuntu partition is still 4.58GiB. However, what was several partitions, is now claimed by GParted to be /dev/sda1, with 3.89GiB used and 103.31GiB free. Theres no way all that data could have been overwritten in such a small amount of time.

My questions are:
Is vista recoverable, or will I need to reinstall? Or, more importantly, can I get the data back from the vanished partitions?

Thanks,

Sharon

---

### Post by labrat256 on 2008-11-03
Wow, I've got a very similar problem. If you find an answer to it, please PM me...

---

### Post by dagrump on 2008-11-03
what file system is shown by gparted on /dev/sda1?
Much of the  old data can be recovered, it requires some effort, just depends on how important it is. Does it justify the effort.

---

### Post by TeXtonyx on 2008-11-03
When Vista is used to resize itself, then Vista is aware of its new
boundaries. If a Linux tool is used to resize a Vista partition then
there is more chance of an error in Vista realizing its information.
There may be a backup of your partition table that Testdisk can 
use. [http://www.howtoforge.com/data_recovery_with_testdisk](http://www.howtoforge.com/data_recovery_with_testdisk)

The Testdisk documentation describes its various capabilities.
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download) [free]

---

### Post by louieb on 2008-11-03
> **sharondenscabbia said:**
> ... I downloaded the GParted partition editor. Messing around, trying to learn my way around, I seem to have set an MS-DOS disklabel. I've no idea what the HELL that means... However, the result of which, was the apparent disappearance of my vista partitions from the list on GParted....
Is vista recoverable, or will I need to reinstall? Or, more importantly, can I get the data back from the vanished partitions?


disk label is anther name for the partition table. By writing a new disk label there is no way of knowing where partitions start or end. 

Before you do anything else to that computer get a [SystemRescueCd]("http://www.sysresccd.org/Main_Page") and run **testdisk. **That may get your vista partiton back. On the same CD is a program call **photorec **it has a good chance of recovering files if testdisk can't restore your partition table.

---

### Post by sharondenscabbia on 2008-11-04
> **dagrump said:**
> what file system is shown by gparted on /dev/sda1?
Much of the  old data can be recovered, it requires some effort, just depends on how important it is. Does it justify the effort.

Hello
Under /dev/sda1 gparted says ext3.

Some of the data, since my last backup, is certainly worth the effort!First, I'm going to try doing what louieb suggests. I'll tell you what happens.

Thanks,
Sharon

---

### Post by sharondenscabbia on 2008-11-09
Right! I finally managed to get the SystemRestoreCD working. Even though it is slow (repeatedly scanning my drive, at about 2 hrs a time, is frustrating!) it managed to do the job it was designed for, and did it well.

Well, I managed to save all of the data on my (old) second partition. The first partition however, was a lost cause. It seems the first 1/4 of the partition had been overwritten, and as a result, nothing seemed to be able to get the data from it. 

As most of my data with any value was on the second drive (the first was used primarily for applications) I decided to backup all the data I still had on an external drive and just reformat my drive with a 30GB Ubuntu partition, the same old 50GB NTFS partition for my data, and about 40GB left clear for vista, if I ever decide to put it back on.

Thanks all for your help,

Sharon

---

