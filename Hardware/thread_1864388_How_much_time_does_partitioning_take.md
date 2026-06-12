---
title: "How much time does partitioning take?"
date: 2011-10-18
forum: Hardware
---

### Post by Superdude_123 on 2011-10-18
I'm partitioning a new 3 TB external hard drive to ext4, and I'm wondering how long would such a thing usually take?

Also, does Ubuntu 9.10 have any problems working with an ext4 external hard drive?

---

### Post by Bmonsterboy on 2011-10-18
Should not take long, only around 15 mins or so with Gparted. And the other answer is no.

---

### Post by Superdude_123 on 2011-10-18
I've been at this for the last 30 min, so could something have gone wrong or should I switch to a newer PC with USB 2.0 or 3.0 instead of slow point O (1.0)?

GParted is in the phase of "create new ext4 file system" and looks to me like it used the following command:

mkfs.ext4 -j -O extent -L "3TB" /dev/sdb1

Should I kill it and start it on an other pc?

---

### Post by Bmonsterboy on 2011-10-19
How is it going? Sorry I had to go offline. I guess 3TB moght take a little while...
But if it is still going, switch to a PC with whatever the hard drive is capable of (Probably 2.0 unless it stated otherwise)

---

