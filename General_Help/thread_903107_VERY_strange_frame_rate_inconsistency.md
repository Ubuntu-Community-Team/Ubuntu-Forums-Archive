---
title: "VERY strange frame rate inconsistency"
date: 2008-08-27
forum: General Help
---

### Post by perillux on 2008-08-27
OK, every time I have EVER run glxgears I get from around 285 to 295 fps.
I have NEVER seen it reach 300fps.

Ok, so then just now I type glxgears and press enter (just like always) and when it starts printing the FPS I am not only getting 300fps, I was getting about 400fps!!!
I couldn't believe my eyes.  So I close glxgears, and then **IMMEDIATELY, WITHOUT DOING ANYTHING ELSE** I press up so that I see 'glxgears' in the console again, and I then press enter, and I was back to 290 fps...  excuse me but, WTF!

> jason@ubuntu-laptop:~$ glxgears
1979 frames in 5.0 seconds = 395.641 FPS
1981 frames in 5.0 seconds = 396.087 FPS
1983 frames in 5.0 seconds = 396.527 FPS
1953 frames in 5.0 seconds = 390.406 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 24409 requests (23038 known processed) with 0 events remaining.
jason@ubuntu-laptop:~$ glxgears
1469 frames in 5.0 seconds = 293.720 FPS
1470 frames in 5.0 seconds = 293.865 FPS
1470 frames in 5.0 seconds = 293.968 FPS
1456 frames in 5.0 seconds = 291.134 FPS

I doubt that little error in between them has much to do with it.  I get that when I close glxgears via alt+f4.  If I simply press escape then I get no error like that.

I then ran glxgears again 3 times after that.  They all showed around only 290 fps again.

What could possibly cause this increase in fps, and what could possibly cause it to suddenly stop?

---

### Post by Crafty Kisses on 2008-08-27
That's really weird, post the ouput of > glxinfo

---

### Post by tuxxy on 2008-08-27
lol what about mine then :confused: :lolflag:

```
:~$ glxgears
46223 frames in 5.0 seconds = 9244.529 FPS
46938 frames in 5.0 seconds = 9387.399 FPS
46120 frames in 5.0 seconds = 9223.916 FPS
44482 frames in 5.0 seconds = 8896.369 FPS
45938 frames in 5.0 seconds = 9187.447 FPS
43560 frames in 5.0 seconds = 8711.875 FPS


```

---

### Post by mb_webguy on 2008-08-27
Wow... and I thought I was doing good at @2050fps...```
matt@the-tardis:~$ glxgears
10207 frames in 5.0 seconds = 2041.311 FPS
10283 frames in 5.0 seconds = 2056.560 FPS
10271 frames in 5.0 seconds = 2053.905 FPS
10309 frames in 5.0 seconds = 2061.699 FPS
10228 frames in 5.0 seconds = 2045.044 FPS
10303 frames in 5.0 seconds = 2060.537 FPS

```

---

### Post by perillux on 2008-08-28
AHA!  I figured it out!  But the answer seems to me to be far stranger than the problem...

I was messing around with stuff trying to see if I could recreate what happened.  I noticed that if I switched between different workspaces the fps increase to 1000+  I tried leaving glxgears open on workspace1 and switched to workspace2 and left it like that.  When I went back to workspace1 it was showing 3000+ fps.
This actually makes sense.

The strange thing is, that if I start glxgears, I am getting 290fps, then if I switch to workspace2 and then back to workspace1 and then as long as I leave glxgears open I am getting 390fps !! that is strange.

> 1452 frames in 5.0 seconds = 290.201 FPS
1469 frames in 5.0 seconds = 293.715 FPS
1469 frames in 5.0 seconds = 293.663 FPS
1469 frames in 5.0 seconds = 293.645 FPS
1469 frames in 5.0 seconds = 293.713 FPS
1469 frames in 5.0 seconds = 293.708 FPS
1469 frames in 5.0 seconds = 293.676 FPS
**2963 frames in 5.0 seconds = 592.369 FPS**
1985 frames in 5.0 seconds = 396.836 FPS
1984 frames in 5.0 seconds = 396.631 FPS
1985 frames in 5.0 seconds = 396.824 FPS
1984 frames in 5.0 seconds = 396.798 FPS
1984 frames in 5.0 seconds = 396.630 FPS
1976 frames in 5.0 seconds = 395.054 FPS
1975 frames in 5.0 seconds = 394.912 FPS
1976 frames in 5.0 seconds = 395.049 FPS
1977 frames in 5.0 seconds = 395.234 FPS
1976 frames in 5.0 seconds = 395.075 FPS
1976 frames in 5.0 seconds = 395.144 FPS
1957 frames in 5.0 seconds = 391.382 FPS
1975 frames in 5.0 seconds = 394.973 FPS
1975 frames in 5.0 seconds = 394.911 FPS
1976 frames in 5.0 seconds = 395.014 FPS

See how everything before the line in bold is 290fps and everything after is 390fps?

I let it run at length so u all could see that it somehow changes something that doesn't change back until I close the program.

The part that is in bold is when I switch to workspace2 and then back to 1.

NOTE: I'm NOT leaving it on workspace2.  I go back to workspace1 where glxgears is being rendered.  But now I am getting 390fps.
This is very odd to me....

---

### Post by tuxxy on 2008-08-28
> **mb_webguy said:**
> Wow... and I thought I was doing good at @2050fps...```
matt@the-tardis:~$ glxgears
10207 frames in 5.0 seconds = 2041.311 FPS
10283 frames in 5.0 seconds = 2056.560 FPS
10271 frames in 5.0 seconds = 2053.905 FPS
10309 frames in 5.0 seconds = 2061.699 FPS
10228 frames in 5.0 seconds = 2045.044 FPS
10303 frames in 5.0 seconds = 2060.537 FPS

```

What card are you using? is it even possible I can be achieving anything near 9000 :lolflag:

---

### Post by sdennie on 2008-08-28
I've seen this expression used before but, "glxgears is not a benchmark".  It really is just a simple OpenGL app that can be used to see if OpenGL is working at all on your machine.  If you want to get proper benchmarks, the phoronix benchmarks are starting to come along pretty nicely: [http://www.phoronix.com/scan.php?page=news_item&px=NjY3Mw](http://www.phoronix.com/scan.php?page=news_item&px=NjY3Mw).  If you see wild discrepancies in an isolated test environment then, yes, it's possible that something odd is going on.

---

### Post by mcduck on 2008-08-28
Yeah, you really shouldn't pay much attention to FPS readings in glxgears. There's a reason you used to need to start glxgears with "glxgears --iacknowledgethathistoolisnotabenchmark" to even get the fps output at all.

Actually I think they should disable the default fps output and start using that option again. :D

---

