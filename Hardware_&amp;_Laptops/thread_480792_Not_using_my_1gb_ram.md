---
title: "Not using my 1gb ram"
date: 2007-06-21
forum: Hardware &amp; Laptops
---

### Post by Nuclearwombat on 2007-06-21
Ubuntu has detected the the full 1002.8mb of ram, but is not using it properly.

I'm running 7.04 ubuntu on a intel 2.8ghz, with 1gb of ram, and an automatically set swap file of 2.9gb. I have a pci nvidia 256mb card.

However, my ram usage is at a constant 16% in the system monitor, regardless of my activity, , and my swap file remains unused at all. This is then causing my cpu to max out to 100% every time i click or type. Graphics, music and video run fine once they load, but day to day usage(typing etc) is impossible, 5 second lag on typing etc, and application launching takes at least 30 seconds. As you can imagine this is most frustrating. Any idea how i can fix this?

Thanks.

---

### Post by CrispyFried on 2007-06-21
I think your swap is too big, set it down to a gig or so.

---

### Post by lizardorb on 2007-09-01
How do you lower the swap? I have the same problem the original poster had and I'm a noobie

---

### Post by davidsrsb on 2007-09-01
At one stage x86 was limited to 2GB swap. Under 2.6 kernels, 64 bit cpus support 100s of TB
Unfortunately some of the manpages are seriously out of date, so I really don't know where more recent 64 bit compatible cpus running 32 bit Linux 2.6 are now.

---

