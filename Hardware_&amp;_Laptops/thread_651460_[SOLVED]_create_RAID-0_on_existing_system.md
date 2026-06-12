---
title: "[SOLVED] create RAID-0 on existing system"
date: 2007-12-27
forum: Hardware &amp; Laptops
---

### Post by a_posse_ad_esse on 2007-12-27
Hello, all.

I have a server set up that serves as a mythtv system among other things.  It has since come close to outgrowing its existing drive, and I have procured another disk.

Am I able to move to a RAID-0 setup without having to reinstall?  I see that it is possible with a RAID-1 situation as shown [here]("http://www.debian-administration.org/articles/238"), but that has the data spread throughout the system.  Is a similar thing possible using RAID-0?

Thanks

---

### Post by fazavon on 2007-12-27
I would think not. 

With Raid-1 all you need to do is copy the hard drive. 

What you are trying to pull off is spanning data across two drives, one of which is a live drive with data on it. I am not sure if it is possible just based on the sheer nature or a Raid-0 setup. 

If it does work, please and I think I speak for everyone when I say this **PLEASE** post how you pulled that off.

thanks

//j

---

### Post by jsully1 on 2007-12-27
You'll have to jump through a number of hoops - long story short there's no simple/straightforward way to convert it to software RAID. 
After a quick bit of googling I found [this, for an example](http://togami.com/~warren/guides/remoteraidcrazies/) of how difficult it seems.

It's worth noting that with hardware some cards have morphing abilities where it can preserve your data while it does the conversion.  Some nVidia RAID cards support this, as do some IBM xservers.

In any event I think you're crazy to consider RAID 0 - it's an accident waiting to happen :)

---

### Post by a_posse_ad_esse on 2007-12-28
I would normally agree with you about RAID-0, but it turns out that the scenario is different from what I had originally thought.  Hopefully this way will be much more plausible.

I came upon my wife's parents' old desktop.  I originally thought that the machine had a single 120 GB drive, but it turns out that there was a 40GB and 80GB instead.  Windows apparently "sees" RAID-0 by default.

Here is my current plan of action:  

I would like to walk through it first to make sure that my rationale is sound and to hopefully provide a good example to those looking to do the same thing in the future.

My thinking is to have the "important stuff" on the 40, and RAID-0 the existing 160 and 80 for the recordings/movies.  This data isn't particularly important, as either the media already exists in a hardcopy form or can be re-recorded.  The extra bandwidth and space that RAID-0 provides is all that would really be important.

I have partitioned the 40 GB drive with swap and root filesystems.  The existing system has about 100GB total used space, and my thinking is that I would be able to move the data to the drive (mounted on /mnt) using:
```

sudo tar cvpjf /mnt/backup.tar.bz2 --exclude=/mnt /

```

The .tgz file should be small enough I would think-- ~30% of original size (with /tmp cleared)...  

I would then use the alternate boot cd to create the RAID-0 between the 160 and 80 GB drives.  This would provide a safe environment in which to do so in my estimation.  After creating the new "single" partition and mounting it to the appropriate mythtv directory, backup.tar.bz2 could be extracted and grub reinstalled.

After that, it should simply automagically reboot to its newfound glory.  Like I asked before, is this a relatively "smart" way of doing this, or is there a better approach?

Thanks

---

### Post by a_posse_ad_esse on 2008-02-05
I ended up simply backing up important data and reinstalling.  Thank you for the input.

---

