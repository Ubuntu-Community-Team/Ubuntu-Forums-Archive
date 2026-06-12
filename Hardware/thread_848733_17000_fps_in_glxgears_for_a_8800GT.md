---
title: "17000 fps in glxgears for a 8800GT"
date: 2008-07-03
forum: Hardware
---

### Post by ProbablyX on 2008-07-03
Hello!

I have a GeForce 8800GT, 512MB PCI-E gfx card. When I run glxgears (in fluxbox here to minimize system load) I get this:
```

glxgears
64260 frames in 5.0 seconds = 12851.902 FPS
90470 frames in 5.0 seconds = 18093.949 FPS
90597 frames in 5.0 seconds = 18119.355 FPS
85166 frames in 5.0 seconds = 17033.115 FPS
89948 frames in 5.0 seconds = 17987.223 FPS
85570 frames in 5.0 seconds = 17113.865 FPS

```

Isnt this very low? I know glxgears isn't a benchmark but I've seen people with at 10000fps more than that!

Could this be a driver problem? It seems kinda weird..

Thanks

---

### Post by ProbablyX on 2008-07-03
OK!

I uninstalled the nvidia drivers, purged envy drivers.
removed xorg.conf and installed nvidia-glx-new and ran nvidia-settings.

Im now up in 21000fps - though its still "too low" any ideas?

Thanks :)

---

### Post by zgornel on 2008-07-04
Try testing your performance on something more appropriate warsow or open arena. Glxgears's is very simple and does not reflect in a decent manner the actual power of the graphic card. As a reference, my ATI Mobility X1350 scores ~2500 :D .

---

### Post by ProbablyX on 2008-07-04
My card broke today, called the store and just got an RMA approval. Very fast processing so far so I hope Ill get a new card by next week's end... Might be that causing the low FPS...

So it's just to put it back in the box, print out the postal service return label I got in the e-mail and head off to the post office tomorrow :P

Thanks anyway

---

### Post by Marshal0505 on 2008-07-04
> **ProbablyX said:**
> My card broke today, called the store and just got an RMA approval. Very fast processing so far so I hope Ill get a new card by next week's end... Might be that causing the low FPS...

So it's just to put it back in the box, print out the postal service return label I got in the e-mail and head off to the post office tomorrow :P

Thanks anyway

glxgears is not a benchmark to measure performance 'cause not all the render techniques used in games are used in glxgears. So I'd take Zgornel's advice.

some more info:
[http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark](http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark)

---

### Post by ProbablyX on 2008-07-05
> **Marshal0505 said:**
> glxgears is not a benchmark to measure performance 'cause not all the render techniques used in games are used in glxgears. So I'd take Zgornel's advice.

some more info:
[http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark](http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark)

I know, but if I have more RAM, a faster processor and he same gfx card I should still get at least the same result?

---

### Post by zgornel on 2008-07-05
> **ProbablyX said:**
> I know, but if I have more RAM, a faster processor and he same gfx card I should still get at least the same result?

Normally, not -  because the simple rendering of glxgears is not limited by the GPU but by the CPU and memory subsystem (glxgears try to get maximum number of frames). This means that the card could render 2-3 times that number of frames but the CPU cannot process them. This is also the reason why when testing CPU performance in games it is a good idea to use very low resolutions.

---

