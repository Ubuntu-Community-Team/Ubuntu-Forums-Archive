---
title: "SWAPPINESS, SWAP PARTITION and FLASH DRIVE SWAP"
date: 2007-06-06
forum: Hardware &amp; Laptops
---

### Post by adampyre on 2007-06-06
Hello, I posted within a long post so it might get overlooked:

[http://ubuntuforums.org/showthread.php?p=2791213#post2791213](http://ubuntuforums.org/showthread.php?p=2791213#post2791213)

I have some questions about proper configuration for "cascading" RAM, PENDRIVE SWAP and HD SWAP. I also am wondering if someone can help me to understand swappiness better and what number would be good for my amount of ram (256) and my swap partitions for the snappiest system. THANKS!!!

---

### Post by kidders on 2007-06-08
Hi there,

I took a quick look at your other post, to get a better idea of what you're up to. Hopefully I can be of some help...

There isn't really a "proper" configuration for prioritised use of memory (ie it very much depends on why you want it), but there are a great many *wrong* configurations. For instance, it would be _highly_ inadvisable to fiddle with your kernel's swappiness to force it not to use swap space unless it had no alternative. To be honest, I wouldn't recommend playing with "hardcore" kernel parameters (like swappiness) at all without a very solid understanding of Linux's memory management model.

I'd also suggest that using a pen drive (or anything not directly connected to an IDE or ATA bus) would be a bad idea, for a variety of reasons.

On the other hand, many servers keep reasonably large volumes of swap space in reserve ... mostly for stability. Imagine for instance that you had three hard disks, one with a gigabyte of swap, and the others with 512 MiB each. You could force Linux to use the two small swap partitions in parallel (for better performance), and to avoid using the second gigabyte at all, unless it became necessary to do so.

**Edit:** Sorry... I forgot to answer your question about how much swap to use. Normally, the number people choose depends on how much RAM they've got. Unfortunately, 256 MiB is far too little for most purposes, so you'll probably wind up having to allocate far more virtual memory (in %age of RAM terms) than would be ideal. Depending on what you plan on doing with your box, I would suggest anything between 512 MiB and 1 GiB. it may never really feel very "snappy" though. :-(

---

### Post by 444 on 2007-06-08
> 
This is cool. I don't know why I didn't think of it before! It really helps with my laptop that only has 256 MB of ram (the ram for it is hard to find and expensive but I would love to upgrade it.) In the meantime using my pendrive helps!

I DO HAVE A QUESTION THOUGH!!!!!!!

Is there a way to cascade the systems memory usage? Please read the following oh intelligent ones and tell me if I am going about this the right way:

I followed the tutorial about mounting my pendrive as swap space and then I turned of the HD swap space hoping it would speed things up. I have, 256 MB RAM, 512 MB pendrive all dedicated as swap, and 500 MB HD Partition that was dedicated as swap, but I turned it off to force the system to use my pendrive as a swap.

Would it be worth it, to turn the HD swap back on and possibly even make my system "cascade" it's memory usage? What I mean is, use the ram, once ram is full, go to pendrive. Once ram and pendrive are both full, then go to HD. Once all three are full, oh well...

Anyway, is there a way to do this? I have been plaing around with swappiness, should I set this to a certain number? What else do I do to figure this out? Thanks!


The 'cascade' thing is called swap priority. In /etc/fstab you'd say pri=1 for the hd and pri=2 for the flash. See 'man swapon' for details.

Feel free to play with the swappiness, you can set it permanently with /etc/sysctl.conf, of course make sure the setting works fine first. Back when I had 64mb of ram I played around with this, I forgot what it does exactly but lower values were giving me better results. Too low (like 10) made it act weird and hang for 10 secs at a time for no reason. I think I settled on 25 or 40.

---

