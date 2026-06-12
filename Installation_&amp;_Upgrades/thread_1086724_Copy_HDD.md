---
title: "Copy HDD"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by quantum80 on 2009-03-04
I have 2 HDD's

#1 Debian 160GB
#2 Ubuntu 40GB

I have decided that I want to keep Ubuntu and want to copy all of it to HDD#1.  I have everything customized the way I want it. Both drives are independent of one another, I can remove either hard drive from the system and boot from the remaining.

Is their anyway for me to copy my entire Ubuntu installation directly to the bigger HDD?  I don't want to lose all of my settings.

Thanks.

---

### Post by albandy on 2009-03-04
to backup entirely a disk do this:

boot with the live cd
mount the first disk
mount the second disk

open a terminal
cd /mountpointofthefirstdisk
sudo tar zcvfp /mountpointoftheseconddisk/backup.tgz ./

---

### Post by quantum80 on 2009-03-04
It appears I'm making an entire copy of Ubuntu and saving it to the Debian drive per your instructions.  But how does this help me get rid of Debian?

Do I need to install ubuntu with the live cd on disk 1 to wipe out debian first, then use your commands to bring my backup over to drive 1?  And if so, how do I then restore the archive?

Thanks.



> **albandy said:**
> to backup entirely a disk do this:

boot with the live cd
mount the first disk
mount the second disk

open a terminal
cd /mountpointofthefirstdisk
sudo tar zcvfp /mountpointoftheseconddisk/backup.tgz ./

---

### Post by OffAxis on 2009-03-04
you can boot off the LiveCD and use gParted to wipe out the Debian install.
I don't remember if there's a 'Copy' or 'Clone' function in there. There might be.

If not, you can download some hard drive utilities from your hard drive manufacturer that can clone it for you.

The ultimate boot cd has a lot of them compiled for you in one spot:
[http://www.ultimatebootcd.com](http://www.ultimatebootcd.com)

or you can use the dd utility from the command line (it takes a while, though).
It does a bit by bit clone of the drive.
It has a lot of options so you might want to read up on it.
```
man dd
```

The simplest use is
```
dd if=/input/path of=/output/path
```

---

### Post by quantum80 on 2009-03-04
I went ahead and copied using the dd command from sda1 to sdb1.  There is also sda2/sdb2 and sda5/sdb5  one being a swap partition and the other being some other linux partition that installs by default.  Do I need to use dd on the other partitions as well, or just on the main partition as I'm doing now?

---

### Post by quantum80 on 2009-03-04
Ok, I pulled out the small hard drive and successfully booted Ubuntu on the new drive, everything is still the way it should be. 

I do have a problem though.  I copied 38gb from the old drive into the new drive.  The new drive is 160 gb.  However, when I look at in gpart,it shows as being nearly full (120gb filled) which is impossible b/c I copied from a 38gb drive which was only half full.

Also, when I look at the free space on the drive, it is showing 18 gb, exactly what the old drive was showing.  It's almost as if the system thinks i'm still running the 38 gb drive when I'm not.  Any way to let the system know there is more space available now?

---

### Post by jespdj on 2009-03-04
The dd command copies the content from the old drive to the new drive exactly, byte by byte. The partition on your new drive is now exactly the same size as the partition on your old drive - not the whole space of the new disk is used.

You can use a program like gparted to resize the partition on the new disk.

---

### Post by quantum80 on 2009-03-04
> **jespdj said:**
> The dd command copies the content from the old drive to the new drive exactly, byte by byte. The partition on your new drive is now exactly the same size as the partition on your old drive - not the whole space of the new disk is used.

You can use a program like gparted to resize the partition on the new disk.


That was my first thought also.  However, when I open up the partition manager, it shows my partition being 140+ gb in size with 120gb used and 20gb free.

---

### Post by quantum80 on 2009-03-04
Also, when I go to computer, and right click on my drive, it tells me 14 GB used, and 20 GB Free.

In partition manager, 120GB used, 20gb free.

---

