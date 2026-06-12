---
title: "Drive emulation?"
date: 2006-11-02
forum: Hardware &amp; Laptops
---

### Post by casperiv on 2006-11-02
What is a good program that works well with Ubuntu that will load an iso as to an emulated drive?  I have a lot of my CD's backed up as ISO's and I want to load them up like I would with Alchohol in XP.  Any suggestions?

---

### Post by mark_g on 2006-11-02
The program you need is already installed: mount. For example:

> mount -t iso9660 -o loop /home/username/myimage.iso /mnt/mountdirectory

would mount an iso-image in the directory /mnt/mountdirectory.

---

### Post by casperiv on 2006-11-02
Now see, thats awsome. I would have never found that since my searches never turned it up.  That will be very handy when I go to break into my iso's.

---

