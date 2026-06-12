---
title: "getting a new HD"
date: 2007-04-10
forum: Hardware &amp; Laptops
---

### Post by rock4christ on 2007-04-10
my current hard drive on the old pc is 10gb, so i want to go up to 40(20 apiece for Xubuntu and windows 98) and i was wondering:

with internal hd's  are compatibility issues possible (such as the connector from the hd to the motherboard) or physical space for the hd(like laptops needing a certain type) so is that an issue, or is it as long as its a internal hd your fine?

---

### Post by heimo on 2007-04-10
There may be incompatibilities between BIOS and your hard disk, like a ~32GB limit. But if your computer supports >32GB disks, and the new disk is of same type (same connector), your (modern) operating systems will be just fine.

---

### Post by rock4christ on 2007-04-10
> **heimo said:**
> There may be incompatibilities between BIOS and your hard disk, like a ~32GB limit. But if your computer supports >32GB disks, and the new disk is of same type (same connector), your (modern) operating systems will be just fine.

how would i check for a limit? and ho would i know what connector i need?

---

### Post by heimo on 2007-04-10
> **rock4christ said:**
> how would i check for a limit? and ho would i know what connector i need?

Best place is laptop manufacturers website (support). There may be list of compatible hardware. Don't assume that any 2.5" disk will work. Easiest would be ordering upgrade part from manufacturer, but these may be a bit pricy.

You could also tell us make and model of the computer -- basically, if it's really old, it might have a limitation. If it's not more than couple years old, it will not have this limitation. And even if it did, 40GB would probably be usable as a 32GB disk.

---

### Post by rock4christ on 2007-04-10
[this]("http://h10025.www1.hp.com/ewfrf/wc/genericDocument?lc=en&cc=us&docname=c00191338") is my pc

---

### Post by heimo on 2007-04-10
Oh. I misread your original post, and thought that it was a laptop. Sorry for that.

I searched HP/Compaq site, but couldn't find information I was looking for. I couldn't find BIOS updates for your machine (they might be there somewhere, I just couldn't find).

Then I searched Google and found someone who had upgraded from 10GB to 40GB and hit the 32GB barrier:
[http://forums.pcpitstop.com/index.php?showtopic=82354](http://forums.pcpitstop.com/index.php?showtopic=82354)

So you may need to find a BIOS upgrade which fixes the problem, or you might be able to get IDE controller card which can handle over 32GB disks (but that might not be worth the 8GB and all the trouble).

If you'll buy a disk, check that it's parallel ATA (PATA) and not the new serial ATA (SATA).

---

