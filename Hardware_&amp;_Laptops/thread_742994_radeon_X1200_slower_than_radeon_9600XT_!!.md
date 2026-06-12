---
title: "radeon X1200 slower than radeon 9600XT ?!??!"
date: 2008-04-02
forum: Hardware &amp; Laptops
---

### Post by freedom on 2008-04-02
I have now two computers at office... 
Old one...
1. AMD Barton 2500+ (1,83GHz), 512Mb DDR400, ATI RADEON 9600XT
and new one
2. AMD Athlon64 X2 4000+ (2GHz) two cores, 1Gb DDR2-667, integrated ATI X1200 with shared 128Mb memory

latest ATI fglrx drivers are installed on both machines, same xorg.conf
and fglrxinfo returns

display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series (and ATI Radeon X1200 Series)
OpenGL version string: 2.1.7412 Release

on both systems, Direct rendering is YES and OpenGL render string: ATI...
and speed results are weird... (I would said insane but...)

glxgears test for 9600XT gives 3450FPS and at X1200 1250FPS
fgl_glxgears on 9600XT gives 770FPS while on X1200 is just 250FPS

Am I missing something or it is normal to have 3-4 years old card 3x faster than this X1200 S*IT :confused:

---

### Post by bryonak on 2008-04-02
Yup!

The X1200 is a low-end office card with stripped down bandwith (the express version is built into notebooks because of its low power consumption... and performance).
The 9600XT was a high-end gaming card.
This still shows even if they're 4 years apart.

---

