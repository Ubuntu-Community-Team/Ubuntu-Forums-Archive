---
title: "Conceptronic cchatcam problem"
date: 2009-05-06
forum: Hardware
---

### Post by henriquemaia on 2009-05-06
I have a Conceptronic cchatcam and I'm trying to get it work without success. The camera seems to be correctly detected, but when I try it with some program (wxcam, for example), I always get an error about the frame format.

lsusb shows this:

ID 0ac8:0302 Z-Star Microelectronics Corp. ZC0302 WebCam

dmesg this:

[19240.239932] gspca: frame overflow 118889 > 118784


Any ideas on how to solve this?

---

### Post by henriquemaia on 2009-05-06
Bumping this thread up.

---

### Post by henriquemaia on 2009-09-10
Still not working on Karmic. Unfortunately.

Any ideas on how to solve this?

---

### Post by no2498 on 2009-09-14
in wxcam click settings frame size set it to 320x240

---

