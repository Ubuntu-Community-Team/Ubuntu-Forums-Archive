---
title: "Help choosing partition formats!"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by peter_q on 2009-03-18
Hello. I'm using linux for the first time.

So I'm trying to install and dual boot it, and my friends recomended that I have Vista on one partition, ubuntu on another, and All my personal files on a third partition seperate from program files.

So I was lookin up how to do this, and I came across a problem. I want both OS's to be able to access the middle partition. So what should my partition formats be?

I know Vista likes Her NTFS and can't write on a FAT 32 setup. But I've heard that Ubuntu cant use NTFS very well... So I'm stuck here. :p

---

### Post by taurus on 2009-03-18
Linux can read and write to ntfs filesystem just fine with ntfs-3g driver which should be already installed on your machine if you install Ubuntu.

---

### Post by upchucky on 2009-03-18
ext3 is what you need for the ubuntu partition, ubuntu handles read/write to windows ntfs just fine also.

should have the ubuntu home partition on its own ext3 partition too, ubuntu should have 25g and the home partition can be as big as you want it to be.

if you did not make a separate partition for ubuntu home, it is easy to make it later there are instructions here somewhere to do this.

---

