---
title: "Extend my current partition"
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2009-02-13
My partition is almost full, I want to extend it is it there a console command to do it.
I am googling but not good cnadidate yet.

---

### Post by avtolle on 2009-02-13
You will need to do this with the partition unmounted, thus the need to boot from a Live CD (either the Ubuntu Live CD or a Live CD from Gparted) unless you are booting from another OS that doesn't mount that partition, then select the partition in question for resizing/moving. It goes without saying that you should back up your files before doing anything with the partition. Good luck.

---

### Post by Mark Phelps on 2009-02-14
I've personally found that GParted LiveCD to be the best choice -- basically because they update the version frequently.

Be aware, though, that it can take a LONG time to resize a partition.  So, don't be surprised if it takes an hour or more.

With the LiveCD, you can watch the details and see the progress as it goes.

---

