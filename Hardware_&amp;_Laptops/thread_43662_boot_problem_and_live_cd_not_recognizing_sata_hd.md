---
title: "boot problem and live cd not recognizing sata hd"
date: 2005-06-22
forum: Hardware &amp; Laptops
---

### Post by colinhayes on 2005-06-22
A few days ago I ran the first stage of installing hoary on my powermac g5.  I had left 25GB free on my <a href="http://www.newegg.com/Product/Product.asp?Item=N82E16822144327">new maxtor sata hd</a>, and the install cd recognized the drive perfectly, and partitioned the remaining space and completed the first stage of the installer perfectly fine.

When it tried to then boot onto the linux drive, it went straight back into mac osx, so i restarted holding option; it showed the bootable drives, and I clicked the linux one.  it then brings up the yaboot boot loader saying:
First Stage Ubuntu Bootstrap
l for GNU/linux
x for mac osx
c for CDROM

stage 1 boot:

I type "l", it then flashes for a split second below the boot prompt "loading second stage bootstrap..."  before it goes back to the mac's graphical menu.  What a lovely little loop.

So I figure there's a problem with the boot loader's configuration file, so I start up on the live cd with the intention of mounting the drive and editing the file. 

However, the live cd does not recognize hdb.  It shows hda, but when i fdisk it and select p, it shows around 16877 things and has a segmentation fault.  lspci says "serverworks: unknown device" for the ide section.

So, any suggestions on how to get this to work?

---

