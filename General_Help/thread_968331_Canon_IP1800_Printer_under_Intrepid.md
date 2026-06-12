---
title: "Canon IP1800 Printer under Intrepid"
date: 2008-11-02
forum: General Help
---

### Post by lakerssuperman on 2008-11-02
Hello,

I am attempting to use a Canon IP1800 printer with Intrepid.  I had it previously working under Hardy.  I did a fresh install and am now trying to reinstall the printer under Intrepid.  I am setting it to use the PPD file for the printer and it seems to install fine, but it doesn't print. Anyone get this printer working or have any tips on getting it to work.  Thanks.

---

### Post by N'ko on 2008-11-14
Please see this thread "Canon PIXMA ip1800 Installation Issue"
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=850298](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=850298)

This should get your printer up and running under Intrepid

---

### Post by x1a4 on 2008-11-26
Hi,
See [my HOWTO]("http://hex1a4.net/xubuntu/howto/04/") on this and try installing the Hardy driver.  If it doesn't work please let me know.  I haven't upgraded to Intrepid so I didn't bother repackaging the driver for it.  But if it doesn't work for you I'll see what's what and create one.

---

### Post by Weidbrewer on 2009-02-11
That did the trick.m  Awesome.  Thanks!

---

### Post by mastapat11 on 2009-06-08
> **x1a4 said:**
> Hi,
See [my HOWTO]("http://hex1a4.net/xubuntu/howto/04/") on this and try installing the Hardy driver.  If it doesn't work please let me know.  I haven't upgraded to Intrepid so I didn't bother repackaging the driver for it.  But if it doesn't work for you I'll see what's what and create one.

i'm using ubu8.10 ibex.
the common file installed fine.

i tried the hardy driver and it wouldn't compile. i then edited the deb file to remove the libxml1 dep and it complied.  but the /etc/init.d/cupsys file wasn't created. i copied the /etc/init.d/cups file to make it.

with all that done, when i go to select the printer i see the "USB Printer #1 with status readback for Canon IJ", but the model ip1800 still isn't on the list. the 2000 is the smallest # on there.

anybody know what to do next? thanks.

---

### Post by Weidbrewer on 2009-06-24
Here's a question:  How do I kill the freakin' thing?  For some reason, in the last few days, it quit working and now starts some background process that is using a full core of my CPU.  I can't find any way to kill it.

---

