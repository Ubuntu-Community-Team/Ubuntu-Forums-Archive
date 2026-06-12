---
title: "Partition problems"
date: 2007-06-02
forum: Hardware &amp; Laptops
---

### Post by georgecm3 on 2007-06-02
I was trying to install Ubuntu on my friends laptop and for some reason I can't edit the partitions in GParted or the installation partition editor. The windows partition can be mounted though (I can access the files). Can someone please help me?

---

### Post by merlinus on 2007-06-02
A couple of things:

Did you defrag the windows partition several times first?  And did you set virtual paging to zero (it can be set back to something near the original size after installing ubuntu)?

Also, there may be a hidden restore partition that some OEMs (e.g. Dell) create.

And did you use the gparted live cd?

hth....

-merlin

---

### Post by ugm6hr on 2007-06-03
> **georgecm3 said:**
> I was trying to install Ubuntu on my friends laptop and for some reason I can't edit the partitions in GParted or the installation partition editor. The windows partition can be mounted though (I can access the files). Can someone please help me?

GParted on Ubuntu seems unable to resize/move NTFS (most modern Windows) partitions.  Try GParted on the GParted LiveCD.

---

