---
title: "DMA won't turn on ... ?"
date: 2006-01-15
forum: Hardware &amp; Laptops
---

### Post by dbee on 2006-01-15
So I followed the ubuntu wiki for accessing dma [https://wiki.ubuntu.com/DMA]("https://wiki.ubuntu.com/DMA") 

I'm using a scsi drive - instead of my harddrive being at /dev/hdc, mine's at /dev/sda1

when I attempt to add DMA I get 
```

/dev/sda1:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

```

Is there a different method to setup DMA on scsi ? 
And if so, then why isn't it in the wiki ?

---

### Post by nalmeth on 2006-01-15
have you tried automatix? I don't know exactly how *it* installs DMA, but it might work for you..
its near the bottom of the list of apps, if you haven't tried yet.
ubuntuforums.org/showthread.php?t=66563

---

### Post by handy on 2006-01-15
Automatix is great, get it here:

[http://ubuntuforums.org/showthread.php?t=80295](http://ubuntuforums.org/showthread.php?t=80295)

It will give the choice to painlessly install many usefull things. :D 

I don't believe that DMA is appropriate for the SCSI bus though.

If I'm wrong someone will say so pretty quick!

All the best.

---

