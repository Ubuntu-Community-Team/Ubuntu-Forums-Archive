---
title: "HDPARM = HDIO_SET_DMA failed: Inappropriate ioctl for device"
date: 2009-09-08
forum: Hardware
---

### Post by Saunatonttu on 2009-09-08
I would wanna test if hdparm speeds up my hard disk.

now the readings are: 

 Timing cached reads:   13542 MB in  2.00 seconds = 6780.60 MB/sec
 Timing buffered disk reads:  356 MB in  3.02 seconds = 118.07 MB/sec

but:

sudo hdparm -c3 -m16 -d1 /dev/sda

/dev/sda:
 setting 32-bit IO_support flag to 3
 HDIO_SET_32BIT failed: Invalid argument
 setting multcount to 16
 HDIO_SET_MULTCOUNT failed: Inappropriate ioctl for device
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_MULTCOUNT failed: Inappropriate ioctl for device
 IO_support    =  0 (default) 
 HDIO_GET_DMA failed: Inappropriate ioctl for device

---

