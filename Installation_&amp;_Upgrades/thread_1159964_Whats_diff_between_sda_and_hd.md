---
title: "Whats diff between sda and hd?"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by jonnyl888 on 2009-05-15
Everyone is going on about sda1 sda2 and like hd0,1 and hd0,2. Whats the difference and is there a way to list both sda number and hd number?

---

### Post by 73ckn797 on 2009-05-15
> **jonnyl888 said:**
> Everyone is going on about sda1 sda2 and like hd0,1 and hd0,2. Whats the difference and is there a way to list both sda number and hd number?


sda = hd0 & hd0 = sda
sdb = hd1 & hd1 = sdb
and so forth. When you talk sda you are talking hd0.

No difference other than grub designates the hd and Ubuntu/Linux uses sd

---

### Post by jonnyl888 on 2009-05-15
No what i mean is each individual partition. My sda6 is actually hd0,5 why is this? And how can i chrck the other partitions?

---

### Post by 73ckn797 on 2009-05-15
> **jonnyl888 said:**
> No what i mean is each individual partition. My sda6 is actually hd0,5 why is this? And how can i chrck the other partitions?

The hd designation begins at "0" and the sd begins at "a". So, 0 = a, 1 = b etc. In another way sda1 = hd0,0, sda2 = hd0,1. A second drive would list as sdb1 = hd1,0.

sda1 would be the first drive, partition 1. If there is more than 1 partition on that drive then the other would be sda2 or hd0,1.The swap partition jumps ahead so do not let that confuse you. It will all make sense and be second nature in your thinking.

---

