---
title: "Enough memory for desktop?"
date: 2005-08-16
forum: Hardware &amp; Laptops
---

### Post by bue on 2005-08-16
Hi!

I have a Mitac-laptop with a Pentium 233 and a 4 Gb HD. I have made a swap-partition of about 170 Mb and have 160 Mb RAM (or close to that). Problem is that when the ubuntu graphical log-in is displayed I have already used up about 75 Mb, and after logging in to gnome I have like 20 Mb free (of the RAM, no swap used). This means that there is not much room left to do any work without using swap-memory.

A few days ago I did little more than boot, log in and run two applications for a short while and boom, all swap used up. Computer was unbelievably slow, took 10 minutes just to shut down, which I had to do from a console. My question is: Is there a way to free up memory? I don't know if a lot of memory is used to cache files, but if so, can I tell ubuntu to cache less files, like a cache-limit or something?

Thanks in advance!

/bue

---

### Post by varunus on 2005-08-16
One thing I would suggest is to try using XFCE instead of GNOME if you can.  (Install the xfce4 package and associated packages from synaptic.)  Its a full-featured desktop environment, very similar to GNOME, uses GTK2 for its toolkit, and runs in much much less RAM.

GNOME 2.10 is not meant for computers from that era, unfortunately.  XFCE should get you going, though.  You can configure it to be like GNOME...just make sure to install all of the plugins for it.

You may also want to try enlightened GNOME, the author says he has it running on a P300 with 128MB RAM:
[http://www.ubuntuforums.org/showthread.php?t=54476&highlight=enlightened+gnome](http://www.ubuntuforums.org/showthread.php?t=54476&highlight=enlightened+gnome)
This replaces metacity (the GNOME window manager) with enlightenment (a harder to use, mostly GNOME compatible window manager.)  If you do choose to go with enlightened gnome, use E16, and post back here; i'd suggest using E16.7 instead of the version included in Ubuntu, and I can show you how to get it...(what I did to get it is not recommended though.)

If you must use GNOME...Things I'd suggest, remove unnecessary virtual desktops and remove unnecessary panel applets or panels.

---

### Post by jasmuz on 2005-08-16
Check these links out, to see if you get any ideas:

[https://wiki.ubuntu.com/Installation/LowMemorySystems?highlight=%28lowmem%29](https://wiki.ubuntu.com/Installation/LowMemorySystems?highlight=%28lowmem%29)

[http://www.ubuntuforums.org/showthread.php?t=42873](http://www.ubuntuforums.org/showthread.php?t=42873)

[http://ubuntulite.org/about.html](http://ubuntulite.org/about.html)

---

