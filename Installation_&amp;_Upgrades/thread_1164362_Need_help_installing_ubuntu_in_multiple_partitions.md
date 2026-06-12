---
title: "Need help installing ubuntu in multiple partitions"
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by DJ_Crash on 2009-05-19
can somebody help me in installing ubuntu in multiple partitions im a little confused i keep ending up with 2 grub loaders below is a screen shot of my partitions

---

### Post by cariboo on 2009-05-19
First off, what is it that you are trying to do, at most all you need is 3 partitions, / /home and swap.

From your attached screenshot you don't have any mount points set for your partitions. What i would do, is delete all the ext3 partitions you have setup, and then create a / partition of about 10Gb and use the rest of the space for /home.

---

### Post by DJ_Crash on 2009-05-19
these partitions are left over from debian sid (testing) i want to re use them in ubuntu jaunty

---

