---
title: "Hard disk devices keep changing"
date: 2009-03-18
forum: Hardware
---

### Post by dreadnyah on 2009-03-18
My hard disk devices keep changing every time I boot, i.e. sometimes a particular drive will show as sda, then on the next boot it might be sdc, etc. I'm using Ubuntu 8.10, Intrepid Ibex, kernel is 2.6.27-11-generic. I have 3 hard drives:

PATA - Western Digital WDC800BB
SATA 0 - Seagate ST3160215AS
SATA 1 - Western Digital WDC800BD

dmesg output:
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)


My (BIOS) boot messages show the following:
IDE Channel 0 MASTER - Western Digital WDC800BB <-i.e. the PATA drive
IDE Channel 0 SLAVE - My DVD drive
IDE Channel 1 MASTER - Seagate ST3160215AS <-i.e. SATA drive
IDE Channel 1 MASTER - Western Digital WDC800BD <-i.e. SATA drive

Could the devices be changing because they are all setup as master? If so, how do I change that? If not, any thoughts as to what might cause this?

Regards

dreadnyah

---

### Post by taurus on 2009-03-18
Instead of using /dev/sdaX, /dev/sdbX, & /dev/sdcX for your harddrives in /etc/fstab, you should use UUID's instead.

```
sudo fdisk -l
sudo blkid
df -h
```

---

