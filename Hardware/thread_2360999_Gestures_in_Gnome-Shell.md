---
title: "Gestures in Gnome-Shell"
date: 2017-05-10
forum: Hardware
---

### Post by goatboy73 on 2017-05-10
Hi!

I've recently purchased a Laptop (Dell Inspirion 5577) upon which I've bestowed Ubuntu-Gnome Zesty.  Things work well enough, except for some reason gesture support is either very basic, non-existent, or inconfigurable.  For instance: two-finger vertical swipe causes scrolling, which is as expected.  (Two finger) Pinch-to-(un)zoom doesn't work at all.  Three-finger gestures are completely missing (i.e. show overview/apps menu, minimize/maximize, etc).

I've recently read an [article]("http://news.softpedia.com/news/gnome-shell-mutter-to-handle-three-finger-touchpad-pinch-gestures-in-gnome-3-24-510460.shtml") where they rather clearly state that this functionality is already part of Gnome 3.23. Since Zesty ships with 3.24 I would have expected that functionality to be included.  Am I wrong? Am I missing packages or configurations?

If not, where in the settings panel(s) might I find the configuration for what each gesture does (i.e. to configure my own actions)?  The default panel contains nothing on the topic.

Thanks!

---

### Post by #&amp;thj^% on 2017-05-10
All I know is It has been reported Holding down CTRL while pinching or zooming will allow you to perform the gesture.
My small effort.
BTW Have you looked here: "synclient" to list all touchpad features then create a file to execute them at startup.

---

### Post by goatboy73 on 2017-05-11
The synaptics driver doesn't quite integrate nicely with the Gnome UI.  I'm well versed and perfectly capable of working at the command-line level, but I've become old and spoiled/lazy: I'd rather not do that if there are simpler options, simply because I shouldn't have to in this day and age.

I'll give it another shot, and see where that gets me.

Still, I'm wondering why Gnome Shell doesn't have better support for this already since it's supposedly been there since the previous version (3.23)...

---

