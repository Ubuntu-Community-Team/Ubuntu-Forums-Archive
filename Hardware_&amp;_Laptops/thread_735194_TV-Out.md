---
title: "TV-Out"
date: 2008-03-25
forum: Hardware &amp; Laptops
---

### Post by Kiri on 2008-03-25
Can anyone tell me how to setup to play video fullscreen on a tv that is connected to my laptop?
I have a dell xps m1210 with nvidia geforce go 7400.
Running Ubuntu 8.04.

Nvidia propriety drivers are enabled and seem to be working.

---

### Post by jocko on 2008-03-25
One way to do it is to set up your monitor and tv as separate displays (nvidia-settings should be able to do this for you, set the tv as secondary screen).

I'm not sure how different media players handle this, but for mplayer, try this:
```
gedit ~/.mplayer/config
```
and add these two lines to the file:
```
DISPLAY=:0.1
fs=1
```

This will result in mplayer (and gmplayer) opening up fullscreen on your tv, even if you start it from the display on your monitor.

---

