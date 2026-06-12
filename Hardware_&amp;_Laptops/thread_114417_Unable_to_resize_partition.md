---
title: "Unable to resize partition"
date: 2006-01-08
forum: Hardware &amp; Laptops
---

### Post by cbudden on 2006-01-08
I re ogranised my partitions when I removed my Windows Xp install.  I need to resize my hda1 partition by 1 GB for swap space but i cannot do it.  I have tried the live CD, which does about 6-7 minutes work then says "error", thats it.  When I tried with another partition editing program from booting and it wouldn't let me resize at all.  I tried in normal ubuntu, and umounted the partiton.  Then the error message was after about 6-7 min's and it said "cannot be applied to a busy device"  What else can I try?

here is a screenie of gparted
[http://static.flickr.com/36/83964877_0ce7d3d4c3_o.png](http://static.flickr.com/36/83964877_0ce7d3d4c3_o.png)

---

### Post by plors on 2006-01-08
you could try the [gparted livecd]("http://gparted.sourceforge.net/livecd.php"). It's still in testing, but should work ok.

cheers

---

### Post by cbudden on 2006-01-08
Thanks for your reply but I backed up the data on the problematic partition, deleted it and created a 1gb smaller partition and a 1gb swap space, which worked fine.

---

