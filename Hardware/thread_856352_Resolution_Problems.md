---
title: "Resolution Problems"
date: 2008-07-11
forum: Hardware
---

### Post by drkemprd on 2008-07-11
I'm new and I know this has already been covered serveral times. My resolution is 800x600 and wont go any higher, I tried the sudo dpkg-reconfigure xserver-xorg and it only had stuff about the keyboard.. It's on an old HP N5000 1.1ghz AMD laptop.. Anyone help me, I'm almost completely new to linux...

---

### Post by PfromD on 2008-07-11
I don't mean to hijack, but I'm having the same problem; 800x600 and won't go higher. When I installed Ubuntu it had no problems doing 1280x1024, but all of a sudden it would only do 800x600 and below. I'm perfectly clueless as to how I go about detecting the root of this problem, and 800x600 IS a problem ;)
(GeForce2 FX5200)

---

### Post by drkemprd on 2008-07-11
btw it's version Xubuntu 8.04.1.. Any help would be great..

---

### Post by Vorian Grey on 2008-07-11
Any idea what kind of video card you have, like ATI, Nividia, or Intel?

---

### Post by drkemprd on 2008-07-11
Trident Video Accelerator.

---

### Post by drkemprd on 2008-07-11
Holy crap.. I fixed it sudo displayconfig-gtk worked, let me select the res and LCD...

---

### Post by Vorian Grey on 2008-07-11
All right, way to go.

---

