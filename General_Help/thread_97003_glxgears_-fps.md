---
title: "glxgears -fps"
date: 2005-11-30
forum: General Help
---

### Post by yib on 2005-11-30
I was wondering, is there a difference between the displayed fps from glxgears between hoary and breezy? I tried glxgears on 3 machines and got some strange results:

1) P3 desktop, 32 mb vram: glxgears gave an average of 231 fps, but the gears ran very fast, videos, dvds play no problem.
2) centrino laptop, 64mb vram: no driver installed, glxgears gave an average of 250fps, but the gears were crawling. Videos on hdd play ok, dvds are very choppy.
3) 2.8 Ghz P4, 128 mb vram: ati driver installed and working. glxgears gave 1200 -1300 fps. However gears weren't running as fast as on the p3. videos on hdd plays fine. However, dvd play back is choppy and laggy.

The laptop I excepted to have poor video performance, since there is no acceleration. However, I expected the p4 with ati drivers installed and running to be much better than the p3. 

any ideas? Thanks

-yib

---

### Post by RAOF on 2005-11-30
Ideas:
1) Glxgears is a poor measure of opengl performance (It seriously has an option "-iacknowledgethatthistoolisnotabenchmark" to print the fps :)).  Glxgears uses a **tiny** subset of the opengl subsystem.

2) The perceived rate at which the gears spin is dependent upon a number of things.  Since glxgears will always be running at a fps far higher than the refresh rate of your monitor, how far the gears appear to turn will depend upon the interaction with the fps and the refresh rate.  It should be possible to see them going backwards, with suitable refresh rate/fps :)

3) Choppy DVD playback is likely due to not having DMA enabled on your DVD drive.  See [here]("https://wiki.ubuntu.com/DMA") for how to enable it.

I don't actually know of a good OpenGL benchmark for linux, but glxgears is definitely not one.

---

### Post by dafl00 on 2005-11-30
[Did Someone say BENCHMARKS????????]("http://www.nvnews.net/articles/technology.shtml")

hahah sorry i just couldn't resist

---

