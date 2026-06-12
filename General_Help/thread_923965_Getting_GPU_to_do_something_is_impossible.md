---
title: "Getting GPU to do something is impossible?"
date: 2008-09-19
forum: General Help
---

### Post by Lord Udedenkz on 2008-09-19
Is it not possible to unload graphical processing from the CPU to the GPU? 
After multiple hours of not getting it, I think I got it although it is not a fun realization.

GUI/Flash/Glxgears and things like that rely madly on the CPU. Glxgears uses 100% of one core for example.

Also because of this reliance on the CPU, how come glxgears only uses one core? Wouldn't it be more efficient to use both cores?

Or am I doing something wrong?

Core 2 Duo T8300 @ 2400Mhz w. 3072kb L2
1024x2 666Mhz Equivelent DDR2
800Mhz FSB
8600M GT 475Mhz Core / 400MHz DDR2 RAM / 950Mhz Shader Clock
173 Drivers (EnvyNG installed)
39415 frames in 5.0 seconds = 7882.860 FPS (3-4k with GUI fancy)

:(

---

### Post by mcduck on 2008-09-19
CPU stil has to send data to GPU for processing.

Besides, you really shouldn't pay much attention to glxgears. It's only useful as a simple way to check if 3D works or doesn't work, nothing else. It definitely isn't a benchmark or anyhting. (Actually, you used to need to start it with "glxgears --iacknowledgethatthistoolisnotabenchmark" to get any fps output at all :D)

---

### Post by TenPlus1 on 2008-09-19
If you are using an nvidia card, the best thing is to pop into terminal and sudo nvidia-settings, turn on vsync for 3D and this will still give you smooth 3d but use far less cpu time in doing so...

---

### Post by Lord Udedenkz on 2008-09-19
Ok, that kinda made it better with the Vsync
Now I get a constant 59.xxx FPS - so now it doesn't go above the 60Hz Monitor. That is bound to use less CPU then 7888.xxx FPS
So now it seems to just have masked it... doesn't make a difference with flash player and wrapper.

What I want, is that the GPU would actually do the rendering. The fact that it never gets above 76C is proof of that. It need to go to 86-90C when it is actually used.

Yes CPU and GPU interconnect, but the GPU needs to like do the graphical stuff so that the CPU could do the rest otherwise it is extremly inefficient - that my problem and... I don't know what to do about it.

Or is it that the GUI/Glxgears/flash does not support the GPU? How can I check that the GPU does something? Maybe be an Open Source Driver or a newer NVIDIA driver?

Thanks.

---

### Post by Lord Udedenkz on 2008-09-19
Also,

Is there a way to reaload the networking component of Ubuntu? It does not work for me once in every 2 to three boots. No network devices. Is there a terminal command for that? I would make that a shortcut on dekstop..

I never thought that it would be so hard to actually get it to work right. );

---

