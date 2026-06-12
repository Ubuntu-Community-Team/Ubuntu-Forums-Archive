---
title: "No permission to turn on DMA for /dev/sda1"
date: 2006-11-20
forum: Hardware &amp; Laptops
---

### Post by djvishnu on 2006-11-20
I am having problems with choppy sound, and I got a tip to check if my hd is configured to use dma. This is the info i get:

```
0 vishnu@vaio:~> sudo hdparm -v /dev/sda  
/dev/sda:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 12161/255/63, sectors = 195371568, start = 0

```

This means DMA is not enabled for this device, am i right?
When i try to enable it manually, i get this error:

```
0 vishnu@vaio:~> sudo hdparm -d1 /dev/sda 

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
```

I have googled a bit, but I haven't found anything that helps. Does anyone have an idea on how to fix this?

PS. My sound problems started after my last dist-upgrade, maybe 2 weeks ago. Please let me know if you think the problem lays elswhere.

---

### Post by andree182 on 2006-11-20
i'm just guessing - if you have /dev/sda device, it means that you're using a sata/scsi drive. In that case you can't/don't have to set dma mode - it is used automatically (afaik). The dma mode is optional just with standard ata drives (cdroms, older hdds etc.)

---

### Post by djvishnu on 2006-12-04
Turns out it was my Nvidia driver that didnt play well with my soundcard. Just upgraded to the 97-something beta, and the problem went away!

---

