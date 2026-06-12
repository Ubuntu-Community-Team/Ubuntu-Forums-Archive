---
title: "Kernel Error with WL"
date: 2015-01-24
forum: Hardware
---

### Post by shawn27 on 2015-01-24
I am getting the below in my log

```

Jan 24 09:21:08 tux kernel: [52976.030772] wl 0000:06:00.0: swiotlb buffer is full
Jan 24 09:21:08 tux kernel: [52976.030773] DMA: Out of SW-IOMMU space for 2048 bytes at device 0000:06:00.0

```

and this eventually bring down all networking on the computer. I am using ubuntu 14.04 with kernel 3.13 and i have the iommu=soft parameter added but i am still getting the error. I am using the proprietary broadcom driver from ubuntu and i am on 64 bit OS.

lspc for the network shows the below:

```
06:00.0 Network controller: Broadcom Corporation BCM4321 802.11b/g/n (rev 01)


```

any help is much apprieciated as i have been trying to figure this out for days now.

---

