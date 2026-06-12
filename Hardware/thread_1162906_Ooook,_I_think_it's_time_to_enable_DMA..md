---
title: "Ooook, I think it's time to enable DMA."
date: 2009-05-18
forum: Hardware
---

### Post by MarcelloSav on 2009-05-18
Hey Guys,
I have an "old" PC, an AMD 3200, bought I think in 2003.
When I upgraded to 8.10, i began to notice a strange CPU load during drag'n'drop end copy of files. I never noticed something similar with previous versions, but since I had no problems with cds and dvds I didn't care about it. But since I upgraded to Jaunty, my problems became heavier.
I have two hds, PATA, and old Maxtor (sincerely I don't know how it is still working :D ) 120 gb, and a 160 gb Western Digital.

Now:
```
marcello@kidA:~$ sudo hdparm /dev/sda
[sudo] password for marcello: 

/dev/sda:
 IO_support    =  0 (default) 
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 19457/255/63, sectors = 312581808, start = 0
marcello@kidA:~$ sudo hdparm /dev/sdb

/dev/sdb:
 IO_support    =  0 (default) 
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 14946/255/63, sectors = 240121728, start = 0

```

If I try to enable DMA by

sudo hdparm -d1 /dev/sda

I have this problem
```
marcello@kidA:~$ sudo hdparm -d1 /dev/sda

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device

```

The same thing on  /dev/sdb.

But it's not only a problem of dma. Even if I try to set IO_support to 32 bit, it gives me a similar problem:
```
marcello@kidA:~$ sudo hdparm -c1 /dev/sda

/dev/sda:
 setting 32-bit IO_support flag to 1
 HDIO_SET_32BIT failed: Invalid argument
 IO_support    =  0 (default) 
```

Can anybody help me?
Thanks all of you guys,
m!

---

### Post by smorar on 2009-05-22
It might not be setting because it's currently mounted.
Try setting the appropriate option in /etc/hdparm.conf

---

