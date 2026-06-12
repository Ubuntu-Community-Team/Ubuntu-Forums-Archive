---
title: "&quot;/usr/X11R6/bin/X&quot; takes a lot of CPU"
date: 2008-12-01
forum: Hardware
---

### Post by aleck on 2008-12-01
hi, all
I'm using ubuntu 8.10 on IBM T61p, I found my system is slow even at idle time. Can anyone help me on this ? Thanks in advance.

Detail description:

After login, I close all the windows except for a terminal and a system monitor, do nothing, I found the CPU is always busy. The two CPUs becomes busy alternatively (I think this is due to the system dispatch), but the sumof both CPU usage is stable at about 60%.

"ps -aux"
I found "/usr/X11R6/bin/X" takes a lot of CPU (nearly 60%), I checked my desktop(integrated graphic card), it's also using ubuntu 8.10, the ratio is about 2% even open highest desktop effect. So I guess there's some wrong with "/usr/X11R6/bin/X" or my configuration.

It doesn't matter which level of desktop effect I'm using, the problems occurs all the time.

Pictures are attached.
ubuntu-cpu-chart1.png is when extra desktop effect is on.
ubuntu-cpu-chart2.png is when no desktop effect is on.

* my laptop:
CPU Intel Core Duo T7700
Memory 4GB
Graphic Card: 256MB nVIDIA Quadro FX 570M

* my desktop
CPU Intel Core Duo E7200
Memory 2GB
Graphic Card: Intel G31/33 integrated graphic card

I hope someone can help me on this, or give some suggestion.
I've searched on the web for a long time, but haven't found much useful.
Thanks very very much...

---

### Post by cariboo on 2008-12-01
you  will get a much better view of what is using all your cpu cycles, if you use in a terminal:

```
top
```

See attached screenshot.

---

### Post by aleck on 2008-12-01
Thanks for you tip, I tried "top", and updated the picture.

I set to no desktop effect,
It seems that "xorg" takes most of the CPU time, as shown in the terminal.
In the system monitor window, as we can see, the curves are quite abnormal.

If I close the system monitor, the cpu usage of "xorg" drop to 4%, but I still feel the system very slow.

any more tips ?
Thanks very much.

---

### Post by sdennie on 2008-12-01
There is a bug with the system monitor where it uses causes a high amount of CPU usage (especially when the window is large).  You'll have to use top or htop to get an accurate picture of how busy your machine is.

---

### Post by aleck on 2008-12-01
Yes, my resolution is large "1920x1200", 
If I use "top", the cpu usage of xorg is about 4%.

I wonder if my system lag is caused by the big resoution?

:-)

---

### Post by boterbram on 2009-01-08
I actually have the same problem. It occured to me it was only after I got some errors due to my nvidia-driver. When using wine for example, it said there was no 3d acceleration or something like that, and when checking with some command (forgot what is wat, it had to grep something with render) it showed an API mismatch, that's all I can remember.
When I now bring up my compiz benchmark, it shows a framrate of around 60 frames/sec, which is just plain awfull (I first had 600-800 frames per second with the same compiz settings :S (laptop is really new and with good specs)).
So my guess is that it's compiz, not using my video driver, but my cpu for the graphics or something like that. What I'm gonna try in a moment is update my video driver again since I downgraded it to prevent the API mismatch.
Be back soon!

---

### Post by boterbram on 2009-01-08
Allright, that did not help:S

I found out watching video's on metacafe is a pain, although other flash-video websites act a lot more user friendly..?

---

### Post by boterbram on 2009-01-08
Allright I fixed it somehow:S Not quiet sure what it was yet, but what I did was go into the CompizConfig Settings Manager to default, the to Display settings and set everything to default. My 700 f/s are back:D Even metacafe seems to work a lot better.

---

