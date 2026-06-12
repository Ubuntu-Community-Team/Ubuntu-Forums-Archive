---
title: "will ubuntu be noticable?"
date: 2008-10-15
forum: General Help
---

### Post by reinaldistic on 2008-10-15
i want to install ubuntu but will it be noticable from my win xp  partition that another os is installed? i e like will it slow down, or say anything???

---

### Post by snowpine on 2008-10-15
Nope, Windows won't even know Ubuntu is there. :)

---

### Post by Sam on 2008-10-15
Yes it will be aware that an other OS is there. But it won't slow down XP for that. And without specific tools you won't be able to access the files in Ubuntu (but with a wrong manipulation you can mess the partition).

---

### Post by Elfy on 2008-10-15
> **snowpine said:**
> Nope, Windows won't even know Ubuntu is there. :)

Unless it's installed as wubi - in which case it will know it's there, but it shouldn't slow xp down. Wubi is though apparently marginally slower than when installed on it's own partition.

---

### Post by az on 2008-10-15
> **reinaldistic said:**
> i want to install ubuntu but will it be noticable from my win xp  partition that another os is installed? i e like will it slow down, or say anything???

If you would like to access the files you have on your Ubuntu system, you can install this driver for ext2-ext3 filesystem on Windows:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

Once you install that, Windows will notice your linux partition.  But it won't affect windows nor slow it down.

If you installed using Wubi, then the fs-driver will not allow you to see your Ubuntu filesystem.  It's not a separate partition in that case.

---

### Post by Dr Small on 2008-10-15
XP is sluggish by nature, over time. But the causes will not be from Ubuntu on the same hard drive..

---

### Post by TeXtonyx on 2008-10-15
In some of the newer laptops they are using a Linux OS chip that lets you connect 
to the internet to check email and browse about without having to wait 3 minutes for
the whole Windows OS to load. Ubuntu is about 2 minutes faster and Thunderbird,
my email client has nicer fonts on Ubuntu than on Windows. 

The thing is that it will be noticeable because the easy way of installing Ubuntu
puts grub in the MBR, so that XP will show up as a booting choice in that menu.
With about 10 minutes more work you can put grub into the Ubuntu boot partition.
Then XP boots from its own boot.ini and Ubuntu shows up as another choice. If
you screw up the Ubuntu partition you don't have fix anything to get XP to boot.

Another thing to do is carefully carve out 20 or 30 GB for the Ubuntu install to live in
before installing Ubuntu to the hard drive. Ubuntu is much faster on the hard drive
and if you run it from the live cd it takes as long as XP to get ready. The 
advantage of creating the partition for Ubuntu first is that you can choose "install
to largest unallocated space" from the Ubuntu live cd install to the hard drive.  A
few people report not being able to boot XP when they choose the live cd install
option of resizing the XP partition during (not before) the install to hard drive.
I'm recommending this method because it is safest for XP and for users who can
follow instructions. The default automatic way is much easier but not quite as safe.

----------------------------------------------------

[http://www.linux.com/feature/113945](http://www.linux.com/feature/113945)
Boot sector transplant ...

"And there you have it: a Windows machine that boots Linux as well. The advantages of this setup are:

    * The Windows configuration remains essentially untouched.
    * No changes to the Windows hard drive boot sector are necessary.
    * Removing Linux from the machine is simple: physically remove the Linux disk and remove the Linux entry from boot.ini under Windows.
    * Windows users have a tendency to reinstall the OS from time to time. If that occurs on this system, the Linux disk would be untouched (although you might not be able to boot to it until you copy the boot sector again and fix boot.ini).

While this configuration isn't ideal for everyone, it is a great way to add Linux to an Windows machine with minimal disruption of an existing Windows installation."

----------------------------------------------------

[http://forums.majorgeeks.com/showthread.php?t=108021](http://forums.majorgeeks.com/showthread.php?t=108021)

This shows how to use Bootpart, but you wouldn't follow the directions exactly.
I made an assumption that you might be sharing the computer. Another person 
will notice the least difference and have XP the most safeguarded this way. If
my assumption is wrong then my approach becomes less important. 

[http://theubuntublog.wordpress.com/2008/09/03/the-easiest-dual-booting-solution/](http://theubuntublog.wordpress.com/2008/09/03/the-easiest-dual-booting-solution/)
Explains how to use the free Gparted to resize your partition before doing the live
cd Ubuntu install. How much to shrink the XP partition?! Go to My Computer, right 
click on your C drive, go to properties and which shows you how much used space, 
and free space you have. You are going to use some of the free space
on the XP drive to make your Ubuntu partition. When you make the XP partition
smaller the free space gets converted into "unallocated" space (the live cd install
choice I recommend). Your XP free space (still part of XP and not unallocated)
should be 15% of your total drive size. So don't resize XP too much, although
Ubuntu needs at least 12GB. Ubuntu is going to be created on the unallocated
space, not the free space owned by XP so don't get the terms confused. XP can
use its own free space for storage; it can't use unallocated space without steps. 

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
This is a partition resizing tutorial with lots of pictures, though it is a bit old.

[http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron](http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron)
This is a pictorial guide that shows the Ubuntu live cd install to the hard drive.
*Do not* follow this guide step for step, especially step 4 of 7. Use unallocated.

---

