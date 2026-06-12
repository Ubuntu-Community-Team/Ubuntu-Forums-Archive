---
title: "Can't burn on Acer Travelmate 4672 (Feisty)"
date: 2007-09-18
forum: Hardware &amp; Laptops
---

### Post by ril560 on 2007-09-18
I've been having trouble getting CDs or DVDs burning in Ubuntu. I believe the problem is that DMA is turned off. I've already followed some basic guides for turning it on, but with no luck. Can anyone help?

---

### Post by linuxwizard on 2007-09-20
[https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)

---

### Post by ril560 on 2007-09-25
That's one of the pages I've tried using. The problem is every time I try using hdparm I get an error:

> sudo hdparm /dev/scd0 

/dev/scd0:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

also:

> sudo hdparm -d1 /dev/scd0 

/dev/scd0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

From what I gather, I'm probably getting this error because the drive is scd0 and hdparm isn't suppose to work with scsi/sata. Also, from what I gather, my DVDRW isn't sata, I think it's pata (not really sure how to verify). So I'm not sure what's up.

Any further help would be appreciated!

EDIT: I have burned DVDs and CDs using this laptop before on previous versions of Ubuntu.

---

