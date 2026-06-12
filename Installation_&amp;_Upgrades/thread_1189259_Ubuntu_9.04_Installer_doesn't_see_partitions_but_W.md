---
title: "Ubuntu 9.04 Installer doesn't see partitions but Windows 7 does"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by drdoombot on 2009-06-16
Hello,

I recently attempted a dual boot installation of Windows 7 RC and Ubuntu (originally 8.04, now 9.04). I installed Win7, then installed 8.04, using gparted to make the various partitions. Everything seemed to be going smoothly and I even went through the tedious process of upgrading 8.04 to 8.10, then 9.04. Somewhere along the way I had trouble getting into Win7 and used the install disk to fix the MBR, then used the Super GRUB disk to get GRUB back and fix the boot entries.

(I installed Ext2IFS in Win7 at some point and wonder if that did anything to exacerbate my problem)

Here is where I am at now: selecting my Ubuntu installation brings me to a BusyBox shell. Editing GRUB has no effect. Trying to reinstall using a 9.04 LiveCD shows me a hard drive that is unallocated. I've spent the past 2 weeks getting my Win7 installation the way I want it and would hate to lose it.

My computer continues to load through GRUB. GParted doesn't see my partitions. Win7 doesn't assign a drive letter to my ext3 partitions, but I can still see the partitions in Drive Management. Why is it that Win7 can see the partitions but GParted can't?

What I'd like to do is reinstall 9.04 from the LiveCD using the ext3 partitions that are already there and without damaging my NTFS partitions. For clarity, here is what TestDisk shows for my HD's current partition structure:

```

1 * NTFS
2 P NTFS
3 P Linux
4 E extended
5 L Linux
  X extended
6 L Linux Swap

*=Primary bootable
P=Primary
L=Logical
E=Extended

```

In other words, my primary boot partition is NTFS, followed by a primary partition in NTFS for data, and then another primary partition in ext3 for Ubuntu. Then I have an extended partition for the rest of HD, containing a ext3 "/home" partition and a swap partition. Or at least this description was how I intended to set up the HD...

Any ideas on how to get GParted to see the partitions that Win7 sees would be appreciated.

---

### Post by merlinus on 2009-06-16
Perhaps you can be a bit more precise in describing exactly what is going on.  Does the problem occur at the partitioning screen during install?  Can you run from the live cd, and if so, post a screenshot of gparted from that?

You also might try the text-based alternate install cd.

---

### Post by drdoombot on 2009-06-16
Quite simply, the LiveCD installer shows device "/dev/sda" as unallocated: no partitions whatsover. The only option I have is to create a new partition table. However, I have a working installation of Windows 7 on this hard drive that I don't want to lose.

Windows 7 sees my partitions; GParted does not. The question is how to get GParted to see my partitions and install 9.04 to the ext3 partitions.

---

### Post by merlinus on 2009-06-16
Your response indicates that the partitioning screen did not give any options for selecting existing partitions.  What about posting a screenshot of gparted.

I assume you selected the manual option?

It also might be useful to burn the live gparted cd, boot from that, and see what shows.  It is a later version, with more features, than the one on the ubuntu cd.

You also might try the text-based alternate install cd.

---

### Post by drdoombot on 2009-06-16
I've attached a screenshot.

I'm currently burning the GParted livecd (0.4.5-2) to see if my partitions show up there.

I've already tried going into Windows 7 and deleting the ext3 partitions. In Win7, I now have 15gb of unallocated space on the hard drive, but as per the attached screenshot, Gparted sees the whole hard drive as unallocated.

---

### Post by merlinus on 2009-06-16
I wonder if it is not something about win7 and gparted....

What does this show:

```

sudo fdisk -l

```

---

### Post by drdoombot on 2009-06-16
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1175448d

   Device Boot      Start         End      Blocks   Id  System
ubuntu@ubuntu:~$ 

