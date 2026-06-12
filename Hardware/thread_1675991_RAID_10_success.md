---
title: "RAID 10 success"
date: 2011-01-26
forum: Hardware
---

### Post by YesWeCan on 2011-01-26
I usually visit this forum with a problem I am frustrated with or to try to be helpful to someone else. For a change, I wanted to express my glowing satisfaction with RAID 10 support.

I use 10.0.4 64-bit and discovered RAID 10 recently while exploring SSDs. Using 4 WD 1TB Caviar Black drives (which seem pretty cheap at the moment) I managed to create a clean install of Ubuntu across 4 1TB partitions and set up a RAID 1, 100MB partition for boot, thus enabling rebooting even if a single drive were removed. I cannot claim this is a trivial installation and I find the 10.0.4 alternate CD installer somewhat unintuitive. However, after much online consultation from sites such as this I got through it.

And what a reward. My system runs significantly faster now. When I did a 'dd if=/dev/md0 of=/dev/null bs=10m count=500' the speed comes out at 240MB/s compared to 70MB/s without the RAID. This is actually faster than the same test run on my brother's SSD drive. Not a typical performance scenario, admittedly, but it shows how fast a RAID 10 can be.

So I now have a 2TB redundant array containing Ubuntu OS and all my files, with similar performance to SSDs and MUCH cheaper. \\:D/

---

