---
title: "Gateway Laptop Dual Boot"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by whalogreg on 2009-04-26
I recently got a Gateway MD7818U laptop as a gift.
Specs
-Windows Vista Home Premium (64 bit)
-2.0Ghz Intel Core 2 Duo T6400
-4.0Gb RAM
-500Gb Hard Drive

I want to install Ubuntu 8.04 on the new laptop, but I am a bit hesitant due to some of the horror stories I've been reading about bootloader problems, losing Vista after installing Ubuntu and even due to the partitioning the hard drive. I am curious if anyone with this same laptop has a success story with a dual boot and could guide me on the proper way to do so. One of couple reasons I want someone with the same laptop is due to the hard drive. When I bought it, it said it had a 500Gb hard drive, and when I looked under My Computer in Vista it listed two 227 hard drives. One listed as "OS C:" and one as "DATA D:". I am not sure if these are two individual drives or one partitioned drive (I'm assuming the latter), and am not sure how this would effect the partitioning/installation.. But any help would be wonderful.. 

Thanks

---

### Post by groman88 on 2009-05-12
Yea bro i have the same laptop and have successfully dual booted Ubuntu, Vista, and windows 7! Ok first off all, my hard drive was partitioned with the DATA D: and I just deleted it. In the data partition you can install your programs and keep it separate from  OS in case a virus breakouts. I don't really care so I just deleted it. 

I recommend doing a manual install. If you do this you'll need some partition software to partition an empty space on your hard drive. Use Gparted

[http://gparted.sourceforge.net/index.php]("http://gparted.sourceforge.net/index.php")  

Ive done a lot of crazy **** to my comp :-P, so feel free to ask me anything, i might be able to help. Within the next few weeks I might do a video on youtube to help others out too.

---

### Post by mike_j_w on 2010-04-25
> **groman88 said:**
> Yea bro i have the same laptop and have successfully dual booted Ubuntu, Vista, and windows 7! Ok first off all, my hard drive was partitioned with the DATA D: and I just deleted it. In the data partition you can install your programs and keep it separate from  OS in case a virus breakouts. I don't really care so I just deleted it. 

I recommend doing a manual install. If you do this you'll need some partition software to partition an empty space on your hard drive. Use Gparted

[http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)  

Ive done a lot of crazy **** to my comp :-P, so feel free to ask me anything, i might be able to help. Within the next few weeks I might do a video on youtube to help others out too.

Hi,

I recently dual booted a Gateway laptop (ubuntu and windows 7).

When I turn the computer on the following  two actions continually recycle.

     1. The Gateway logo appears.
     2. The Gateway logo is replaced by the following message in the upper left corner:  GRUB Loading

Anyone have any ideas what is going on and recommendations for how to proceed?  

Thanks,
Mike

---

### Post by oldfred on 2010-04-25
Lets see what is installed where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

