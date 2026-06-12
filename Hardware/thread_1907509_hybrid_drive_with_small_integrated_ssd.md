---
title: "hybrid drive with small integrated ssd"
date: 2012-01-11
forum: Hardware
---

### Post by r.stiltskin on 2012-01-11
I'm planning on getting a new HP Pavilion dm4t laptop.  The hard disk options include a "500GB 7200 rpm + 20GB SSD" "with Intel Smart Response Technology".  I'll keep Windows 7 that it comes with for occasional use, and set up dual-booting with Ubuntu as my primary OS.  The HP docs don't specify the manufacturer of the drive.  This drive costs an extra $150 over the base price of the laptop.

But I'm worried about the Intel "SRT".  Is it supported under Linux, or will I have to essentially ignore it & treat the drive as an ordinary HDD under Linux, or is even that likely to cause problems?  Are there any special issues with partitioning this kind of drive?


Now I just found that for just a slightly higher price I can buy a [Seagate Momentus XT Solid State Hybrid]("http://www.seagate.com/www/en-us/products/internal-storage/momentus-xt-kit/?cmpid=ppc-_-momentusxt-_-g-_-us-_-500_gb_ssd-_-b&gclid=CLrYl9HMyK0CFcfe4AodsE1QiA#tTabContentOverview") which Seagate claims "works with any laptop with any OS" and just pull out HP's standard drive.  Seagate's performance claims for this drive are impressive.  Anyone aware of anything wrong with that idea?  Have any problems been encountered with using the Momentus XT drive under Linux?

---

### Post by Mark Phelps on 2012-01-11
The WikiPedia page on this (see link below) doesn't fare well with non-Windows OSs.  I would not be surprised if Linux OS are not able to actually "see" the drive ...

[http://en.wikipedia.org/wiki/Hybrid_drive]("http://en.wikipedia.org/wiki/Hybrid_drive")

---

### Post by r.stiltskin on 2012-01-11
Yes, thanks, I already read that, as well as the wikipedia pages about [Smart Response Technology]("http://en.wikipedia.org/wiki/Smart_Response_Technology") and [Intel Matrix RAID]("http://en.wikipedia.org/wiki/Intel_Matrix_RAID").   I was just hoping that someone might have some more up to date "good" news.

I'll probably go with the Seagate solution, unless someone pops up with info that would discourage that (or a better idea).

---

### Post by Mark Phelps on 2012-01-12
One other thing I should mention is that laptops are notorious for NOT having their specialized hardware supported under Linux, the most recent case in point being the "hybrid graphics".  What I read on this most recently is that even Ubuntu 12.04 won't have native support for this.

So, you're going to jump into another "hybrid" technology solution?

Sure, it's going to work in Windows -- because that will come preloaded on the PC.  But, if it's anything like "hybrid graphics" it could be 6 months, to a year (or longer) before the Linux community has working drivers that support it.

---

### Post by r.stiltskin on 2012-01-12
No, it's not like that.  The Seagate drive doesn't need a special driver.  The OS sees it the same as any standard SATA drive.  The caching is handled internally in the hardware and firmware of the disk.  (See link in post #1.)

Actually I just found out that Seagate now offers a 750GB version with 8GB built-in flash cache for only $50-$60 more which according to [PC Magazine]("http://www.pcmag.com/article2/0,2817,2398337,00.asp") is considerably faster, so that seems a still better choice.

---

### Post by Mark Phelps on 2012-01-12
> **r.stiltskin said:**
> No, it's not like that.  The Seagate drive doesn't need a special driver.  The OS sees it the same as any standard SATA drive.  The caching is handled internally in the hardware and firmware of the disk.  (See link in post #1.)

Thanks for the update. 

It's good to know this is one new technology that we can use NOW in Linux -- without waiting months or years for working drivers to get written.

---

### Post by r.stiltskin on 2012-01-13
Hey Mark, still thinking about my new laptop plan.  I'm now looking into the question of moving the Windows7 from the original disk to the Momentus, which I'll have to do before installing Ubuntu.

I came across [this thread]("http://ubuntuforums.org/showpost.php?p=11222288&postcount=10") in which you wrote about Macrium Reflect -- which is great because it's been a long time since I messed around with saving/restoring Windows images & I'm not familiar with current utilities.

Will Macrium let me copy just the Windows System and C partitions over to a blank new drive & end up with a bootable Windows?  Does it create the MBR and partitions on the new drive, or will I need something else to do the partitioning first?


Update: I found this article on [replacing a Windows 7 hard drive]("http://www.winsupersite.com/article/windows-7/replace-your-hard-drive-using-free-windows-7-tools") using Windows Backup and a Windows system repair disk.  Is there any reason that Macrium Reflect would be preferable to this?

---

### Post by Mark Phelps on 2012-01-13
I've done essentially the same with Macrium Reflect (MR) ...

Image off the OS partition (and if there is a separate 100MB BOOT partition, as well) to an external drive.

IF you have the FREE version, use the option to create a Linux Boot CD.

If you have a drive adapater, connect up the new drive; otherwise, shutdown the laptop and replace the drives.

If you have two drives connected, simply Restore the image you just made to the second drive.

If you have only the new drive, boot from the Linux Boot CD and restore the image to that drive.

There have been times when the new drive wouldn't boot, so BEFORE you remove the old drive, if you have Win7, use the Backup feature to create and burn a Win7 Repair CD.  If the laptop doesn't boot after the image restore is done, boot from this Repair CD and run Startup Repair three times (yes, three times).

---

### Post by r.stiltskin on 2012-01-13
Sounds good.  Thanks.  I'll post back if there are any problems.

---

### Post by vinodkhare on 2012-06-26
I bought an hp dm4 laptop with the same hybrid drive. I'm trying to install ubuntu 12.04 on it but the installer cannot see any partitions. Did anyone else face the same problem?

---

### Post by r.stiltskin on 2012-06-27
No.  If you bought it from HP with the auxilliary SSD already installed, that is NOT the same as my setup.  I bought a laptop with an ordinary hard disk  and then  I *replaced* the hard disk that HP provided with a Seagate Momentus XT drive that I bought and installed separately.  The Seagate drive has a standard HD and an SSD integrated in a single unit with all of the support for the SSD caching built-in, so it appears to the OS the same as an ordinary hard disk.

You bought a laptop containing an ordinary hard disk plus a separate Intel SSD based on Intel's _proprietary_ "Smart Response Technology" (SRT).   SRT support is built into the Z68 chipset (on the motherboard) and depends on the Windows driver for that chipset.  As far as I know there is no Linux support for Intel SRT.

You can probably install Linux on your ordinary hard disk but then unfortunately you would get no benefit from the solid state drive.

---

### Post by rhlobo on 2012-11-23
Ive received a computer to use as my work station and it had the same issue of the hybrid drive and ubuntu's installation not being able to "see" it. It ends up I had to disable Intel Matrix RAID from within windows before trying to install linux, and after that was done everything went fine till this day. =)

Just to be clear, Ive kept windows on the machine in a dual boot setup and I am using the hybrid drive as a normal drive, because as it was said, the caching seems to be done internally on the hardware/firmware level.

---

