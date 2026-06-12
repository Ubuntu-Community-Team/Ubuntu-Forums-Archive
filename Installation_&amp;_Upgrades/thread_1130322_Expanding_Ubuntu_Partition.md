---
title: "Expanding Ubuntu Partition?"
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by Eff3cTz on 2009-04-19
I currently run Windows Vista Home Premium 64-bit, and Ubuntu 8.10 64-bit on my computer. I have 350GB free, but my Ubuntu partition is only 15GB in size. I've searched around, but I haven't seen any real answers.

Is there a sure-fire way to expand my Ubuntu partition to say, 60GB and shrink my Vista partition 60GB?

Thanks!

---

### Post by aheckler on 2009-04-19
**_Back up all your data_!** Defrag your Windows paritition several times. Then, burn a GParted LiveCD, boot to it, shrink the Vista partition to the size you want. Expand your Ubuntu partition to the size you want. Bingo!

---

### Post by Eff3cTz on 2009-04-19
Thanks for helping a noob of ubuntu out! I'll try that out tomorrow.

 So far I'm really enjoying it...a very cool OS. Need to keep Vista for gaming though, and the fact that I like MS Office better than OpenOffice.

Again, thanks.

---

### Post by Mark Phelps on 2009-04-20
Since you "need to keep Vista for gaming ...", before you use GParted to shrink the Vista OS even more, be sure you have a Vista DVD around just in case the partition gets corrupted in the process.  IF that happens, boot from the Vista DVD and run Startup Repair.

If you don't have such a DVD, suggest you do the shrinking using the Vista Disk Management tool instead of GParted.

---

### Post by Eff3cTz on 2009-04-20
> **Mark Phelps said:**
> Since you "need to keep Vista for gaming ...", before you use GParted to shrink the Vista OS even more, be sure you have a Vista DVD around just in case the partition gets corrupted in the process.  IF that happens, boot from the Vista DVD and run Startup Repair.

If you don't have such a DVD, suggest you do the shrinking using the Vista Disk Management tool instead of GParted.

The Vista Disk Management tool is screwed up. I have a 500GB HD, and about 350GB free, and it only let me shrink it 15GB. I can no longer shrink it via Vista D. M. 
I do have a Vista disc handy though.

---

### Post by Mark Phelps on 2009-04-22
> **Eff3cTz said:**
> The Vista Disk Management tool is screwed up. I have a 500GB HD, and about 350GB free, and it only let me shrink it 15GB. I can no longer shrink it via Vista D. M. 
I do have a Vista disc handy though.

You could try some of the suggestions from the following link:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

If that doesn't get you enough shrinkage, suggest you download and burn the latest GParted LiveCD from distrowatch.com and use it to shrink the Vista OS.  When you do that, make sure that "Round to the nearest cylinder" is not checked.  That lessens the likelihood that the partition will get corrupted.

Would still recommend backing off any critical data from the Vista partition before you start.

---

### Post by chrisinspace on 2009-04-22
> **Mark Phelps said:**
> Would still recommend backing off any critical data from the Vista partition before you start.

You should definitely back up your data.  An OS can be very fickle when it comes to messing with partitions.  I crashed a Win2k3 server doing this one time.  It looked fine when I was done and even ran for a couple of days before it bit it.  Luckily it wasn't a vital server and I had an image.

I would highly suggest that you take an image of your hard drive.  Then you can restore from the image if things go wrong.  It will save you a ton of time and headaches.  You can use [Clonezilla]("http://distrowatch.com/table.php?distribution=clonezilla") to do take images and restore them for free.

---

