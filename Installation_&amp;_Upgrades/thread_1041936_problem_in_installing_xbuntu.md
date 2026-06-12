---
title: "problem in installing xbuntu"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by balaji_n on 2009-01-17
Hi all,
Earlier i installed Ubuntu 8.04 LTS as a single partition of 40GB. Then used GParted and created a new partition for 19.5 GB and formatted as ext3. Now i booted with xbuntu 8.04 LTS, it detects the new partition (19.5 GB, showing 320 MB used and remaining free), but when i choose to go forward, it says 'Too small size'. How can i install xubuntu and have it besides my Ubuntu 8.04 LTS. Please help me.

Regards,
Balaji

---

### Post by theozzlives on 2009-01-17
just install the Xubuntu desktop on Ubuntu

---

### Post by stefangr1 on 2009-01-17
Maybe you can also try to manually partition the free space. Then you just delete the (still empty?) 20GB partition, assign 1GB swap or so, the remaining part as ext3 / an you leave the partition of you Ubuntu install as it is (make sure it says it won't be formatted, which is default btw.)

---

