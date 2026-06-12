---
title: "Installing on Virtual PC"
date: 2006-01-02
forum: Installation &amp; Upgrades
---

### Post by mckennas on 2006-01-02
When installing Ubunto 5.1 on Virtual PC , the install gets to a point where you have 3 choices regarding partitioning:

1. Erase entire disk
2. Erase entire disk and use LVM
3. Manally edit partition table

I get to this point no matter which install I choose: Sever, PC or Live DVD. Without knowing what will happen I can't proceed. I am looking on the Web for tips on VPC and Linux. Any ideas?

Thanks !!

---

### Post by abandoned_hussam on 2006-01-02
First, you should create a virtual disk. Virtual PC should offer a wizard for that. 
During the install, choose "erase entire disk". This will let you use the whole virtual disk you created.

---

### Post by mckennas on 2006-01-02
That worked. Thanks !! I feared that the install would overwrite my Windows partition but based on your reply I let it "erase" the partition and then let it do its thing. Success !!

---

