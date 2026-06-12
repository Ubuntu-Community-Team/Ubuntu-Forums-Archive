---
title: "Use samsung GT3010s mobile's camera as webcam"
date: 2012-09-14
forum: Hardware
---

### Post by prat22 on 2012-09-14
Hi, 

 I want to use my spare samsung GT3010s (java based) mobile's cam as a webcam to avoid additional cost of equipment. 
I have tried *smartcam*, but it uses only bluetooth/wifi connection, but my phone doesnt have a wifi. My laptop is HP500 (an old model), which doesnt have a bluetooth either. I need to use my phone's cam as webcam only through usb data cable. 

Ideas?

---

### Post by gordintoronto on 2012-09-14
I doubt very much that this will work.

When you connect your phone by USB, what does lsusb produce? Ubuntu probably sees a flash drive, nothing else.

My webcam cost $10 (Canadian) when I bought it in China. Works fine.

---

### Post by prat22 on 2012-09-15
Thanks gordintoronto.

However, lsusb produces:


@Poison:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04e8:663f Samsung Electronics Co., Ltd SGH-E720/SGH-E840

so, my ubuntu recognizes my phone. 
There must be something I can get from my scraps!

---

