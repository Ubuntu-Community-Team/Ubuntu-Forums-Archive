---
title: "Ubuntu 12.04  Logitech t650 moulti-touch"
date: 2013-01-22
forum: Hardware
---

### Post by zalletn on 2013-01-22
I have a Logitech multi touch T650 and what i have figure out that this this multi touch is been treated just like a mouse. some fetchers are working in the same way as my Logitech G7 mouse:
2 Finger = scrolling wheel
3 fingers (left-right) = back-forward (web, nautilus, etc.)
4 fingers up = opens unity menu  (have no idea what bottom it is)

i'd like to fin 4 fingers down, 2 fingers tap , one finger double tap.

is there any GUI app or any way that i can monitor what command it received from devise when i double tap and so.


Thank you.

---

### Post by Cyclops_ on 2013-01-26
+1 

I just purchased the same thing.  (Though I'm on 12.10.)  And I would LOVE the ability to use it to its full potential.

One thing that's interesting is that, out of the box, the device isn't even registering the tap events at all.  (I used xev to check.)

I think all of us who have this product should go to the Logitech community support and start begging for Ubuntu/Linux support!  :)

But I'd still take it if we can find our own solutions.

---

### Post by Cyclops_ on 2013-01-29
I started this thread on the Logitech support site.   Anyone else who has these issues - it would be great if you would register over there and chime in.  Squeeky wheels and grease and all that...!

[http://forums.logitech.com/t5/Mice-and-Pointing-Devices/T650-tapping-on-Linux/m-p/969401](http://forums.logitech.com/t5/Mice-and-Pointing-Devices/T650-tapping-on-Linux/m-p/969401)

---

### Post by eccentricity on 2013-05-17
> **Cyclops_ said:**
> I started this thread on the Logitech support site.   Anyone else who has these issues - it would be great if you would register over there and chime in.  Squeeky wheels and grease and all that...!

[http://forums.logitech.com/t5/Mice-and-Pointing-Devices/T650-tapping-on-Linux/m-p/969401](http://forums.logitech.com/t5/Mice-and-Pointing-Devices/T650-tapping-on-Linux/m-p/969401)

My post from Logitech boards:

Here are two links, the first is apparently the initial driver for t650 for linux released in january of 2012
 
[PATCH 1/1] HID: Add full MT support for Logitech Wireless Touchpad
[https://groups.google.com/forum/?fromgroups#!topic/kernelarchive/zKCN47bvMXY](https://groups.google.com/forum/?fromgroups#!topic/kernelarchive/zKCN47bvMXY)
 
Second is a post about the current issues with the developing driver as of february 2013
 
Touchpad: Add support for Logitech Wireless Touchpad and T650
[https://www.google.com/search?http://code.google.com/p/chromium/issues/detail?id=221455](https://www.google.com/search?http://code.google.com/p/chromium/issues/detail?id=221455)

---

### Post by Cyclops_ on 2013-05-17
> **eccentricity said:**
> My post from Logitech boards:

Here are two links, the first is apparently the initial driver for t650 for linux released in january of 2012

[PATCH 1/1] HID: Add full MT support for Logitech Wireless Touchpad
[https://groups.google.com/forum/?fromgroups#!topic/kernelarchive/zKCN47bvMXY](https://groups.google.com/forum/?fromgroups#!topic/kernelarchive/zKCN47bvMXY)

Second is a post about the current issues with the developing driver as of february 2013

Touchpad: Add support for Logitech Wireless Touchpad and T650
[https://www.google.com/search?http://code.google.com/p/chromium/issues/detail?id=221455](https://www.google.com/search?http://code.google.com/p/chromium/issues/detail?id=221455)

I wish I knew more about low level stuffs.  Do these links mean that there is a way to make it work in Linux?

---

### Post by eccentricity on 2013-05-18
> **Cyclops_ said:**
> I wish I knew more about low level stuffs.  Do these links mean that there is a way to make it work in Linux?

It shows the older source code, if you know anything about device driver programming, worst case is there is some kind of hack to make it work. I'm no expert.

---

