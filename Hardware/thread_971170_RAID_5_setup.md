---
title: "RAID 5 setup?"
date: 2008-11-04
forum: Hardware
---

### Post by rhcm123 on 2008-11-04
I will soon going out and buying a cache of hard drives, and I will be using them to augment my filing server.
I am going to set them up in a RAID 5 arrangement (I belive this will be the best, although i am considering RAID 1 for redundancy). I will be using 4 disks controlled of a hardware controller.

I have several questions:
- I currently have a 250 gb hdd that I want to reuse in the array. Do all the disks have to be the same size or can the be different?
- How do I setup the array? (I will be using EIDE)
- Are there any other good forms of raid i'm missing?

---

### Post by psusi on 2008-11-06
Yes, they all need to be the same size.  If it is a hardware raid controller then you set it up using the bios utility.  If it is a fake hardware raid then you might want to read [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto).

---

### Post by rhcm123 on 2008-11-07
Thanks! Finally, someone responds!!!

---

