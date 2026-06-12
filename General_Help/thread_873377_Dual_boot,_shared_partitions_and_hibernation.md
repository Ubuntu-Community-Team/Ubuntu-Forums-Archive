---
title: "Dual boot, shared partitions and hibernation?"
date: 2008-07-28
forum: General Help
---

### Post by mythmon on 2008-07-28
I have a Dell Inspiron 1520 laptop. (I don't think the particular model matters, but I'll mention it) I would like to dual boot Windows and Ubuntu. I have a large amount of data that I would like to share between the two OSs. 

My first attempt of this was to put the shared data on the windows partition and access it from linux using the built in NTFS driver. This worked just fine, except if I hibernate Windows. (which I would really like to be able to do) Windows locks the NTFS partition, and Ubuntu won't mount it, except read only. (which won't work for me)

My next attempt was to make a third partition to share between the two. If I use NTFS for the third, windows will lock it. If I use ext3 for the partition, and use ext2IFS to get windows to read it, Ubuntu locks it on hibernate. Both of these are understandable, albeit undesirable.

Finally I tried to use fat32 for the shared partition. I'm not sure how hibernate will affect this, but it seems to have caused Windows to be unstable. I have got three blue screen crashes since making the shared partition fat32.

Is there a standard way to do this that I'm missing? I am beginning to think that this is one of the kind of things that doesn't really happen with dual boots. Like running both OSs at once. :)

---

### Post by abazoskib on 2008-07-28
good question, I'd be interested in that also! perhaps [http://en.wikipedia.org/wiki/Samba_software](http://en.wikipedia.org/wiki/Samba_software) would have the answer?

---

