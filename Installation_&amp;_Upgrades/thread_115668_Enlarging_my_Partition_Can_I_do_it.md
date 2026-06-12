---
title: "Enlarging my Partition? Can I do it?"
date: 2006-01-11
forum: Installation &amp; Upgrades
---

### Post by shade11 on 2006-01-11
I have decided to make my Ubuntu partition larger. That is, if it is possible. I wanted to know how I can do that. And if I make the partition bigger than will all my information be kept? I wanted my hard drive to be a good 10 gigs for my Ubuntu partition and 30 gigs for Windows.

So in short; Can I enlarge my Ubuntu partition's size? And if so, can I keep all my existing data?

---

### Post by joselin on 2006-01-11
Sure you can. Just use gparted. You can keep all your data, but if i were you i will backup all existing data before.

```
sudo atp-get install gparted
```

Regards.
Jose

---

### Post by Sef on 2006-01-11
You can't enlarge a partition with GParted if it is on the root partition because that is mounted.

Best way to partition is to use the Breezy Live CD.  

Applications -----> System Tools ------> GParted

---

### Post by shade11 on 2006-01-11
Ok, well I am going to try it out now I will tell you wether or not I am successful.

---

