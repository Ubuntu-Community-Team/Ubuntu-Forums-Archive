---
title: "How to open 3D accelaration?"
date: 2006-12-04
forum: Hardware &amp; Laptops
---

### Post by leesshmily on 2006-12-04
When I try to use Cedega, it told me that can't open 3D accelaration. My graphic card is ATI Xpress200M. And I think it can support 3D accelaration. Also I have installed the newest driver and I am sure it can work well. Do I need to open 3D accelaration manually? And how can I do that? Thank you.

---

### Post by evilghost on 2006-12-04
Are you using the open-source ATI driver or the closed-source fglrx driver from ATI?

---

### Post by leesshmily on 2006-12-04
My driver was downloaded from ATI official website.
And the information of fglrx is 

senl@senl-CHALMERS:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6011 (8.28.8)

---

### Post by evilghost on 2006-12-04
What does "glxinfo|grep -i direct" say?

---

### Post by leesshmily on 2006-12-04
It says 

direct rendering: Yes

---

### Post by evilghost on 2006-12-04
What happens when you run:

fgl_glxgears

---

### Post by leesshmily on 2006-12-04
It shows a rotating cube with some gears. And in terminal there are also some information seems like some kinds of benchmark

643 frames in 5.0 seconds = 128.600 FPS
717 frames in 5.0 seconds = 143.400 FPS
1862 frames in 5.0 seconds = 372.400 FPS
2593 frames in 5.0 seconds = 518.600 FPS
2638 frames in 5.0 seconds = 527.600 FPS

---

### Post by evilghost on 2006-12-04
Your drivers are working perfectly and supporting 3D acceleration without issue.  You may want to take it up with Cedega/Transgaming support.  Last time I played with Cedega it was 4.x and I didn't use it very long.

At least you know you don't have issues with your fglrx/ATI driver and that your 3D acceleration is working without issue.

---

### Post by leesshmily on 2006-12-04
Thanks a lot:)

---

