---
title: "HDD mounting issues"
date: 2007-12-19
forum: Hardware &amp; Laptops
---

### Post by ryan-wears-a-hat on 2007-12-19
hey, so i'm not sure how to fix this... btw: i am (was) using gutsy 64


i have 2 160Gib drives set up in a RAID 0 array through a PNY s-cure raid controller. it worked fine for about 2 months set up like this. then the other day it wouldnt boot.

so, after some trouble, i ran fsck on the drive. this is where i made my first mistake because it found an error, and i said 'y' to fix it. it wasn't until 300 more errors, that i realized fsck thought the drive was formated ext2, instead of ext3.

then i thought crap, ill just reset the RAID array, loose everything, and start again...but this didn't work either. i booted the live cd, hit install, (chose the guided - erase/use everything partition) and it gave me an error essentially saying it can't mount the partition it just made.

so, using gparted, i tried to create my own partition of the whole drive. and i could sort of do it. i could create ext2 partitions fine. but ext3 ones fail every time (it says it works fine, but then it's flagged as un-mountable). i didn't try every option, but of the ones i tried only ext2 ones worked. logically, i then formatted it ext2 and tried the installer again, and got the same error.

i think it's a mounting issue, but why wont a fresh install, using the whole array, return a mounting error? at this point i don't care about keeping any data still on the drives, i just want it up and running again. 

any help would be awesome! thanks!

---

