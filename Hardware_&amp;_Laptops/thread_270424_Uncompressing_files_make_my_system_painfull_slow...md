---
title: "Uncompressing files make my system painfull slow..."
date: 2006-10-03
forum: Hardware &amp; Laptops
---

### Post by Psyk[o] on 2006-10-03
Hi,
after the installation my system is very slow... 
For example, when I uncompress a file (tar.gz, tar.bz, rar) the uncompressing process is very slow and the system become very slow!

I have the DMA of my HD set to ON and this is the result of the hdparm test:

HDPARM TEST


/dev/hda:
 multcount    = 16 (on)
 IO_support   =  1 (32-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 160086528, start = 0

/dev/hda:
 Timing cached reads:   788 MB in  2.00 seconds = 393.17 MB/sec
 Timing buffered disk reads:  134 MB in  3.03 seconds =  44.24 MB/sec


My configuration is:

Ubuntu Edgy
Celeron 1700
768MB ram
Nvidia 5900XT 128mb

What can I do? In the past my system wasn't so slow...

---

