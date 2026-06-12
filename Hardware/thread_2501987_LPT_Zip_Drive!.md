---
title: "LPT Zip Drive!"
date: 2024-10-28
forum: Hardware
---

### Post by peyre on 2024-10-28
I recently had to abandon the old desktop I bought back in 2009.  I bought one a couple years newer on Craigslist a week or two ago for $40, stuck my drives in it, and I'm back up and running.

I love to keep old hardware going, and still use floppy and zip disks.  This new desktop doesn't have any legacy ports, so I can't use a built-in floppy or ATAPI zip drive any more, but I have several old 250MB LPT zip drives and a PCI-E parallel port, so why not?  To get it working in Xubuntu I had to add two lines to /etc/modules:
ppa
imm

I plugged it in and my old LPT zip drive was working, woot!  But this weekend it stopped.  I think the culprit might be the upgrade from 24.04 to 24.10, which I did this weekend.  Anyone know what might have changed to break it, and what to do about it?

(This is the card, in case anyone's interested: [https://www.amazon.com/dp/B08MY7564C?ref=ppx_yo2ov_dt_b_fed_asin_title](https://www.amazon.com/dp/B08MY7564C?ref=ppx_yo2ov_dt_b_fed_asin_title))

---

### Post by peyre on 2024-11-04
Over the weekend I wiped the drive and reinstalled 24.04.1 from scratch, and the drive works now.  Not sure what changed to break it.

It's probably better to be running the LTS version on my main system anyway.  Leave the smaller upgrades for my laptops.

---

