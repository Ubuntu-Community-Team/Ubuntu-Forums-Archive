---
title: "how do i defrag. (yes, i need to.)"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by notquitemichael on 2007-06-20
I've seem to run into a problem, much like the titanic.

According to the last fschk my video storage drive was over 25% non contiguous, which i take to mean it's pretty fragmented. I've looked around about how to defrag in linux and all i can find is articles telling me how i'll never have to defrag in linux. 

I'll admit as it's a video drive and the content's remained static on there for quite some time I haven't really noticed any performance loss but I find it a bit worrying that it is (i think it was 27.5%) defragmented and that there's nothing I can do about it.

It seems, for future purposes, the thing I did wrong was to fill it as the reason ext3 never needs defragmenting is because it leaves spaces between files. which doesn't work when it only has 3 / 500 gb left.

So, any ideas? or have we just not put any lifeboats on because we think it's un sinkable.

---

### Post by bluenova on 2007-06-20
There is a package called 'defrag'
```
sudo aptitude install defrag
```

I'm not sure if it does ext3 though as it only says ext2 in the description.

---

### Post by kerry_s on 2007-06-20
boot with the live cd, open the terminal and run> fsck /path/to/your/drive(ex: fsck /dev/hda)

---

### Post by notquitemichael on 2007-06-20
alright, i'm a bit weary of using the defrag as I can't backup my data (haven't got a spare 500gb) and it'll be annoying to lose. 

note to the previous poster that fsck doesn't defrag, else life would be easy :)

although searching around i've come across suggestions that ext doesn't actually suffer if defragmented? is this true?

---

### Post by floke on 2007-06-20
I don't think 25% is anything to worry about. There's a thread on this somewhere, in which people posted their non-contigious readings. There were some far far higher than this with no reported performance loss.

---

### Post by az on 2007-06-20
How full is the drive?  Ext3 filesystems will become fragmented when they are mostly full, and there is no way around it.

If this is not your root filesystem, then you will not notice any perfromance problems.

---