```

---

### Post by merlinus on 2009-06-16
So it is not only the installer that does not see win7.  The fdisk command *should* have shown partitions, but obviously is seeing none.

Is the hdd ide or???

Also, ext2ifs should show linux partitions with the drive letters you assigned when you installed it.

---

### Post by drdoombot on 2009-06-16
Yes, it's ide. I unplugged all of my other drives to avoid confusion.

---

### Post by merlinus on 2009-06-16
Why not install ubuntu onto one of your other hdds?

---

### Post by drdoombot on 2009-06-16
I frequently remove my other drives and plug them into external usb enclosures to move files to other computers.

So, it looks like I have no option but to use GParted and make a new partition table, erasing my Win7 installation?

---

### Post by merlinus on 2009-06-16
You could run testdisk to see if it can find your partitions.  It is possible that something went awry with the win7 partition and it does not conform to specs, but it might be repairable.

Starting fresh is always an option...

---

### Post by Cheesemill on 2009-06-16
This probably won't help (I'm clutching at straws here) but can you give us a screen shot of Disk Management in Windows so I can see what's Primary and what's in your extended partition.

Ta

---

### Post by twright on 2009-06-16
I have seen other people saying that partitions created in windows 7 are not shown by other operating systems although I did not see this myself. You could try using fdisk to create a new mbr without deleting data, I think it has this option.

---

### Post by drdoombot on 2009-06-16
Interestingly, TestDisk found my partitions instantly when run from Win7. From the Gparted LiveCD, it didn't see the partitions until I searched for them. Not that that helps me any...

I don't have a screenshot of Disk Management right now, but I can tell you that the ext3 partitions did NOT show up with the green outline the way extended partitions usually do.

---

### Post by merlinus on 2009-06-16
Another long shot, but did you try the alternate install cd, which is text-based?

---

### Post by drdoombot on 2009-06-16
I'd try the alternate install cd, if I had a CD to burn it too. I haven't purchased one of those in years (used my last one on the live Gparted disk).

In any case, I have a feeling that Win7 is making screwy partitions. I seem to remember having trouble installing Win7 on the NTFS partition made in GParted, and being forced to reformat it from within Win7's installer.

---

### Post by Cheesemill on 2009-06-16
There's a chance you can still save your Windows install although it's a bit long winded.

You'll first need to back up the Windows 7 partition on to one of your other drives (I reccomend CloneZilla) , then use gparted to recreate your partitions from scratch before installing Ubuntu first (or you could partition using the installer).

Then restore your Windows partition into the now hopefully valid partiton you created for it earlier.
You'll probably have to manually edit GRUB to be able to boot into Windows afterwards but this isn't too difficult.


Edit - Just noticed that your out of CD's for CloneZilla but you should be able to achieve the same thing by installing partimage whilst running the Live CD.

Edit 2 - Obviously  I'm hoping that CloneZilla or PartImage will recognise your partitions in the first place !!!!  If not then you may be able to run Acronis TrueImage from within Windows (I think they do a free trial).

---

### Post by drdoombot on 2009-06-17
Not a real solution but this is what I ended up doing:

1. Used GParted disk to set up all the partitions
2. Installed 9.04
3. Restored an image of my Win7 partition
4. Could not get into Win7, so used SuperGrub disk to fix it
5. At this point, could not get back into 9.04, even with SuperGrub, so reinstalled 9.04 again (three times in one day!)
6. Finally edited /boot/grub/menu.lst and everything is working!

...well, almost. Rollback RX got toasted by the image restore, so I need to reinstall that.

Anyways, I learned my lesson and I'll pass it on to whoever may be reading this; for dual-booting Windows 7 and Ubuntu, this is the correct order:

1. Make partitions in Gparted
2. Install Windows 7 first
3. Then install Ubuntu

Thanks to everyone for their help.

---

### Post by bcwilson on 2009-06-17
> **drdoombot said:**
> Not a real solution but this is what I ended up doing:

1. Used GParted disk to set up all the partitions
2. Installed 9.04
3. Restored an image of my Win7 partition
4. Could not get into Win7, so used SuperGrub disk to fix it
5. At this point, could not get back into 9.04, even with SuperGrub, so reinstalled 9.04 again (three times in one day!)
6. Finally edited /boot/grub/menu.lst and everything is working!

...well, almost. Rollback RX got toasted by the image restore, so I need to reinstall that.

Anyways, I learned my lesson and I'll pass it on to whoever may be reading this; for dual-booting Windows 7 and Ubuntu, this is the correct order:

1. Make partitions in Gparted
2. Install Windows 7 first
3. Then install Ubuntu

Thanks to everyone for their help.
I've experienced the same problem trying to install 9.04 as a dual boot with Vista. The partition window only shows a single unformated drive where I have four. Vista's disk manager sees all but my existing Ubuntu 8.x partition. My question is after you repartitioned your disk with Gparted and reinstalled W7, did the live CD install recognise your partitions?

---

### Post by Insidious311 on 2009-06-17
> **bcwilson said:**
> I've experienced the same problem trying to install 9.04 as a dual boot with Vista. The partition window only shows a single unformated drive where I have four. Vista's disk manager sees all but my existing Ubuntu 8.x partition. My question is after you repartitioned your disk with Gparted and reinstalled W7, did the live CD install recognise your partitions?
 
 
I would like to know this as well, I'm having a similar problem. There has got to be a better way than creating a back up image and then re-imaging everything. Someone has to have figured it out by now, I mean this has been a problem since 7.10 appearantly (I was trying to reinstall 7.10 , ran into this problem, and figured surely by 9.04 this would no longer be a problem.) :(

---

### Post by Mark Phelps on 2009-06-17
I do now that under some circumstances (sorry, don't know the specifics) that Windows 7, when installed to an empty drive and as the only OS, actually creates two partitions -- a regular NTFS partition and a special boot partition (for itself). 

Once you partition a drive, though, Seven doesn't create the special partition but uses the NTFS partition to hold its boot and loader files.

You said you installed Seven to a new drive by itself. Could be that the special partition was confusing GParted such that it was then unable to see the remainder of the drive.

---

