---
title: "Everytime I boot back to XP it does a check disk? Says volume is dirty?"
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by abrrymnvette on 2009-09-02
I've been dual booting 9.04 and XP Pro on my Dell Inspiron 640m laptop for a couple weeks now. Everytime I go into XP from Ubunut it does a checkdisk and says the volumes are dirty? Is this b/c I'm mounting part of my XP partition to use as storage for Ubuntu? 

I have a 120gb HD, 90 for XP and 30 for Ubuntu. When I download stuff in Ubuntu, I save it in the XP partition.

---

### Post by Mark Phelps on 2009-09-02
> **abrrymnvette said:**
> ... Is this b/c I'm mounting part of my XP partition to use as storage for Ubuntu? ...

Yes -- presuming you're mounting your XP partition read/write, not read-only.

It's a BAD idea to mount the partition containing an MS Windows OS as read-write.  Any filesystem glitch will mark the partition as dirty and you will then have major difficulty mounting it again.

A much better solution is to create a shared data partition (preferably NTFS, so that, even if you get a filesystem glitch, your OS partitions remain untouched.

---

### Post by abrrymnvette on 2009-09-02
Got it, that's what I thought it was. Thanks.

---

