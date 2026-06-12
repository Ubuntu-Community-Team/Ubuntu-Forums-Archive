---
title: "cd/dvd-drive too slow (despite dma turned on)"
date: 2005-12-01
forum: General Help
---

### Post by ember on 2005-12-01
Hi,

today I was about to rip a cd and so tuned my hdparm-settings a bit. Now everything is turned on and it works with the harddisk (/dev/hda) quite flawlessly.

Yet even if I enable everything (32-bit transfer, dma, unmask irq) on my cddrive, it still gives me poor results:

```

root@sleipnir:/home/ember# hdparm /dev/hdc

/dev/hdc:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
root@sleipnir:/home/ember# hdparm -tT /dev/hdc

/dev/hdc:
 Timing cached reads:   1592 MB in  2.00 seconds = 794.93 MB/sec
 Timing buffered disk reads:    8 MB in  3.06 seconds =   2.62 MB/sec


```

Any ideas on that?

Best,
ember

---

