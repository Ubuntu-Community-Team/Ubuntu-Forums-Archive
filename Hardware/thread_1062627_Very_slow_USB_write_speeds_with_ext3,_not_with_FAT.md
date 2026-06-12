---
title: "Very slow USB write speeds with ext3, not with FAT32 and ext2"
date: 2009-02-07
forum: Hardware
---

### Post by oblidor on 2009-02-07
Hi

I just wanted to share what I found out with my USB stick as many seem to have slow transfer speeds for different reasons.

I bought a Corsair 16Gb GT, which should have write speeds of 13-14Mb/s. As I wanted to transfer a ubuntu ISO image I change the partition to linux and formated it as ext3. Then I tried to transfer a ~4Gb iso image. This took 25 minutes which gave 3Mb/s. I then tried with a file of 190Mb and this took 90 seconds which gives 2Mb/s. This is HORRIBLY slow for such an expensive stick that is supposed to do 13Mb/s

I then checked trasfer speeds with the 190Mb file on FAT32 and ext2 as well (ext4 doesn't work on 2.6.27 kernel). Here are the results:

   EXT3     90s   2Mb/s
   FAT32    17s   11Mb/s
   EXT2     17s   11Mb/s

Testing was done from terminal with *time cp*

So my recommendation would be to ditch ext3 and use ext2 for USB sticks. The journaling system seems to be horribly slow.

I have not tested ext2 vs ext3 on my external HDDs yet, but will do it soon.

Hope it helps.

PS: Test system: Ubuntu 8.10 (ext3 slow on 8.04 too). CPU Q9550, 4Gb RAM, Asus P5Q PRO P45, USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2

---

### Post by tormod on 2009-12-15
Actually, it is probably because ext3 use journaling by default (ext2 can not) that it is slower. You can use ext3 without journaling also. See [http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/) which is a very good read. If I understand correctly, the best for SSD (and USB flash drives also I guess) is to use ext4 but turn off journaling and use the noatime option.

See in particular comments #6 and #23 in tytso's blog post.

---

