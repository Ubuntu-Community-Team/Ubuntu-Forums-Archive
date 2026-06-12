---
title: "Hardware Benchmark - Screen capturing - CPU/GPU dependance"
date: 2009-05-08
forum: Hardware
---

### Post by Meelis on 2009-05-08
*So what's your PC capable of when it comes to screencasting?*

Is some GPU better than other!

Pleas write your's fps @ some resolution & Mb/s (24bit frame size x fps). CPU/GPU, Software
--------------

2,14 fps @ 1440x896 (**7,9** Mb/s)
3,30 fps @ 1280x720 (**8,7** Mb/s)
15,0 fps @ 640x320 (**8,8** Mb/s)
*Core 2 Duo e7400 2,8GHz / ATI HD-4670 1Gb* RecordMyDesktop

3D, for example neverball, will lower the RAW power to **4,5** Mb/s
:)

---

### Post by obreiro on 2009-05-08
the command, please?

---

### Post by Meelis on 2009-05-08
> **obreiro said:**
> the command, please?

I don't know command for that.

I calculate so...
1 - Screencasting with RecordMyDesktop @1440x896 / 15 fps.
2 - Copy .ogv video file to windows HD.
3 - Open with VirtualDub
4 - Convert to huffyuv.avi
5 - Open huffyuv format video with Virtualdub
6 - Move with keyboard right (and left) key - notice the first unique frame - move to right and count all similar frames in the row. Repeat the same in multible places in video. If you get most times x similar frames in the row then...
7 - Divide 15 (captured @ fps) with x

**example**
I captured @ 1440x896 / 15 fps.
I had most times 7 (x) identical frames in the row.
15/7 = **2,14 fps**
I use Gimp to save 24bit .BMP image @ captured res (1440x896). It's 3,69 Mb (1 frame size).
3,69 x 2,14 = **7,9 Mb/s**
------

Maybe you can search identical frames in the row from orig .ogv file in linux. Under vista i can't display frame by frame in .ogv format.
:)

---

### Post by Meelis on 2009-05-08
**[COLOR="Red"]NOT IN LINUX[/COLOR]** [COLOR="Red"](Under Vista)[/COLOR]

24,3 fps @ 1280x720 (**63,9** Mb/s)
Core 2 Duo e4500 2,2GHz / ATI HD-3870 512Mb / [camstudio]("http://camstudio.org/") DivX 2-cores

:)

---

### Post by Meelis on 2009-05-09
15 fps @ 1024x600 (**26,25** Mb/s)
Intel Atom N270 / Intel 945 / RecordMyDesktop
:P

---

