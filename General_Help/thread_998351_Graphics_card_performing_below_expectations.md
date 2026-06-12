---
title: "Graphics card performing below expectations"
date: 2008-11-30
forum: General Help
---

### Post by Ixonal on 2008-11-30
So I have a geforce 9800 gt, and decided to run a benchmark to see how it held up (used Unigine Tropics 1.1). Well, here are the results...

```
Unigine
Tropics Demo v1.1
FPS:	
9.3
Scores:	
235
Hardware
Binary:	
Linux 32bit GCC 4.1.2 Release Oct 29 2008
Operating system:	
Linux 2.6.27-9-generic i686
CPU model:	
Pentium(R) Dual-Core CPU E5200 @ 2.50GHz
CPU flags:	
2500MHz MMX SSE SSE2 SSE3 HT
GPU model:	
GeForce 9800 GT PCI Express 180.06 512Mb
Settings
Render:	
opengl
Mode:	
1280x1024 windowed
Shaders:	
high
Textures:	
high
Filter:	
trilinear
Anisotropy:	
4x
Occlusion:	
enabled
Reflection:	
enabled
Refraction:	
enabled
Volumetric:	
enabled
```

I checked some other peoples' scores, and they're much higher with comparable systems and the same video card... so I'm confused. Why am I not getting higher framerates?

---

### Post by sdennie on 2008-11-30
Having compiz enabled while running 3D "benchmarks" can sometimes produce poor results.  Also, you should keep in mind that it's not uncommon for uploaded "benchmarks" to be more or less junk.  Yes, you may be able to configure a system to get those numbers for a particular benchmark but, actually using it in that state may not be plausible.

---

### Post by fragos on 2008-11-30
The real test is the visual experience. One would think the visual experience with your card would be good for almost any application. 3D games are perhaps the truest indicators of video performance. There are many factors that impact performance like how many bits of color. 32 might give you the best image but 24 or even 16 may perform better.

---

### Post by Ixonal on 2008-11-30
well with what I have, I should be getting better frame rates in general. I mean, 25 fps in WoW?

---

### Post by sdennie on 2008-11-30
> **Ixonal said:**
> well with what I have, I should be getting better frame rates in general. I mean, 25 fps in WoW?

WoW performance is almost always abysmal under linux when compared to it's performance on the same hardware under Windows.  It's playable (if you consider 30ish fps playable) but, unless Blizzard releases a native linux client, it is in no way a benchmark for linux 3D performance.  Again, make sure compiz is turned off if you are playing 3D games.  It can make a big difference.

---

### Post by fragos on 2008-12-01
I'm not a gamer so my old FX5200 does the job for me with compiz. The closest thing I've done in the way of a performance reference is glxgears. Many have said it's not scientific but it can provide insite into relative performance. My FX5200 with the default window size gets over 1,100 fps by it's measure. I've no idea how that relates to the fps results from other tests. I perdieve adequait performance so I won't complain won't look to a more powerful GPU until it's time to upgrade my mobo.

---

### Post by Ixonal on 2008-12-01
well, compiz is turned off, I know that. Also had a strange issue when I tried to overclock my card just a lil bit (50 mhz on both processor and memory). The screen just blinked black and white until I rebooted.

---

### Post by sdennie on 2008-12-01
Are you able to alt-tab out of WoW?  Check to make sure nothing bad is happening while playing by using "top" in a terminal.

---

### Post by Ixonal on 2008-12-01
yeah, I can alt tab out just fine. WoW stops rendering new images while it doesn't have focus, but the sound keeps going. everything starts right back up fine when it regains focus.

---

