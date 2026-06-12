---
title: "HP dv9700 webcam issues"
date: 2010-10-19
forum: Hardware
---

### Post by Billygoat on 2010-10-19
I own an hp dv9815nr (9700 series) laptop that has an integrated webcam. I upgraded to 10.10 from 9.04 the other day and noticed that the webcam no longer works out of the box. Was wondering if anyone knows what drivers I need and where to get them or at least how I can view the hardware on my system to figure out what type of webcam is on my laptop. tried lsusb but didnt work since its an integrated cam and not usb.

---

### Post by chessnerd on 2010-10-19
As far as getting the type of the card, my first thought is trying lspci instead. You could also try lshw (it recommends you run that as super-user).

According to the [HP page]("http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&docname=c01394734&dlc=en") on the laptop, the webcam is a "HP Pavilion WebCam with Integrated Microphone"

---

### Post by Billygoat on 2010-10-19
> **chessnerd said:**
> As far as getting the type of the card, my first thought is trying lspci instead. You could also try lshw (it recommends you run that as super-user).

According to the [HP page]("http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&docname=c01394734&dlc=en") on the laptop, the webcam is a "HP Pavilion WebCam with Integrated Microphone"

Yeah, I looked up their page earlier, was no help on exactly what the device is called. 

I used both commands and couldn't find the webcam.

---

