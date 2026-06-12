---
title: "Please Help!! Hdd problem"
date: 2010-09-05
forum: Hardware
---

### Post by Lexess on 2010-09-05
I need some help. I have fully formatted my hdd and installed ubuntu. I used the disk utility and gparted. All the information I had on the hdd including the recovery partition is gone.

I need a way to install windows either XP or Vista and I can't successfully do it. 

I need some help on how to properly format my hdd through Ubuntu so that I can install windows on it. Since I fully formatted it, there is no boot information or anything.

---

### Post by em3raldxiii on 2010-09-05
First off, relax, hehe ... you aren't the first person to want to go through this process.

As you are discovering, Linux is smart ... it knows what to do with a hard drive if there is already a Windows system on it; Windows, however, is not so bright ... if there is another OS on there, it tends to get upity and want to remove the whole thing.  But it's actually fairly easy to do.

First, I would suggest creating a large partition on your hard drive that is formatted NTFS using gparted.  You can sudo aptitude install gparted if you don't have it currently installed.

Second, you should be able to install Windows using your installation CD and choose the appropriate drive to install it to.  Make sure you pick the right one!

Third, during the install, Windows will over-write your existing boot record, so the system will always automatically go into Windows.  You now need to use your Ubuntu CD in "live" mode (I think it's called "Try or Install Ubuntu" or something.  With that running, you need to re-install GRUB which is the boot loader that will allow you to pick windows or ubuntu.

Note:  there are occasionally configuration options that you will need to mess with in order to make the WIndows boot point to the right location.  you can search the forums, or post here.

Finally, if I missed the boat on what you are actually doing, my appologies :D

---

### Post by Lexess on 2010-09-05
Thanks for replying but the information doesn't help me.

I tried leaving a big NTFS chunk. There are no other OS installed on the drive except ubuntu which is on an extended partition between swap and ext4. The rest is an empty NTFS partition.

Windows XP says it can't detect any drives and the Vista DVD is ignored.

Is there a way to run the vista installer through ubuntu?

---

### Post by cdenley on 2010-09-05
AFAIK, you can only install windows by booting to its installation CD. If it does have an upgrade installer, it's not going to run in Linux, even if you use wine. You have to boot to the windows disc. You might need to change the boot priority in your BIOS menu, or select your DVD-ROM from a boot selection menu. If you need help with your windows installer, this might not be the best place to find it.

---

### Post by Lexess on 2010-09-05
I tried that with no luck. Windows XP says it can't find any installed drives.

I need help properly formatting and partitioning the hard drive in Ubuntu in order to run windows.

Thanks

---

### Post by jcolyn on 2010-09-05
I know others will disagree with me but the easiest way to get Windows installed is to first backup any files you want to keep either to an external drive or CD.

Next download the CD version of superfdisk here [http://www.ptdd.com/manual2.htm](http://www.ptdd.com/manual2.htm) and burn the iso to a CD.

Boot up on the CD and delete all partitions (yes this will delete Ubuntu) then format the entire drive fat 32. Takes less than 1 minute. Just click yes to the error messages at the start.

Now install Windows and update and add any software you need/want. If the install sets a recovery partition, delete it and merge that partition into Windows (see next paragraph).

Now right-click my computer and choose manage disk or partition or something like that and shrink the Windows partition. Usually you'll want to give half of the drive to Windows.

Now you are ready...

Start up the Ubuntu install and at the partition setup choose to run side by side or manually partition yourself using the free space but do not delete the Windows partition. Once install is complete grub will detect both OS's and at bootup will give you the option to dual boot Ubuntu or Windows.

No editing of grub needed..

---

### Post by Lexess on 2010-09-06
Thanks for the detailed description.

I've already tried a similar method. I have several bootable partition managers as well as a windows utility boot cd where I have access to partition the hard drive without an OS. I reformatted the whole drive before with Fat32 and I tried NTFS. Still no luck with windows xp because it can't find any hard drives. 

I'm guessing its Windows XP that's the problem. After partitioning several times, I had problems installing Ubuntu again. Eventually I got it to work.

I'll have to try installing Vista to see if it makes a difference.

---

### Post by jcolyn on 2010-09-06
If you can't get XP to install from the CD check the bios to see if the CD is set to first boot. If you still can't get it to go first do a drive surface scan with one of the utility CD's. If the drive checks out with no bad sectors go here [http://michaelstevenstech.com/cleanxpinstall.html](http://michaelstevenstech.com/cleanxpinstall.html)

---

