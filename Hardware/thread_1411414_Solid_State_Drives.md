---
title: "Solid State Drives"
date: 2010-02-19
forum: Hardware
---

### Post by Neezer on 2010-02-19
Does linux, specifically Ubuntu, work well with solid state drives? Any experiences or reading materials I can use to look into them? I'd be looking for one for my laptop.

---

### Post by steveneddy on 2010-02-19
They must work well due to the fact that System76 offers a SSD in most of the laptops they carry.

---

### Post by Neezer on 2010-02-20
Any other input from the masses?

---

### Post by IcarusR on 2010-02-20
Googling 'linux ssd' gives plenty of reading material

---

### Post by hxcobd on 2010-02-20
I'm using one right now, actually.

My system is a Thinkpad X41, just put the SSD in yesterday. It's a Samsung 60-gig solid state.

Works like a charm. System had no problems recognizing it, formatting it, or installing linux. Smooth sailing.

However, one thing to note: Apparently 9.10 has a widely-known issue of the disk utility that runs at boot giving false positives on errors for a lot of SSDs.

The drives work fine, but for some reason, the utility sees them as super corrupt and with a ton of bad sectors. It's a known issue/bug with the disk utility, and there's nothing actually wrong with the disk drives.

---

### Post by Neezer on 2010-02-25
I'm a little worried about a few things...I have an HP dv6 that I want to put it in. I am looking at a SATAII drive, but I'm not sure that my laptop has SATAII.

Also, I can't really tell if I will be able to continue to use my regular hdd for storage.

---

### Post by dabl on 2010-02-25
I've been running Linux on my Asus EeePC 4G/701 for almost 2 years now (OK, actually my wife is the user of it).  It is a ext2 filesystem.

Ted Ts'o is the principle ext4 filesystem developer. Regarding running ext4 on a SSD, he wrote this a year ago:

[http://thunk.org/tytso/blog/category/computers/ssd/](http://thunk.org/tytso/blog/category/computers/ssd/)

---

