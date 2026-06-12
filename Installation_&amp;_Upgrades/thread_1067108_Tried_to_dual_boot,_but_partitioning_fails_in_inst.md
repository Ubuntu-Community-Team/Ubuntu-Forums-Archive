---
title: "Tried to dual boot, but partitioning fails in install"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by shateredsoul on 2009-02-11
Hi Everyone,

I'm new to Linux, and tried out wubi and loved it!  I uninstalled wubi to try and dual boot my machine.  Now i'm just trying to dual install it into my laptop (dell xps m140).  I burnt a ubuntu install cd and made my computer boot from the cd.

It goes smoothly until I have to resize my partitions.  I chose the top choice, the guided partition.  Slide the bar to give Ubuntu about 35 gigs and the rest to windows xp...

then a box pops up with a bar and it says "resizing partition" 

Shortly after it says, "An error occurred while writing the changes to the storage devices" and it skips to the next step.  

Does anyone have any idea what is going on? Is there anything I can do through windows xp to fix this install?  Should I just create the partition from Windows XP?

---

### Post by unixeducation on 2009-02-11
Make sure you have enough space free on the existing Windows partition. If there isn't, the resize operation will fail.

---

### Post by avtolle on 2009-02-11
Also, defrag your Windows installation before attempting to resize it.

---

### Post by shateredsoul on 2009-02-11
Ok I will try defragging, but I definitely have enough space.  I have 54.7 gigs free in my c drive.

---

### Post by shateredsoul on 2009-02-11
Thank you for the advice.  If that doesn't work is there any program that I can use on windows xp to partition my hard drive?

---

### Post by Mark Phelps on 2009-02-12
Since you're using Windows XP, download and burn a GParted LiveCD, and boot using it.  It will allow you to resize the Windows partitions as much as you want, and create any new partitions you want.

The CD ISO image can be downloaded from the following link:

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

### Post by unixeducation on 2009-02-12
This whole process will be a lot easier if you download the Ubuntu 32-bit ISO image and install from it.

---

### Post by bribera on 2009-02-12
@unixeducation -- check again; shateredsoul *is* installing from the ubuntu install cd:

> **shateredsoul said:**
> I burnt a ubuntu install cd and made my computer boot from the cd.

That said, I'm having the same issue.  I'm giving my proposed Windows partition plenty of free space, yet I get the same "error occurred while writing..." message when using graphical installer.

I attempted to resize using the -alternate iso, and the resizing process hung at 0% for long enough that I gathered it was never going to complete.

I'm experiencing this with xubuntu images, although I'd bet money that the installer code is unchanged between the different flavors.  Anyone know how to work around this?

---

### Post by unixeducation on 2009-02-12
Sorry about my confusion :). With regard to this portion of your post:
> I attempted to resize using the -alternate iso, and the resizing process hung at 0% for long enough that I gathered it was never going to complete.

I've seen repartitioning take up to an hour to complete, and it always stayed at zero percent until it was complete for me.

---

### Post by Mark Phelps on 2009-02-13
Look, I know that Ubuntu includes GParted in its installation routines -- but the latest in Intrepid is 0.3.8 -- and the GParted LiveCD is 0.4.1.

I've had better experience using the GParted LiveCD, and it's newer than Ubuntu -- so I recommend using that.  Also, you're not inside an installer while you're using it.

But ... it CAN take a LONG time to resize partitions because it goes through several steps, including a complete TEST read of the entire partition before it does anything.  I've had it take nearly an hour on a small (10GB) partition.  So be prepared for it to take a LONG time on a large partition.

Also, you have the option of seeing the details for each of the operation steps, which shows you that it is making progress as it goes.

---

### Post by bribera on 2009-02-14
Well, I figured out my issue at least -- although not definitively; that is to say, I can't be completely confident that any of the steps I did were necessary or truly helpful.  But my installation is now working :D

Here's what I changed prior to my successful installation attempt:
[LIST=1]
[*]Forced Windows to run chkdsk in fix mode on reboot (ie, chkdsk /f from cmd).
[*]reduced Windows' pagefile size to ~250mb.
[*]reduced Windows' restore snapshot size to 1%.
[*]After chkdsk, defragged the drive a few times.
[/LIST]

Someone on some other thread (which I have lost, so unfortunately I can't credit them) suggested that the presence of bad sectors on a drive might negatively affect the resize operation. That seems plausible enough to me, although chkdsk didn't appear to repair anything on my drive when I ran it. Still good to be safe.

Conventional wisdom / Windows mythology pointed me to the  last three, arguing that the defragging the drive makes less work for the resize operation (ie, needing to move fewer files into the forward partition) and therefore presents less of a failure vector. The pagefile and restore snapshot are targeted because they are typically large contiguous files that Windows will refuse to move when defragging.  Again, this information is dubious at best, but may produce results. You can always up the pagefile/snapshot size afterward (although personally I like to keep my working set well below the physical RAM on my machine -- contrary to popular belief, swapping is *slow* and only performant when you need to accomplish a ton of memory-hungry tasks at once. Generally not a desktop/gaming scenario).

I still used the xubunutu-alternate install CD (I had trashed the graphical installer CD by then, otherwise I would have tried it) -- this time, the initial resize operation took *a few minutes*.  Last time, I was working on my laptop for an hour or two while it hovered at 0% or gave me the "error occurred" message, these errors respective to whether I was using the graphical or alternate installs.

Hope this helps someone in the future!

---

