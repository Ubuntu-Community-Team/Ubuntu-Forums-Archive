---
title: "Possibly bizarre use of system resources?"
date: 2008-10-10
forum: General Help
---

### Post by stevejesus on 2008-10-10
So I upgraded from 1gb of ram to 2.5gb or ram.  Before, upon logging into gnome, I would tun "top", and it would tell me I was using 970(approx)mb or ram.  That seemed unreasonable high.  Now, I run "top", and it's telling me that all 2.5gb is being used!  

In both cases I would swap a little.  Usually less than a megabyte.  So I loaded Gimp and Firefox, and the used amount of ram did not change...

I installed preload before.  Is this why?

If so, is preload worth using?

---

### Post by Sam on 2008-10-10
It's absolutely normal! That's how linux manages memory. Read [this](http://ubuntu.wordpress.com/2005/10/07/memory-swap-management/) for more information.

---

### Post by Yannick Le Saint kyncani on 2008-10-10
Hi stevejesus,

Ram is used as cache so that files/libraries that are often used can be read from ram instead of disk to enhance performance (ram is considerably faster than hard drives).

Of course, if you use applications and need memory for them, this cached memory will be automatically freed. When you close your apps, the unused ram will be used as cache then again improve performance.

So no worry :)

---

### Post by stevejesus on 2008-10-10
Thanks guys.  You know, in 2003 when I was using RH9 and Fedora core I was very low on RAM (256).  I was swapping like crazy.  In 2005, running fedora 4/transitioning to Breezy, I had 512.  I was swapping like crazy.  When you never have enough RAM, you never notice how aggressive the caching is!

Thanks for the info guys.

So, if all of this is true, what is the point of preload?

---

### Post by stevejesus on 2008-10-10
And more importantly, why am I swapping 45 megs to disk just browsing the web and using a terminal emulator?

---

### Post by Sam on 2008-10-10
> **stevejesus said:**
> So, if all of this is true, what is the point of preload?
preload does cache the libs/data BEFORE you access them. The memory management caches only what you already accessed. Example: Open OpenOffice when you just switch on your pc, then close it when it's loaded. Reopen it again. Enjoy the speed.

> **stevejesus said:**
> And more importantly, why am I swapping 45 megs to disk just browsing the web and using a terminal emulator?
Don't know. I also have some megs in swap. It's probably the oldest cached data that goes there... However I never felt my system slower.

---

### Post by stevejesus on 2008-10-12
This is much more realistic; removed preload and when browsing the web, managing files with nautilus, listening to tunes, managing torrents, etc., I am using 750MB ram.  
Before when I had only 1GB, I would loud huge images into GIMP's tile cache and because of preload I would swap heavily before preload decided which programs to kick out of ram.

So, I have concluded that preload is great if you are the type that uses the same apps often with little deviation.  If you like to try new software, work with very large files, or a combination of the 2, preload is probably not for you.

---

