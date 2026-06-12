---
title: "Google Earth on Unichrome"
date: 2008-11-16
forum: Hardware
---

### Post by ukch on 2008-11-16
Hi,

I'm using Ubuntu 8.10: The Intrepid Ibex on my 4 year old laptop. I was very impressed to discover that 3D support has recently started working on my hardware, so I rushed out to install Google Earth. Unfortunately, although it works better than I was expecting, it still has some odd flaws. Firstly, upon starting the program, the display is entirely black until I resize it, then it appears about OK. My main problem though, is the complete lack of any text (place names, etc) in the main window. All text appears as empty white boxes, which isn't really very helpful for finding my way around. Everything else works pretty well - zooming and moving the screen isn't even jerky or anything, which has to be a good thing.

Anyway, here is the output of running lspci|grep VGA:
```
01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)
```

I am using the OpenChrome display driver that comes installed by default. I tried installing the latest driver as described [here](https://help.ubuntu.com/community/OpenChrome), but my xserver wouldn't start, so I returned to the default driver. I also tried compiling the drm from source, as described on the same page, but that doesn't seem to have made any difference to anything - I kept the compiled drivers anyway, in case it helps.

So, does anyone have any ideas, or should I just sit here and wait for the next version of Xorg and/or the OpenChrome drivers to come out?

---

### Post by ukch on 2008-11-16
Oh yes, here's a screenshot of the text issue:

[google_earth.png (1005x706px)](http://www.kazbak.co.uk/images/google_earth.png)

As you can see, mostly everything is working fine (apart from the big black section at the bottom, but I can live with that). The only real problem is the missing place names.

And yes, for the pedantic among you, the missing names are not all white rectangles - some of them are other colours.

---

### Post by Fitzcarraldo on 2009-01-04
I'm not sure if it's the same problem that you are experiencing, but one possible cause of missing text in the latest Linux version of Google Earth is missing font information in the xorg.conf file -- see the following thread for details:

_[Google Earth fonts not displayed](http://forum.sabayonlinux.org/viewtopic.php?f=59&t=15638)_

Hope it is of help.

---

### Post by ukch on 2009-01-11
Hi,

Thanks for the pointer, but it doesn't help. I imagine it's probably a hardware issue.

I don't suppose installing the 'quasi-official' version from Medibuntu will help, do you think? Or is it exactly the same? (I just downloaded from the Google website and installed using the script)

---

