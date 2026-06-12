---
title: "Should I use SD card for Swap?"
date: 2008-12-01
forum: General Help
---

### Post by madhatter563 on 2008-12-01
Would it be worthwhile/efficient to an SD card [SanDisk ultraII (2GB)]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820180616") as swap space? I would assume this may be faster than using the HDD for swap or at least use less power. How would I direct the system to go to the SD card for swap instead of the HDD's swap partition?

Thanks!

---

### Post by sdennie on 2008-12-01
How much physical RAM do you have?  Are you sure you are even using and swap space?  The output of the following might be useful after using your machine normally for a few hours:

```

free -m

```

Using an SD card may not be a good idea for swap as they only have a limited number of writes.

---

### Post by HermanAB on 2008-12-01
No, SD cards are very slow.  These things use multi-level flash memory and are much slower than a hard disk, with throughput as low as 7 MB/s, while a hard disk will be around 40 MB/s.

Transfer a large file and test it yourself using 'dd'.

Cheers,

Herman

---

### Post by albandy on 2008-12-01
You can, but don't do it, SD cards are not designed for intensive writings, and you will break it.

---

### Post by snowpine on 2008-12-01
Try copying a large file to your SD card, then your HD, and time which is quicker. :)

I don't think you'll see a performance boost by moving swap to SD.

---

### Post by madhatter563 on 2008-12-01
@vor - I have 2GB internally.  And thanks for that cmd "free -m" I see I'm only using ~1/2 of my memory currently, and none of swap.  

Thanks for the quick responses.  I'll just have to find another use for my SD card then :-P

---

