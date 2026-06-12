---
title: "No wireless or proprietary drivers for HP dv9000 with 9.10"
date: 2009-11-01
forum: Hardware
---

### Post by sergeroy on 2009-11-01
Hi I have a HP dv9000 and after a fresh install of 9.10 (using wubi),  I have no wireless available and ubuntu also doesn't provide me with any proprietary drivers for my video card.

---

### Post by InsaneBeast on 2009-11-24
I have the exact same problem with my HP TX2Z.  I installed ubuntu 9.10 using wubi.exe, but my installation has no sound, wireless, touchscreen, ati drivers, etc.  Previously, I had tried to install ubuntu on its own partition and resize my windows 7 partition, but installing ubuntu corrupted my windows 7 partition so I had to use the HP recovery disks to restore windows 7.  If you figure out how to get your HP laptop working with ubuntu 9.10 via a wubi install please let me know.

---

### Post by ramjet_1953 on 2009-11-24
Hi, there!

This link may be worth looking at:

[http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html](http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html)

Regards,
Roger :)

---

### Post by don_pucci on 2009-11-24
How can anyone say that Ubuntu is ready to take on Windows in the desktop market when 9.10 there are issues "out of the box".

SO frustrating...every machine i have has issues with every version of ubuntu.

---

### Post by ramjet_1953 on 2009-11-24
Hi don_pucci!

And your question is?

If you have issues, just ask them, how do you expect to get help by just complaining?

Remember, most issues are because hardware manufacturers do not release drivers for Linux, or are slow to release drivers for their new hardware.

There are dedicated coders working to reverse-engineer drivers, but this takes time.

You should be venting your spleen on the hardware manufacturers, not people who are providing you with Linux.

Don't forget, that when Vista was released, there was a huge problem for many Windows users with exactly the same problem - no drivers!

Regards,
Roger :)

---

### Post by walks on 2009-11-25
Hello, I am new to Ubuntu and am loving it so far. But I am also having issues with the wireless. I have an HP dv6000. I understand how it works and will continue to be hard wired until it is resolved. Hopefully soon!

---

### Post by walks on 2009-11-25
> **ramjet_1953 said:**
> Hi, there!

This link may be worth looking at:

[http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html](http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html)

Regards,
Roger :)

Thanks Roger for the site although i'm a bit of a noob/newb as far as linux goes so this all seems terribly complicated at the moment. Has anyone investigated this issue further that could relay what they are suggesting to do in slightly simpler terms? If not i believe i can figure it out but just might be quicker with some help!

Thanks!

---

### Post by jbrevik on 2009-12-07
When I did the fresh install of 9.10 on my HP dv600 I was not able to see any proprietary drivers. After I enabled the Pre-release Updates (not sure if this is necessary) and the Unsupported updates (karmic-backports) I was able to install the broadcom wireless drivers and nvidia drivers 
 

System>Administration>Software Sources>Updates>Select :: 
Pre-release Updates and Unsupported updates (karmic-backports)

The sources will update.....now goto System>Administration>Hardware Drivers

The b43 Broadcom and all other nvidia drivers should be listed and ready to install

Hope this helps

---

