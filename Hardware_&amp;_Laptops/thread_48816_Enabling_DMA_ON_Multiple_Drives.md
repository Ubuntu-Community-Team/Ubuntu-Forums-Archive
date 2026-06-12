---
title: "Enabling DMA ON Multiple Drives"
date: 2005-07-13
forum: Hardware &amp; Laptops
---

### Post by codejunkie on 2005-07-13
i've been having trouble with enabling DMA on multiple drives. i have a dvd-rom and a dvd+rw drive that are on the same ide chanel. I can only enable DMA on one of the devices at a time by adding either 
```

/dev/hdc {
       dma = on
}
for the dvd-rom drive

```
or
```

/dev/hdd {
       dma = on
}
for the dvd+rw drive

```
to the /etc/hdparm.conf file but if i try and enable DMA on both drives at the same time my system freezes at the gnome splash screen any help here would be gladly appreciated.

---

