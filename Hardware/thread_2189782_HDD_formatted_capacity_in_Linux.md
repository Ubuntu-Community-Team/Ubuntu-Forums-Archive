---
title: "HDD formatted capacity in Linux?"
date: 2013-11-24
forum: Hardware
---

### Post by junk.here on 2013-11-24
I have a 3 TB HDD. Under Windows 7 and NTFS, I had 2.72 TB of usable space. However, after reformatting in Ubuntu with ext4, I now only have 2.68 TB of usable space. On top of that, 139 GB of space has already been used somehow, leaving me with just 2.54 TB of space.

What's going on here?

---

### Post by oldfred on 2013-11-24
Serveral things. Different tools show space differently for GB or GiB. And different tools report just available space  or include the reserved or formatted space.

 MB vs MiB
[http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)
[http://www.osforge.com/news/001337.html](http://www.osforge.com/news/001337.html)
Then when you format it, the ext4 is journalized so it reserves space for the journal (NTFS also has journal, FAT32 does not). This improves performance and allows error correction for the cost of a small amount of space. Also reserves space for superuser.
[http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/](http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/)
Hard Drive size
[http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)

sudo parted -s /dev/sda unit GB print
sudo parted -s /dev/sda unit GiB print

The 5% reserved for the system partition with new very large drives it often too much. That was from when drives were MB in size and you wanted some hidden space to prevent system from crashing if full. With Windows is just slows down & crashes when full. So when you get to 10% left in Windows it will be very slow but you actually only have 10% left.

 Also in Linux the default is to reserve 5% of the diskspace for the superuser (this can be adjusted using tune2fs -m).
sudo tune2fs -l /dev/sdd3

---

### Post by junk.here on 2013-11-28
Thanks for the advice. After running tune2fs -m 0, all 2.68 TB is now usable.

I'm curious as to why ext4 formatting eats up an extra 40 GB compared to NTFS though...

---

### Post by oldfred on 2013-11-29
The 5% is just extra protection that Linux uses. The file space used by journals are similar but may not be reported the same way.
Windows will let you get down to 0%, where Linux will have a little reserve. Some issues can still fill reserve quickly like run-away log files or other system issues. But with normal use it gives the user a little more time to reorganize to make space and help prevent system from crashing.

---

