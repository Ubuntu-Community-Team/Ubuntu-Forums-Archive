---
title: "Is a swap file mandatory?"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by tmcarson1 on 2009-01-28
I tried letting ubuntu installer resize my partitions and it keeps failing and giving an error.  I do have a spare partition I can install ubuntu to, I just don't have a 2gb partition for the swap file.

question is, is this required and necessary?

Will ubuntu run well without a swap file?

I have 1gb of ram installed now.

Any advice is appreciated.

---

### Post by dstew on 2009-01-28
You do not need a swap partition (what you have called a swap file) for Ubuntu to run. A dedicated partition will help it run faster, but if you do not have a swap partition, Ubuntu I think can make a swap file on your lone root partition if it needs to swap. Also, you don't need a swap partition bigger than 1 Gb.

The real question is why is the resize operation failing. Remember, you can only resize an unmounted partition. If you are tring to resize a Windows partition, there can be immovable files that impede the resize operation. These can be fixed using Windows tools.

---

### Post by ajcham on 2009-01-28
Someone on these forums, in their sig, likens swap to a reserve parachute.  You probably won't need it, but if you do&#8230;

In your case, I wouldn't worry about having 2GB of swap though - you've probably seen the advice that recommends double the RAM.  This advice is somewhat outdated in most cases and 512MB should be adequate, regardless of how much RAM you have.  The only exception I know of is if you wish to use suspend/hibernate features, in which case the swap should at least equal your RAM.

---

### Post by tmcarson1 on 2009-01-28
> **dstew said:**
> You do not need a swap partition (what you have called a swap file) for Ubuntu to run. A dedicated partition will help it run faster, but if you do not have a swap partition, Ubuntu I think can make a swap file on your lone root partition if it needs to swap. Also, you don't need a swap partition bigger than 1 Gb.

The real question is why is the resize operation failing. Remember, you can only resize an unmounted partition. If you are tring to resize a Windows partition, there can be immovable files that impede the resize operation. These can be fixed using Windows tools.

Thanks for the info, this could have well been the problem, I think the partitions may have well been mounted.   I will try again after making sure the partition (ntfs) is not mounted and see if it will re-size it and do a proper install then.

I appreciate everyone's help.

---

### Post by Mark Phelps on 2009-01-28
You mentioned NTFS ... If the partition you are trying to resize is Vista, do NOT use Ubuntu or Gparted to resize it unless you have a Vista DVD at hand.  In some cases, resizing a Vista partition using non-MS software results in the Vista partition being unbootable -- which is no problem if you have a Vista DVD because you then boot from that DVD, do a Startup Repair, and you're back in business.

But if you don't have a Vista DVD, you're running a risk of leaving your Vista partition unbootable and, therefore, unusable.

The less risk approach, for Vista, is to use the Vista disk management console to shrink the Vista drive to make room for another partition.  If you're having trouble getting it to shrink enough, check out this link:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

---

