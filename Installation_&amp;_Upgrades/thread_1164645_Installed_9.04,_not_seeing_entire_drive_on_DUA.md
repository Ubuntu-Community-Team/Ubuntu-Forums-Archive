---
title: "Installed 9.04, not seeing entire drive on DUA?"
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by Insoc on 2009-05-19
I'm new to Unbuntu, switched from Windows fully after experimenting with the live CD. 

I purchased a new Western Digital 500GB Caviar Green HDD and did a fresh install with Unbuntu 9.04 only.

I noticed under the Disk Usage Analyzer that the total filesystem capacity is only 452.8GB not 500GB?  Can I fix this with gparted or is there another way within Unbuntu?

Thanks!

---

### Post by StooJ on 2009-05-19
That's because hard drive manufacturers don't actually use the same scale as an operating system does. The HDD people calculate 500GB as 500 x 1000000000 bytes.

Now, computers work in multiples of 2 (2, 4, 8, 16, ..., 1024), and measure things accordingly. So a Gigabyte *actually* works out to be 1073741824 bytes. Not a nice number in decimal, but a nice number in binary.

As you can see, Western Digital's idea of a gigabyte is a lot smaller than a computer's idea of a gigabyte. So you haven't lost space, you're just looking at the total on a different scale.
The question of who is using the correct scale is a different matter, of course.

---

### Post by Insoc on 2009-05-20
> **StooJ said:**
> That's because hard drive manufacturers don't actually use the same scale as an operating system does. The HDD people calculate 500GB as 500 x 1000000000 bytes.

Now, computers work in multiples of 2 (2, 4, 8, 16, ..., 1024), and measure things accordingly. So a Gigabyte *actually* works out to be 1073741824 bytes. Not a nice number in decimal, but a nice number in binary.

As you can see, Western Digital's idea of a gigabyte is a lot smaller than a computer's idea of a gigabyte. So you haven't lost space, you're just looking at the total on a different scale.
The question of who is using the correct scale is a different matter, of course.

Thanks,  that totally passed my mind.  This is the first Western Digital drive I have owned, had a Hitachi previously and never noticed capacity being off this much.

---

