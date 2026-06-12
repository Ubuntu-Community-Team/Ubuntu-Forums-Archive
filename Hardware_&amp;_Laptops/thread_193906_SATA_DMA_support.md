---
title: "SATA DMA support"
date: 2006-06-10
forum: Hardware &amp; Laptops
---

### Post by Juancho on 2006-06-10
Hi,

I'm having problems enabling DMA support for my two SATA drivers. After reading several posts (and this [wiki page]("https://wiki.ubuntu.com/DMA")) I found that a command like this would do:

```
sudo hdparm -d1 /dev/sda
```
But it shows this error:

```
/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
```
In other posts people are suggesting recompiling the kernel. Is this really needed to enable DMA support for a pretty standard SATA drive ? Isn't there other way ?

Thanks in advance,

- Juan

---

