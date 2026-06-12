---
title: "Apps using /media/cdrom no longer see /dev/scd0 for audio CDs"
date: 2008-02-08
forum: Hardware &amp; Laptops
---

### Post by sproaticus on 2008-02-08
Recently, audio CDs stopped working.  CD-ROMs still work as expected, as do DVDs.  But when I fire up Totem or Amarok or grip to play an audio CD, they can't find the drive.  

In my fstab, I see that /dev/scd0 is mounted at /media/cdrom0 (which has a symlink to /media/cdrom).

I was able to get grip to work by telling it to look at /dev/scd0 instead of /media/cdrom - but why do I need to do that now when /media/cdrom worked in the past?

One possibility I can think of is a recent hard drive upgrade.  I dd'ed the old hard drive to the new one, then used gparted to resize partitions.  After that I had to go through several files (/etc/fstab and ~/.kde/share/apps/amarok/collection.db and a couple other places) and change the UUIDs to reflect the new hard drive.  This shouldn't have affected the optical drive, however...right? 

I'm running Gutsy (kernel 2.6.22-14-generic) and Gnome 2.20 on a Dell Inspiron E1505.

---

### Post by sproaticus on 2008-02-12
Bump.

I still haven't had much luck discovering how /media/cdrom0 relates to /dev/scd0 for audio CDs.  (My understanding is that audio CDs are not mounted, but rather are read as block devices, so mount points should be unnecessary.)  I also haven't found out why my audio apps were happy with /media/cdrom0 before, but need /dev/scd0 now.

Anyone have a suggestion?

---

