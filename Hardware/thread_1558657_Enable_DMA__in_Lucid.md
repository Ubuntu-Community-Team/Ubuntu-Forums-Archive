---
title: "Enable DMA  in Lucid"
date: 2010-08-22
forum: Hardware
---

### Post by roy913 on 2010-08-22
It took me hours to figure out what had happened to my dvd drive.

My problems were choppy dvd playback and super slow dvd burning speed (less than 2x).

Then I figure out it was something about the DMA.

But most of the solutions out there are for older version of Ubuntu like 8.04 etc so I guess this is the reason why they do not work on my machine with 10.04.

Finally found this thread:
[https://bugs.launchpad.net/ubuntu/+bug/292142]("https://bugs.launchpad.net/ubuntu/+bug/292142")

In this thread Dimitris Kalamaras wrote:
> Here is the dmesg message I was getting:
 [ 7.684439] ata8.01: ATAPI: HL-DT-ST DVDRAM GSA-4167B, DL10, max UDMA/33
[ 7.684457] ata8.01: WARNING: ATAPI DMA disabled for reliablity issues. It can be enabled
[ 7.684459] ata8.01: WARNING: via pata_ali.atapi_dma modparam or corresponding sysfs node.

I followed these workarounds:
Added
1) "options pata_ali atapi_dma=1" in /etc/modprobe.d/options (new file for me!)
2) "echo 1 > /sys/module/pata_ali/parameters/atapi_dma" in /etc/rc.local

and finally I added
 "pata_ali atapi_dma=1" to "/etc/initramfs-tools/modules"

All these to be sure! :)

After the reboot (the dmesg messages still appear!) the problem was finally solved.
Now I can watch and write DVDs at full speed.

I have come across exact situation and this thread by Dimitris Kalamaras saves my life.

There should be some reasons for DMA to be disable by default. However, it should provide a solution or better document to show how to enable it. It's really a pain to see my dvd buring at below 2x which it should be at 8x.

Millions thanks to Dimitris Kalamaras!

(not to mention my harddrive shows a drastic increase in reading speed after DMA is enabled.)

---

### Post by Spydr4590 on 2010-09-03
Roy you rock! Thanks for this. Also people should use dmesg | grep ata to tell if it's on or off. ;)

---

