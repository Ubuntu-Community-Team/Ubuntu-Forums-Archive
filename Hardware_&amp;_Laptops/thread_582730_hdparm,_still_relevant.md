---
title: "hdparm, still relevant?"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by hardyn on 2007-10-20
had hdparm been depreciated?

i know they are using the sata drivers for all drives now, however my drive is detecting as using 16bit interface mode, is this just an artifact of an old hdparm program, or is there was a to up this to 32bit; i get an error when i try to change.

example:

/dev/sda:
 IO_support    =  0 (default 16-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 14593/255/63, sectors = 234441648, start = 0


arlen@z71vp:~$ sudo hdparm -c1 /dev/sda

/dev/sda:
 setting 32-bit IO_support flag to 1
 HDIO_SET_32BIT failed: Invalid argument
 IO_support    =  0 (default 16-bit)
arlen@z71vp:~$

---

