---
title: "Minimum GB for U. to install?"
date: 2006-01-14
forum: Installation &amp; Upgrades
---

### Post by amwil1024 on 2006-01-14
My HD is 12.76 GB, I'm trying to set up partition, but keep getting message there's not enough room to install. How much GB does Ubuntu require? I've typed in as little as 5 GB for resizing my existing os (doing a dual boot) I thought Ubuntu required only around 6 GB to install?

---

### Post by bernardfrancois on 2006-01-18
I have Ubutnu 5.04 running on a laptop with only 6gb disk space. After installation, about 2gb will be used, but you can remove some software to make it about 1.5gb (and probably even smaller).

And it's no problem to have large partitions; I have a 92gb ext3 partition over here.

Maybe you didn't specify the right filesystem. 'Unused space' or 'Unallocated space' is not where you'll be able to install Ubutnu. You need to specify a file system type (like ext3). You'll also need to specify that it will contain the root directory '/' if it's not done automaticly.

---

