---
title: "readyboost for Ubuntu?"
date: 2011-08-30
forum: Hardware
---

### Post by MG&amp;TL on 2011-08-30
I have had to use Windows 7 recently, and I noticed that there was an option to use a USB as 'pseudo-RAM', known as 'readyBoost'. Is there something like this for Ubuntu?

Any help appreciated, this is a newb question.

---

### Post by diasf on 2011-08-30
Hi,
(from the top of my head, some details might be wrong)

You can create swap files on any filesystem (as well as activate them with swapon/swapoff). I suppose that, if you create a swap file on the usb drive and activate it, it will be used. Probably not as optimized as in windows (that he uses it differently than swap itself) but it's a start :)

---

### Post by MG&amp;TL on 2011-08-30
Oh, cool, thanks, hadn't thought of that. Will it be an faster than hard disk swap?

---

### Post by walt.smith1960 on 2011-08-30
If your machine has a reasonable amount of RAM (2 GB+), you probably don't need it.  Ubuntu uses way less RAM than Windows.  For doing ordinary tasks on a 4GB. desktop I've run without swap even and never came close to running out of RAM.  I'm pretty sure using a USB drive for swap would be slower than using the hard drive for swap.  I haven't created a swap partition for the past several installs.  Instead I create a swap **file**.  The only downside I see is that I can't use hibernation (suspend to disk).  I use suspend (to RAM) instead and Ubuntu cold boots  fast enough that I don't miss the ability to suspend to disk.  I guess if I used elaborate desktops that take time to recreate suspend to disk would make sense. Here is one pretty simple guide to creating a swap file:
[http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/](http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/)

---

### Post by MG&amp;TL on 2011-08-30
It doesn't. That's why I'm asking. My other machine ran windows7, this one ran XP badly, and occasionally I run system-intensive devloper tools and/or simulations. :D

OK, thanks for the help. Marking thread as solved. Very helpful indeed, machine is running somewhat faster now.

---

### Post by mightyiam on 2013-03-03
Here's [how I did it]("http://randomcrystal.blogspot.co.il/2013/03/hybrid-ssdhdd-ssd-caching-using.html") in my blog.

---

