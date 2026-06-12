---
title: "dvd no media mounted solved"
date: 2005-10-13
forum: Hardware &amp; Laptops
---

### Post by savage on 2005-10-13
I've had linux for awhile but just haven't needed to burn anything but video cds and normal cd's. Then the need arose to archive some stuff to dvd. My DVD Burner is:

hdd: TOSHIBA CD/DVDW SD-R5372, ATAPI CD/DVD-ROM drive

When using k3b I would receive the error:

> /dev/hdd: media is not recognized as recordable DVD: 0

Taking a look at the media

> oliver@puffer:~$ dvd+rw-mediainfo /dev/hdd
INQUIRY:                [TOSHIBA ][CD/DVDW SD-R5372][TU31]
GET [CURRENT] CONFIGURATION:
:-( no media mounted, exiting...

The short answer is that the dvd media I was using is unusable by my burner. Using a different type of dvd media solved the problem. I was using DVD-R media, CompUSA brand.

When I inserted TDK DVD-R media it worked.

---

