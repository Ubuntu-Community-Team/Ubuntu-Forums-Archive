---
title: "Dual-booting with Ubuntu and 4MB Vista??"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by Kobayashi-kun on 2009-01-31
If I make a partition half and half with Ubuntu 8.10 on one and a 4MB version of Vista, will my laptop be ok with running both of them?

Again, just wondering....

---

### Post by binbash on 2009-01-31
Yes but default ubuntu installation may require more than 4-5gb.You may consider vlite to slim down the vista (2gb or 2.gb)

---

### Post by Kobayashi-kun on 2009-01-31
> **binbash said:**
> Yes but default ubuntu installation may require more than 4-5gb.You may consider vlite to slim down the vista (2gb or 2.gb)

Thats brilliant. But did you read the title? "...4MB Vista"!
So my Ubuntu partition will be fine with the 4MB Vista partition?

---

### Post by Mark Phelps on 2009-02-01
OK, smart one, what does "make a partition half and half" mean???  

Does it mean splitting a single NTFS partition into two NTFS partitions -- if so, the answer is NO -- Ubuntu will NOT be happy with that.  

Does is mean trying to install Ubuntu inside the existing NTFS partition but allocating it half the space -- if so, YES, Ubuntu will be happy with that.  

Does it mean shrinking the partition to half its size then creating a second partition of equal size but formatting the second partition as Ext3 -- then YES, ubuntu will be happy with that.

Next time, instead of flaming us with being "brilliant" when we try our best to understand what your vaguely worded question means, why not take the time to tell us, in detail, what you are trying to do.  That way, we won't have to guess.

---

