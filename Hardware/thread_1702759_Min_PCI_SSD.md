---
title: "Min PCI SSD"
date: 2011-03-08
forum: Hardware
---

### Post by jlparsons on 2011-03-08
Hi folks, am running 10.10 on a fairly small 5400rpm laptop hard drive with full encryption so I'm thinking of ways to speed things up.  Obviously an SSD would be the best option but these are expensive and I need 250Gb storage ideally - out of budget.  I topped up my ram and am using preload with a generous cache which helps but things sometimes still drag.  I've got a free mini pci slot and am thinking about a mini pci ssd of 16Gb for / and then /home and swap (which hardly ever gets used on my system) on my regular disk.  I have two questions:

Would I notice much difference?  These things seem to offer around 110ish mb/s read speeds which aren't that much higher than a regular disk (mine's 82 mb/s according to ubuntu's benchmarker), however access times and latencies would (I assume?) be far better with the SSD.  Anyone have any insight?

Is 16Gb enough for / these days?

---

### Post by DanneStrat on 2011-03-08
> Is 16Gb enough for / these days?

16 GB would be plenty of room for "/"

I can't answer your question about

SSD disks as I haven't got any

experience with them.

Good luck.

---

### Post by dabl on 2011-03-08
16GiB is way plenty.

I run Debian Sid KDE on a OCZ 120GiB PCI SSD.  I don't need encryption.  It boots in about 21 seconds.

I would say that if you run your OS unencrypted on the 16GiB SSD, then that's going to give you a faster boot, and the OS should run significantly faster than if it were encrypted, and also use less memory in the process.

But, if your data is still encrypted on the old hard drive, then I don't see that data operations would be improved any.  I guess the question of "value" boils down to the amount of the present sluggishness that is due to operating system functions, versus the amount that is due to opening and saving data files.

---

