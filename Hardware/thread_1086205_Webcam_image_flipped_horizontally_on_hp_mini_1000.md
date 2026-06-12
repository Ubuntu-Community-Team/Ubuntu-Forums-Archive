---
title: "Webcam image flipped horizontally on hp mini 1000"
date: 2009-03-03
forum: Hardware
---

### Post by subtex on 2009-03-03
I just installed UNR on my hp mini 1000.

Everything seems to work right out of the box, but I noticed my webcam video is showing up backwards. (or rather, the software is not flipping it so that when I move my head to the left, I see a mirror of myself moving the same way).

Is there a simple way to flip the image?

---

### Post by subtex on 2009-03-05
So I've been doing a little research.

Based on what I could find from reading this thread: 
[http://ubuntuforums.org/showthread.php?p=5778099](http://ubuntuforums.org/showthread.php?p=5778099)

I know this camera uses the **uvcvideo** driver.

I did a modinfo on it and saw that it only has one parameter: **trace** and is missing the ones I would want to use like **hflip** that the **stk11xx** driver has.

Is there anyone who knows of a way to control uvcvideo cameras this way?

---

