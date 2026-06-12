---
title: "default CFQ scheduler bug"
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by nailujk on 2008-12-29
This just a comment on my recent install of Kubuntu 8.10.

Installation went fine, but after a short while, the desktop would become very sluggish. Writes to the hard drive would virtually cease and reads would become progressively worse until eventually the system becomes unusable. From this point, the only remedy is a hard reset. After some research, I came to the conclusion that it was a bug in the current implementation of the CFQ IO scheduler in recent kernels. To fix this problem I added these two lines to /etc/rc.local:

echo -n deadline > /sys/block/sda/queue/scheduler
echo -n deadline > /sys/block/sdb/queue/scheduler

thereby setting the default IO scheduler to the deadline scheduler for both my drives at boot time. This fixed the problem. There is a slight decrease in performance, but that is better than having an unstable system.

This problem doesnt seem to happen for everybody, only some people. It also only seems to happen in certain circumstances. For me is was heavy writing, like copying a 350Mb file from my server to my desktop. Judging by the symptoms that people on these forums describe, it seems also that this problem is often mis-diagnosed.

The bug seems to have creeped in somewhere after 2.6.18 because debian etch uses 2.6.18 and uses the CFQ scheduler by default. And it works perfectly.

Maybe the Ubuntu kernel team can switch the default scheduler to the deadline scheduler in the meantime until upstream fixes the problem.

My machine specs are:

AMD Athlon X2 6000
6Gb RAM
Seagate 160 Gb HDD (Windows)
Seagate 320 Gb HDD (Linux)
Asus M2V - VIA K8T890 chipset
Audigy Sound Blaster Audigy 4 Pro
Nvidia 9800 GT

---

