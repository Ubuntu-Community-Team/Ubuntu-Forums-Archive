---
title: "OpenGL comes and goes (ATI)"
date: 2007-02-05
forum: Hardware &amp; Laptops
---

### Post by rodrigo666 on 2007-02-05
Greetings,

I've been using the open sources drivers for ATI video cards on my Ubuntu Edgy Eft box.

All seems to be ok. I managed to get Beryl working perfectly with AIGLX.

But, as usual with this damn video card of mine, there's always some problem to came.

The thing is that occasionally, specially when I reboot the machine, my OpenGL (direct rendering) goes off with no apparent reason!

But the most strange thing is that the way I manage to get it working again is a most unusual way: I reboot the machine, load Windows, play a little NBA Live (my favorite game and main reason I still have Windows on my PC), and after a match, reboot again, load Ubuntu and then, voilá, there's OpenGL again!

I wonder, why is that? It's very annoying, there's some way to fix this bug?

Thanks in advance.

---

### Post by Aifel on 2007-02-05
Wow, that's kinda weird. I am also using an ATI (Radeon 9200 PRO) card, and it hasn't given me many issues, or at least none like that. I recommend trying a different driver, or MAYBE changing your AGP aperature size in your BIOS might help (Im just guessing at that though...).

Good luck with your problem.

---

### Post by rodrigo666 on 2007-02-05
Thanks for the quick reply. I don't think that change my driver will be a good solution, since I'm using the open source driver, which in my humble opinion is better than the fglrx or the provided by the ATI.

I will check the AGP aperture on my BIOS thought, it might be that.

---

### Post by Aifel on 2007-02-05
Well, it kinda depends on the things being run. I know for a fact that fglrx provides better glxgears FPS, however, the performance is kinda jumpy. Here's some things to check for:

It may be the incompatibilty between the Linux-based ATI driver, or that Windows doesn't enable OpenGL by default (I think).

Check that 

```
Load "glx"
```

Is in your xorg.conf

Also, for any computer to run Windows games effectively and properly (especially WoW), you need a large AGP Aperature size. It should be double your video card MB (eg my Radeon=128. My AGP=256).

If the problem persists, you can completely reconfigure xorg by running
```
dpkg-reconfigure xserver-xorg
```
Or use the generic "vesa" driver xorg provides, which will give you basic support until you fix the problem.

Good luck, and hope this helps.

---

### Post by rodrigo666 on 2007-02-06
Thanks Aifel, but I don't think that will help.

My xorg.conf has "Load "glx"" for sure, because if not, then beryl wont even start.

Why is that I must have and AGP aperture double the memory of my video card? Based on what you make this claim? I've never heard that before and don't see a reason for that, I will try thought.

Right now I'm going to reboot my PC and set my BIOS setup for AGP = 512.

Well, FGLRX can get some better results on glxgears, but you must realize that is NOT a benchmark. Besides, it does not work with AIGLX.

And I don't think VESA generic driver has OpenGL support for my ATI Radeon 9600 SE.

Thanks for the reply, I really appreciate that.

---

