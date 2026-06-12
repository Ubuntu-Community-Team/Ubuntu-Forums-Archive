---
title: "Use your webcam with flash-based sites like Stickam! SOLUTION!"
date: 2008-05-09
forum: Hardware
---

### Post by Vegetarianrage on 2008-05-09
I was having an issue with getting flash to recognize and use my webcam correctly. It turns out that flash for linux is currently only compatible with v4l.However, most distros and programs, Ubuntu included, use v4l. To get it to work you have to sort of proxy the v4l2 output to the v4l drivers. ](*,) "How?" you ask? 

This man has the answer!=D>=D>=D>

[http://www.swift-tools.net/Flashcam/](http://www.swift-tools.net/Flashcam/)

I have tried this and had it works beautifully on my HP DV6700. The only catch is that before you load the flash applet you have to run ```
flashcam -q
``` in a terminal. No biggie! :KS

---

