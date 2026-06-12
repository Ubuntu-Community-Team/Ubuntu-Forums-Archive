---
title: "what will happen to ext3 in the next 9.10 update?"
date: 2009-07-04
forum: Installation &amp; Upgrades
---

### Post by jittopjose on 2009-07-04
i am currently using ubuntu 9.04. i used all the ubuntu versions till date. all the time i used to reinstall the whole system for new released. but this time, i mean 9.10 version, i am supposed to upgrade. currently i am using ext3. i heard that, 9.10 will be using ext4 as default file system. what will happen if i upgrade?, will it upgrade my ext3 to ext4?.. or they stay with ext3 for upgrads?.
Thanks,
Jitto P.Jose

---

### Post by darolu on 2009-07-04
It will stay with ext3 I'm pretty sure you need to re-format a HD partition to change its files system; but is OK you won't have any problem at all; you can even use ext2, is just a file system, the difference between ext3 and ext4 is ext4 supports 64-bit storage limits and better performance; although I've noticed a slightly better performance with ext3.

Unless you are going to use a very (and I mean VERY) large hard drive, say up to 1 Exabyte and single files up to 14Terabytes, you don't really **need** to use ext4, so don't worry about it, ext3 is great it also has journalling.

---

