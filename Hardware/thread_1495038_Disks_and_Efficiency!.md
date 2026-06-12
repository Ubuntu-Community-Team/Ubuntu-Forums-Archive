---
title: "Disks and Efficiency!"
date: 2010-05-27
forum: Hardware
---

### Post by carlbeech on 2010-05-27
Ok,

I've had a look, but not spotted anything that seems related to this so here goes....

I'm running a laptop - and running 'powertop' I can see programs continually writing data to the disk, and stopping it being spun down, and therefore saving a lot of battery.

Does anyone know of a way to a) create a ramdisk, and b) to redirect arbitrary files to exist within the ramdisk, so that the continual updates take place there and allow the disk to spin down?

Ok - I can see the horror on faces already - these programs need to cache data etc - well a cache most of the time isn't really required long term - and if it came down to it, there'd be nothing wrong in copying the ramdisk value to the real disk say once every 10 minutes etc...

What does anyone think?

I know it should be really down to the developers of the code that's actually doing the writing e.g. kde / google chrome etc, however, I think the developers are mainly coding for the desktops where this isn't really a problem (or is it - after all, writing to a ramdisk would be faster wouldn't it... hmmm)

Comments / Solutions please!

Ta

Carl.

---

### Post by dabl on 2010-05-27
Whenever you starting tinkering with the caching and cache-flushing functions (in the name of efficiency, perhaps), you're also tinkering with data security.  Especially when you're doing it on a laptop -- loss of power at an inopportune moment might cost you your data.  With that said ...

General power saving tips:

[http://www.lesswatts.org/tips/disks.php](http://www.lesswatts.org/tips/disks.php)


You can control the frequency of flushes to the disk as per:

[http://www.westnet.com/~gsmith/content/linux-pdflush.htm](http://www.westnet.com/~gsmith/content/linux-pdflush.htm) 


Also, you can control swappiness and "cache pressure", as per this:

[http://rudd-o.com/en/linux-and-free-software/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that](http://rudd-o.com/en/linux-and-free-software/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that)

---

### Post by carlbeech on 2010-05-31
I can see what you're saying here, however, the solutions that you mention in the links are general purpose defer-write type situations. What I was trying to get at was the idea of targetting specific files, that have little / no long term impact (such as lock files or caches), which are temporary and (in all probability) will be re-created on the next boot anyway.

If you need to write to disk, then you need to write to disk - I've not a problem with that - I'm specifically looking at updates to 'non-important' type files...

If we were able to target specific files, then the disk would be able to go into power saving mode, which would make a potentially large impact on battery life of a laptop...

Carl.

---

