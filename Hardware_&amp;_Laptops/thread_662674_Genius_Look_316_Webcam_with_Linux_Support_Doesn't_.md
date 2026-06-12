---
title: "Genius Look 316 Webcam with Linux Support Doesn't work with Gutsy"
date: 2008-01-09
forum: Hardware &amp; Laptops
---

### Post by wersdaluv on 2008-01-09
I just bought the Genius Look 316 webcam (since samhain referred it to me :P ). I can't make it work. According to the box, it has linux support. I found a linux driver in the box but it's for kernel 2.5.6.

Anyway, the driver can be found here if you want to see it--> [http://www.genius-europe.com/en/prod...&ID=31&ID3=336](http://www.genius-europe.com/en/prod...&ID=31&ID3=336)

here is more info

Code:

lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0ac8:305b Z-Star Microelectronics Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

Code:

[  164.120000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (7)
[  166.480000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (9)
[  166.480000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (14)
[  166.480000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (13)
[  166.480000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (16)
[  166.480000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (11)
[  166.480000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (6)

Code:

lsmod | grep videodev
videodev               29312  2 gspca
v4l2_common            18432  1 videodev
v4l1_compat            15364  1 videodev

---

