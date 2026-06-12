---
title: "Asus DRW-1814BL slow to burn DVDs"
date: 2008-07-11
forum: Hardware
---

### Post by TheHardDisk on 2008-07-11
Well my issue is that my burner burns 16xDVDs at 3-4 speeds.  Strangely when I use a Gutsy livecd it works fine, I had this issue before when I had a Gusty installation done and after some upgrades that is where the issue started.  I have the same issue with Hardy as well.  CD's burn fast and no problems, only dvd's and I'd like to point out I've used three different medias and used both + and -.

Note I DO have DMA enabled, I used the ubuntu wiki to check and know if it's enabled or not. as my dmesg shows:

[I][   34.428535] ata2.00: ATAPI: ASUS    DRW-1814BL, 1.14, max UDMA/66
[   34.600369] ata2.00: configured for UDMA/66[/I]

note when I'm burning my dmesg says this:

[I][84558.633323] attempt to access beyond end of device
[84558.633333] sr0: rw=0, want=8602364, limit=4456384[/I]

and when I do  *sudo hdparm -d1 -k1 /dev/scd0*  I get this:

[I]/dev/scd0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 setting keep_settings to 1 (on)
 HDIO_SET_KEEPSETTINGS failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device[/I]

---

