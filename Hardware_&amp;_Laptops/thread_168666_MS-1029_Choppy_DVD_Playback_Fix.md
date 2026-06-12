---
title: "MS-1029 Choppy DVD Playback Fix"
date: 2006-04-30
forum: Hardware &amp; Laptops
---

### Post by WhiteHorse on 2006-04-30
To fix choppy dma playback on the MS-1029 aka MSI Megabook 635 you need to enable DMA on the drive. To do this, perform the following:

1. Edit /etc/hdparm.conf and add the following to the end of the file:

/dev/hdc {
	dma = on
}

That will turn on DMA every time you boot up. To avoid having to reboot, run this command:

 sudo hdparm -d 1 /dev/hdc

Now you just have to get DeCSS to view encrypted discs which is handled in another thread.

---

