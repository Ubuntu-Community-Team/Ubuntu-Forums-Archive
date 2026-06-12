---
title: "Treating a &quot;fixed&quot; disk as removable?"
date: 2007-08-21
forum: Hardware &amp; Laptops
---

### Post by locovaca on 2007-08-21
Here's my  dilemma.

I have an Inspiron 8600.  For my swappable device bay I have both a DVD drive and a second hard drive.  In general the second hard drive is in there, but on occasion I swap in the DVD to rip some music or something else.

So, the problem is that the "removable" bay devices actually site on the IDE bus.  So, by default they do not get automounted as fixed IDE devices are generally in fstab.  I don't want to put the devices in fstab because I get errors when booting because one or the other device isn't available.  And, I'm looking for an automatic solution which puts my icons nice and neat on my desktop ;)  (Yes, I know about manually mounting, but I moved from Gentoo because I got sick of dropping to a terminal to do basic things!)

Any thoughts?

---

### Post by pbcartwright on 2007-08-21
I have a USB HD that I have in fstab. I use this entry:
/dev/sdf5            /media/backup        ext3       acl,user_xattr        1 0

the last 0 (ZERO) tells it not to run fsck, so it gives me no errors if I don't have it turned on.

---

