---
title: "Pre-seeded LVM on RAID"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by vertigo23 on 2009-06-11
I'm getting an automated install set up, and need to have the following (fairly common) partition layout:

/dev/md0 -> /boot
/dev/md1 -> physical volume for LVM

Where the MDs are mirrored.  Is there any way to do this with the preseed d-i partman stuff?  This is something that RedHat kickstart has handled nicely for many years now.  :(

---

### Post by SergeiFranco on 2009-08-18
Yeah I am very interested in this.
I am actively looking if it is possible...
I have found examples on how to setup LVM and how to setup RAID.
But not both.
Still looking.
Will bookmark this thread and post result if I find something.

---

### Post by lemsx1 on 2010-06-07
[http://ubuntuforums.org/showthread.php?p=9425595#post9425595](http://ubuntuforums.org/showthread.php?p=9425595#post9425595)

I already do this on Lucid. It's giving me trouble though, but this is known to work fine for others. There is something I'm missing or adding that causes this to break.

Check the post nonetheless, you might have better luck.

---

