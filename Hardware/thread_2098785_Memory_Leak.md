---
title: "Memory Leak?"
date: 2012-12-27
forum: Hardware
---

### Post by jspike397 on 2012-12-27
Hello Everyone,
	I am having a problem with Ubuntu taking up far too much ram.  I disabled everything that I have up when I boot up and I am using 800 mb of ram, out of 2 GB. I have two screenshots of my system monitor underneath, but by the time those were taken, the ram went up to around 1GB.

 Also, when I ran the command free -m I got the following response:
```

             total       used       free     shared    buffers     cached
Mem:          2002       1937         64          0         80       1062
-/+ buffers/cache:        795       1206
Swap:         5721          0       5721

```

After I used the command, the memory went a hundred megabytes up as I opened a screenshot utility to take the image.

Once I get up to 1.8 Gigabytes of ram and my computer switches to swap, the computer runs very slow.

I am using Ubuntu 12.10 with a home-built Asus M2N68 AM + Motherboard with 2 GB of ram, a Nvidia G210 Graphics card with 1 GB of ram, so I do not think that Graphics memory is causing it.  I have tried KDE, Gnome Shell and Unity and I always get the same response. Is there some sort of memory leak in my system?

I also have a Asus 1005HAB netbook and what is funny is that it uses only 378 MB of ram while idling.

Thank you for all your help,

Jspike397

---

### Post by ahallubuntu on 2012-12-27
This sounds normal.  The kernel uses up all available RAM and caches everything else, to try to improve performance.  (see the 1062MB of cache?)  The more windows you open, the more RAM it will use; close them and most of that should be reclaimed.

Now, at idle, your RAM use shouldn't keep increasing on its own.

---

### Post by jspike397 on 2012-12-27
Ahallubuntu,
Thank you for your quick reply.  I have one question still. Does my netbook also do this, because of the VERY low amount of RAM that it shows when I run the free -m command? I previously read this online, but I am still very confused because of the ram used idle n the netbook.  It seems like it does not cache things as much as my Desktop then.  I have the same amount of RAM on both systems.

Thanks,

Jspike397

---

### Post by CharlesA on 2012-12-27
You have 1.2GB of RAM free according to free -m. You are fine.

---

### Post by jspike397 on 2012-12-27
Thank you for your advice. If this is not abnormal. I got confused with the Netbook's amount of ram compared to the Desktop computer. Thank you again.

Jspike397

---

### Post by OrangeCrate on 2012-12-27
Always a good read on RAM usage in Linux...

**Help! Linux ate my RAM!**

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by jspike397 on 2012-12-28
Thank you for your help. That was a very helpful article.  I think I solved my original problem so I will now mark the thread as solved.

Jspike397

---

### Post by OrangeCrate on 2012-12-28
> **jspike397 said:**
> **Thank you for your help. That was a very helpful article.**  I think I solved my original problem so I will now mark the thread as solved.

Jspike397

You're welcome.

:)

---

