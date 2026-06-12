---
title: "Partitioning Drives on Install"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by SuperNomad on 2009-02-20
I have a laptop with vista on and I've been using wubi for a month or so and I now want to install it properly.

However I only have 1 hard drive with 2 partition one with vista on. So when I went to install it on the second partion with is 58gb in size I wanted to make it 50gb for ubuntu and 2048mb for the swap (I have 1gb of ram) however the partion tool wouldn't allow me to split it into 2 partitions it could only set it to the maximum size of 58gb.

I'm going to partition my drive in windows, just want to see if I'm missing something.

I'm guessing I could also use gpart on the live cd.

Any help would be appreciated.

---

### Post by Pumalite on 2009-02-20
Use Gparted Live CD to prepare your partitions if you first allocated the space with Vista. Then install, go 'Manual' and pick the already prepared partitions

---

