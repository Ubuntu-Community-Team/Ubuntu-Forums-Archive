---
title: "Flipped webcam. Asus k52f , Ubuntu 10.04 64bit. No solution found"
date: 2013-05-09
forum: Hardware
---

### Post by Gerrozzz on 2013-05-09
Hello to everyone!
Hope someone could help me with my webcam problem, especially because i use Skype at work.
I have Ubuntu 10.04 (64 bit) on my Asus k52f, and my cam is flipped using Skype.

I tried every kind of solution involving the command line "LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype" .....i tried to change the path of the library (lib or lib32 or lib64), i tried to insert "v4l2convert.so" instead of "v4l1compat.so" and i tried every combination of both...but nothing works!

the message is still the same: "_/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored._" if the path is "_usr/lib32/libv4l/v4l1compat.so_",
or "_libv4l2: error dequeuing buf: Invalid argument"_ if the the path is "_usr/lib/libv4l/v4l1compat.so_"


I just wanna know WHY this solutions don't work on my laptop..

please help me :) there must be a solution for this annoying problem!!

---

