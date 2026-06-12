---
title: "Enable DMA for HP dv5000 (AMD64 CPU)"
date: 2008-07-11
forum: Hardware
---

### Post by KDB9000 on 2008-07-11
I am having trouble enabling DMA for the hard drive and my DVD-RW DL (with Ligthscribe). I know my hard drive can support UDMA.

CD-ROM
```
sudo hdparm /dev/scd0

/dev/scd0:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

```

HDD
```
sudo hdparm /dev/sda

/dev/sda:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 19457/255/63, sectors = 312581808, start = 0

```

I have tried stuff from [https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)

Any thoughts? Even though the hard drive is sda it is an IDE drive. I am not 100% sure about the CD (if it is IDE or SATA).

---

