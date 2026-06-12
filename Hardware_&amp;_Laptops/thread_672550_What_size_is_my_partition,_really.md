---
title: "What size is my partition, really?"
date: 2008-01-19
forum: Hardware &amp; Laptops
---

### Post by joeashcraft on 2008-01-19
Summary:
Gparted shows /dev/sda3 to be 34.5 GB with 33.6 GB used.
Nautilus shows /dev/sda3 to be 15.4 GB with 15.1 GB used.
[[IMG]http://i124.photobucket.com/albums/p8/joeashcraft/gparted-thumb.png[/IMG]]("http://i124.photobucket.com/albums/p8/joeashcraft/gparted.png") [[IMG]http://i124.photobucket.com/albums/p8/joeashcraft/naut-thumb.png[/IMG]]("http://i124.photobucket.com/albums/p8/joeashcraft/naut.png")
(screenshots linked)

Details:
I'm running out of space on my ext3 partition (/dev/sda3) so I shrunk my NTFS part. down, moved it to the end, and wanted to enlarge the ext3 part using the newly freed space. Since I couldn't resize a mounted partition I booted to a GParted LiveCD. When gparted opened it showed my entire  HD as one big unpartitioned mass. I rebooted to a SAM LiveCD to use Gparted and tried to resize there. I got an error message about the part. being mounted even after I unmounted it. Accepting temporary defeat I rebooted into Ubuntu (install, not LiveCD). Today I noticed that GParted (not the LiveCD) shows that /dev/sda3 is 35GB and 97% full. But nautilus tells me it's only 15GB and I'm still running out of space.

Bottom Line:
How do I make /dev/sda3 truly bigger?


tia

---

