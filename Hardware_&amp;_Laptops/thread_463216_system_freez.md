---
title: "system freez"
date: 2007-06-03
forum: Hardware &amp; Laptops
---

### Post by fare85 on 2007-06-03
I at all, i have installed new kubuntu 7.04 on my desktop pc but i have one problem.

when insert a cd/dvd in a device, system freez

my conf is motherboard asus m2npv-vm, device samsung dvd+-rw on ide channel
for solved this problem i add **hdc=noprobe hdc=cdrom** in menu.lst of grub config file but in this case i not able to set dma because command **sudo hdparm -d 1 /dev/hdc** 	it gives back 
```
/dev/hdc:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)

```


excuse for my very bad english
thanks a lot

---

