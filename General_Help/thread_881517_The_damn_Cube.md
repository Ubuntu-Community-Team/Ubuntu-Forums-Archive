---
title: "The damn Cube"
date: 2008-08-06
forum: General Help
---

### Post by jeepers on 2008-08-06
O.K. i'm going to try and post this in a different way :)

Is it possible to have the cube (spinning/rotating) as a desktop background.
The reason i'm asking is, i have the cube working using the mouse, i have even got the spherical effect working, But i'm after having a spinning/rotating cube/sphere on my desktop just like a wallpaper.

cheers
:eek:

---

### Post by easybake on 2008-08-06
> **jeepers said:**
> O.K. i'm going to try and post this in a different way :)

Is it possible to have the cube (spinning/rotating) as a desktop background.
The reason i'm asking is, i have the cube working using the mouse, i have even got the spherical effect working, But i'm after having a spinning/rotating cube/sphere on my desktop just like a wallpaper.

cheers
:eek:

Find a video of what you want. Or create your own using [recordmydesktop]("http://ubuntuforums.org/showthread.php?t=294605")
Download [xwinwrap]("http://www.fsckin.com/2008/04/14/fun-with-xwinwrap-in-compiz-fusion/")
Run the video on loop with this code in terminal```
xwinwrap -ni -o 0.2 -fs -s -st -sp -b -nf -- mplayer -loop 0 -wid WID -quiet /home/blahblah/Videos/blahblah.MPG
```

---

