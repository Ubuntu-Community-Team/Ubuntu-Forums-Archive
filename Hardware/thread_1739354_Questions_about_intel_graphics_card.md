---
title: "Questions about intel graphics card"
date: 2011-04-25
forum: Hardware
---

### Post by shelbyvision on 2011-04-25
I have an HP Compaq nc6220 laptop, with Ubuntu 10.04. I've been recently playing with Wings 3d, the 3d graphics program. I made a model that was complicated enough to slow down the program drastically. I checked my system monitor and discovered that when rendering the scene on Wings, the CPU usage was 100%, while memory usage was only 28%. I wrote about it on the Wings Forum, see [http://nendowingsmirai.yuku.com/topic/7524/Too-many-polygons-Not-enough-memory-Or-what?page=1]("http://nendowingsmirai.yuku.com/topic/7524/Too-many-polygons-Not-enough-memory-Or-what?page=1")and was asked some questions about my hardware I couldn't really answer. My graphics card is an Intel Mobile 915GM/GMS/910GML Express Graphics Controller. There doesn't seem to be any proprietary drivers for linux available, so I guess I'm stuck with whatever Ubuntu provides. Someone asked if I had hardware acceleration enabled. I don't know how to find out that information. 
Can anyone offer any help or sources of knowledge about this topic? Any help will be appreciated.
Steve

---

### Post by oracle2b on 2011-04-25
To check if you \have effects enabled go to

System -> preferences -> Appearence -> visual effects

None = disabled

or right click on your desktop select 'Change Desktop background' -> visual effects

---

### Post by shelbyvision on 2011-04-26
I didn't state the problem very well. Someone on the other forum said that maybe my graphics card was not able to process OGL and so was having my CPU emulate OGL. Does that make any sense? Is there any way I can upgrade my graphics card to correct the problem?

---

### Post by pauljwells on 2011-04-26
I'm not familiar with the program, but the laptop is quite a low spec for graphics-heavy work I would say - Pentium M around 2GHz or less? I think you're just expecting too much of the poor thing!

The intel graphics is shared memory, integrated with the CPU and again fairly low spec compared to plug-in cards.

The one thing going for you is that Intel fully supports linux so there is no need for a proprietary driver - the linux one is the best one so you can be sure you're getting the best out of it running linux

---

### Post by shelbyvision on 2011-04-26
That's correct, 2.13 GHz.I bought it because of the price. The way some folks on the Wings 3d forum were talking, it sounded like there might be something I could do about it, but, as I suspected, probably not.

---

### Post by Yellow Pasque on 2011-04-26
To answer the question, you look at the output of glxinfo. If it says Mesa software rasterizer, then you have an issue. More likely, your GPU is so weak (and Intel's Linux drivers are slow) that it doesn't take much load off the CPU.

---

