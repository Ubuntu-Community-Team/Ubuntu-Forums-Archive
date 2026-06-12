---
title: "New external harddrive has alot of used space"
date: 2009-05-08
forum: Hardware
---

### Post by specialblend on 2009-05-08
Hi guys,

Im running 9.04 and I just got a new WD 1TB external harddrive.  I reformatted it to ext3 because it came as fat32.  When viewing the drives properties after the format, it says its a 930 gb drive which is correct, but it says that there is already 50 gbs in use.  I have never put anything on this harddrive.  Any ideas?

---

### Post by taurus on 2009-05-08
930 * 0.05 = 46.5GB.  Ext3 filesystem reserves 5% of the disk space for root.  You can remove the 5% reserved option if you wish with tune2fs command.

---

### Post by DJYoshaBYD on 2009-05-08
you could also just format to ntfs and use it like that.. once its ext3, NO windows machines can read it at all.. if you plan to NEVER EVER plug it into a windows machine, then you are good, but you really want to use it to its fullest, format to ntfs, and it should be plug and play with full read/write support... thats how mine are...

but yeah... either ext3 or ntfs are great choices, but you are just limited to *nix machines with ext3.... you may wanna share some media with a friend.. lol

---

### Post by taurus on 2009-05-08
> **DJYoshaBYD said:**
> you could also just format to ntfs and use it like that.. **[COLOR="Red"]once its ext3, NO windows machines can read it at all..[/COLOR]** if you plan to NEVER EVER plug it into a windows machine, then you are good, but you really want to use it to its fullest, format to ntfs, and it should be plug and play with full read/write support... thats how mine are...

but yeah... either ext3 or ntfs are great choices, but you are just limited to *nix machines with ext3.... you may wanna share some media with a friend.. lol

That is not true at all.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by DJYoshaBYD on 2009-05-08
we were talking about ext3, right? not 2? lol

this is news to me, but either way, how many of windows users will have this? no one... lol.. ntfs is plug and ply in windows, and pretty much plug and play in linux.. it just seems it would be the least problematic...

---

### Post by specialblend on 2009-05-08
thanks for the help.  I am only using this for movie storage, and I only use linux so ext3 is fine.

I tried running tune2fs with:

sudo tune2fs -m 0 /dev/sdc

but I get this error:

tune2fs: Bad magic number in super-block while trying to open /dev/sdc
Couldn't find valid filesystem superblock.

Am I doing something wrong?

---

### Post by taurus on 2009-05-08
You suppose to use /dev/sdc1.

---

### Post by taurus on 2009-05-08
> **DJYoshaBYD said:**
> we were talking about ext3, right? not 2? lol

It works for ext3 too.

---

### Post by specialblend on 2009-05-08
Worked perfectly.  Thanks for the help and the super quick replies.

---

