---
title: "Need help preserving /home (migrating from gentoo)"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by the.drizzle on 2009-06-13
Hello!

OK, I've been fiddling around with kubuntu today on a VM, and I'm sold!  I want to install it to my primary machine, but I'm not sure how I go about ensuring that I preserve my /home partition.  That is, the current setup (gentoo 2009) is:

/dev/sdc1  ext2  /boot
/dev/sdc2  swap
/dev/sdc3  ext3  /
/dev/sdc4  ext3  /home

I want to install kubuntu to drive 1 and 3, and leave 4 untouched.  I'm new to this install-via-a-gui thing, and am not sure how to do this...

Sorry if this is covered in some intro documentation; probably used the wrong search string!

Cheers!

---

### Post by PureLoneWolf on 2009-06-13
During the installation, you will be presented with the partition editor.  Choose manual and then make sure that the "Format" flag is only checked for the partitions you are happy to wipe out.

---

### Post by the.drizzle on 2009-06-13
So I just leave the "format" box un-checked, but still make /home the mountpoint for /sdc4?  This won't overwrite my existing data?

---

### Post by PureLoneWolf on 2009-06-13
Absolutely - It can't hurt to take a backup/copy of your home folder first, just to be safe though.  I am not familiar with Gentoo, so there may well be some gentoo specifics in ".xx" folders that could cause an issue.

---

### Post by the.drizzle on 2009-06-13
Sounds too easy to be true--hence the move though ;)

Thanks, I'll be doing it tomorrow!

---

