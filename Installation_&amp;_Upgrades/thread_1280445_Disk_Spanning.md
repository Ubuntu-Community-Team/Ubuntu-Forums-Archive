---
title: "Disk Spanning"
date: 2009-10-02
forum: Installation &amp; Upgrades
---

### Post by cj100570 on 2009-10-02
I've been a happy Ubuntu user since 2006 but I've recently run into an issue that I can't quite figure out. I have Ubuntu installed on a 500GB hard drive. I have a spare 200GB hard drive that I'd like to reinstall Ubuntu on but have it span across the 500GB drive also. In Fedora, Sabayon and a few other distros I've tried this is as easy as selecting both drives during installation. I have found no choice for that in Ubuntu and no tutorial for such a situation. Anyone have any help you can offer on this? :popcorn:

---

### Post by lemming465 on 2009-10-03
If you are talking about using LVM (logical volume manager) to create multiple physical volumes (partitions) which contribute to a large logical volume using pieces of both disks, you need to use the *alternate install* CD.  The live desktop CD is designed for people with simpler disk setups.

---

### Post by cj100570 on 2009-10-03
> **lemming465 said:**
> If you are talking about using LVM (logical volume manager) to create multiple physical volumes (partitions) which contribute to a large logical volume using pieces of both disks, you need to use the *alternate install* CD.  The live desktop CD is designed for people with simpler disk setups.

I'm using the alternate install cd. That's always my chosen install method because I like to encrypt my drive. I've managed to successfully get the partitioner to see both drives and strip them together for Raid0 but then it always complains of not having a root partition. I'm at my wits end here. This should be a much simpler process. As I noted above, Fedora, Sabayon, and openSUSE make it a simple matter of checking a box.

---

