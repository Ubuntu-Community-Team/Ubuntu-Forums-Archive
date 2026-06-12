---
title: "Webcam Easycam USB 330K not working"
date: 2012-10-13
forum: Hardware
---

### Post by XUwe on 2012-10-13
HI,

using Xubuntu 12.04.01 since a few weeks I hit now the point to activate my webcam within skype. Unfortunately the webcam is neither working within Skype or within Cheese. I only see a black frame with no content. Skype detects the webcam as "USB camera (093a:2600)(/dev/video1)". (side note - webcam is working within Windows XP - so the webcam isn't broken).

The Webcam has the following details (generated with lsusb):
ID 093a:2600 Pixart Imaging, Inc. Typhoon Easycam USB 330K (newer)/Typhoon Easycam USB 2.0 VGA 1.3M/Sansun SN-508

On the website [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) I figured out, that in general the webcam support is given, based on the driver gspcav1 (using sensor/bridge Pac7311) . But I fear this information might be related to an previsous Xubuntu/ubuntu kernel.

Any hints for further investigation are welcome.
Thanks in advance for your help!

Br
Uwe

---

