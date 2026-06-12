---
title: "DMA problems"
date: 2005-09-21
forum: Hardware &amp; Laptops
---

### Post by clueless on 2005-09-21
Hello to everyone,

I have tried Ubuntu linux since the first version and I have always liked it only that I couldn't get DMA to work on either disks, CDROM, CD-R/RW. I have tried every solution but it seemed that my motherboard (QDI K7S746FX - S746FX chipset) was not supported and I needed to recompile the kernel. Beeing a newbie I couldn't do that so I just tried every other distro available. Recently I decided to come back to Ubuntu to retry. But I have added another hard disk. So while my previously configuration was:
Primary Master: HDD
Primary Slave: DVD-ROM
Secondary Master: CD-R/RW
Secondary Slave: none

My new configuration is
Primary Master: HDD
Primary Slave: DVD-ROM
Secondary Master- DVD-R/RW
Secondary Slave: HDD

So I changed my CD-R/RW into a DVD-R/RW and added a HDD to the free channel. The result was that after installation I have DMA on in all channels without having to change anything manual. I have no idea as to why this happened but I'm just sharing here hoping that this information might be useful to anyone else.

---

### Post by heimo on 2005-09-21
Happy to see you're back and finally got it working! :) Remember me?

Just for records, what does your
 ```
lsmod | grep sis
``` 
show?

Cheers!

---

### Post by clueless on 2005-09-21
Hello again!

Yes ofcourse I remember you, you helped me a lot. I reinstalled ubuntu to try again to compile the kernel only that this time there was no need.

```
sis900                 18436  0 
i2c_sis96x              5380  0 
i2c_core               21264  3 bttv,i2c_algo_bit,i2c_sis96x
sis_agp                 8068  1 
agpgart                31784  1 sis_agp 
sis5513                15112  1 
ide_core              118988  4 ide_cd,ide_generic,ide_disk,sis5513
```

Is there any other information I could post that could turn useful to anyone because I have absolutely no idea what might have happened, I am only glad it works.

---

