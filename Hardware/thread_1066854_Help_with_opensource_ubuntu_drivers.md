---
title: "Help with opensource ubuntu drivers"
date: 2009-02-11
forum: Hardware
---

### Post by etherealeclipse on 2009-02-11
Found the opensource ati drivers to give me better video quality than the proprietary drivers only problem is though not a major issue (but can have perfectionist tendencies) I can't seem to get videos continue playing while moving the window or using the cube etc is there anything i can try and add to xorg.conf to enable this?
I have a radeon mobility xpress 1150 (200M), ubuntu 8.10.
Thanks.

---

### Post by nixscripter on 2009-02-14
The obvious thing might be your card isn't fast enough. But aside from that, make sure you have direct rendering enabled. Run this in a terminal.

```
glxinfo | grep direct
```

---

### Post by etherealeclipse on 2009-02-14
Yes I get direct rendering, just realised I didn't mention it worked with the proprietary drivers but some how the proprietary drivers made videos look bad and I couldn't watch 720p videos now I can hence I don't want to go back.

---

### Post by nixscripter on 2009-02-17
You might want to try giving the video player direct access to the graphics card:

[http://ubuntuforums.org/showthread.php?t=176636](http://ubuntuforums.org/showthread.php?t=176636)

Run the video player with the **nonXgl** command afterwards.

---

### Post by etherealeclipse on 2009-02-17
Unfortunately this didn't work, though I'm not getting used to this but a fix would still be good, if any help on pin-pointing the problem i can't take a screen shot of the video and I can watch the video through a windows above the video window if it contains a black area.

---

