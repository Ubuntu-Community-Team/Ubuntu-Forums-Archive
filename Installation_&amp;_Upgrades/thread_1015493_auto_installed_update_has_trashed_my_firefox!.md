---
title: "auto installed update has trashed my firefox!"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by joesnose on 2008-12-18
Hi anyone else experienced this problem, i just auto installed a new firefox about half an hour ago, now all flash videos are a bit choppy and if i go full screen it is just a black screen with the video the same size in the corner. Anyone know how i can fix this, or what it is that needs fixing, is it a flash or totem, mplayer plugin issue?

Edit:it appears the problem is not with firefox as it happens in my other browsers aswell!

---

### Post by stderr on 2008-12-19
Do you experience the same thing if you switch window manager from compiz to metacity?

I find compiz to be a bit buggy with that sort of thing, but it could just be my setup...

You can switch WMs easily by installing the package compiz-icon

```
sudo apt-get install compiz-icon
```

launching it via 

Applications -> System Tools -> Compiz Fusion Icon

and right clicking the blue icon on your panel. You can then do Select Window Manager -> Metacity.

If that doesn't solve it, then that at least rules out compiz.

---

