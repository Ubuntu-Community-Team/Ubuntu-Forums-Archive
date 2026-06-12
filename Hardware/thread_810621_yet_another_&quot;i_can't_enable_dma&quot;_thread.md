---
title: "yet another &quot;i can't enable dma&quot; thread"
date: 2008-05-28
forum: Hardware
---

### Post by paranoid_humanoid on 2008-05-28
hi,
i tried everything from every thread in every forum i found on google regarding this problem..
my device name is /dev/hdb, a dvd-cd writer..

$ sudo hdparm /dev/hdb:
/dev/hdb:
 IO_support    =  0 (default) 
16-bit)
 unmaskirq     =  0 (off)
 using_dma     =  0 (off)
 keepsettings  =  0 (off)
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

$ sudo hdparm -d1 /dev/hdb:
/dev/hdb:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma     =  0 (off)

i added piix and ide-code to my /etc/modules at the very top before any other module is loaded..
the weird thing is, that dma worked for a couple of times without me doing anything at all, but it didn't work again after i rebooted..
i didn't do anything to it! i swear!
what is happening to my computer? someone help me please, it just took me an hour to write a dvd :'(

---

### Post by zgornel on 2008-05-28
Probably it is a SATA device, you should not worry, it works as it should ;) Do you have abnormal CPU usage or buffer underruns when burning dvds ?

---

### Post by paranoid_humanoid on 2008-05-29
actually it's not. it's an IDE device, my harddrive is SATA but my dvd drive isn't..
it used to work on windows very smoothely, yesterday it took me like 50 minutes to write 4.1 GB to a dvd :(

---

