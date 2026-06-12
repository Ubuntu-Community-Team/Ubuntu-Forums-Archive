---
title: "What does it mean by the super user is reserving 5% of the blocks?"
date: 2010-05-02
forum: Hardware
---

### Post by ownaginatious on 2010-05-02
So I'm formatting a 3 TB hard drive RAID using mkfs.ext3, and I've noticed that it says that 5% of blocks are being reserved for the superuser.

Now if what I'm understanding is correct, that means ~150 GB are being "reserved" for the superuser.

What is the purpose of this? Do I have to give these blocks to the super user?

I'd rather have them for myself :p.

Thanks.

---

### Post by P4man on 2010-05-02
Its a feature of Ext. It helps preventing fragmentation, and severe problems in case your drive is full. Its generally a good thing, but you might want to reduce that amount a bit on such a large drive.

have a look here:
[http://tombuntu.com/index.php/2009/03/11/free-disk-space-by-reducing-reserved-blocks/](http://tombuntu.com/index.php/2009/03/11/free-disk-space-by-reducing-reserved-blocks/)

---

