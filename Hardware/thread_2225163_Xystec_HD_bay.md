---
title: "Xystec HD bay"
date: 2014-05-20
forum: Hardware
---

### Post by norbert23 on 2014-05-20
Hello!

I'm currently having a few troubles getting my hd-case/bay [1] to work on a [2] motherboard. (Sorry - it's german)  [ubuntu 14.04 - recent kernel]
I'm using the e-sata port on my hd-bay and plugin in on the SATA port on the pc motherboard (with a e-sata to sata cable).
But all I see in /dev/sd* is always only the first disk in the bay. If I unplug the first disk (put it out of its tray) - after a reboot I see the 2nd disc - and so on (from top to botttom).
I toyed around with scsitools (rescan-scsi-bus) - but equal results. I even checked the BIOS but I did not find something 'crucial' to change - and all I see in the BIOS is the first disk too.
This bay does not have a raid-toggle or so. Even opened the case and checked the interior as good as I could - but unable to see one.

Everything works as expected via the USB 3 port. Unfortunately this PC only has USB 2.0... Which is very slow.
But I bought the parts over time and so... I'd like to get these things working.
All I found after researching is that a sata multiplier is needed - I assume this hd-case provides one (from looking on the internal connections) - but it is definitely not detected as one from BIOS or the kernel.

I'm not sure if I am missing something or this cannot work at all.
Maybe someone has a hint for me or some experience...

Thank you very much in advance,
stefan

[1]: [http://www.pearl.de/product.jsp?pdid=PX2590&catid=1162&vid=953&curr=ATS](http://www.pearl.de/product.jsp?pdid=PX2590&catid=1162&vid=953&curr=ATS)
[2]: [http://www.kiebel.de/index.php?cl=details&anid=5095&lang=0&shp=oxbaseshop](http://www.kiebel.de/index.php?cl=details&anid=5095&lang=0&shp=oxbaseshop)

---

### Post by norbert23 on 2014-05-23
gently *bump*

---

