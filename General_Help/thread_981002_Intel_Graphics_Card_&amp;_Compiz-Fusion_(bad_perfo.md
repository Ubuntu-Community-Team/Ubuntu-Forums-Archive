---
title: "Intel Graphics Card &amp; Compiz-Fusion (bad performance)"
date: 2008-11-13
forum: General Help
---

### Post by svlad cjelli on 2008-11-13
hello everybody...


I have got some issues with my desktop-effects.

I am runnin compiz-fusion with a Intel-Graphics Media Accelerator X3100, and when i turn on the sphere or something like that, the 3d-performance is very poor. Aliasing and everything begins to stutter.

My old laptop with the predecessor of my X3100, the Graphics Media Accelator 900, just works fine.


What I did is to add the following line in the device-section of my xorg.conf:

```
Option "AccelMethod" "XAA"
```


Now its a bit better, but far away from smooth.

heres my glxgears:

```
philipp@ubook:~$ glxgears
1923 frames in 5.0 seconds = 384.556 FPS
2607 frames in 5.0 seconds = 521.222 FPS
2092 frames in 5.0 seconds = 418.371 FPS
2825 frames in 5.0 seconds = 564.946 FPS
2806 frames in 5.0 seconds = 561.145 FPS
2816 frames in 5.0 seconds = 563.058 FPS
2845 frames in 5.0 seconds = 568.948 FPS
2572 frames in 5.0 seconds = 514.267 FPS
2143 frames in 5.0 seconds = 428.557 FPS
```


I Used Archlinux for the last month and there was no problem...


Can anyone help me with this issue?
Can I add something more to improve my desktop-effects-performance?

Edit:

I now browsed this Thread:

[http://ubuntuforums.org/showthread.php?t=909665&highlight=AccelMethod+Intel&page=3](http://ubuntuforums.org/showthread.php?t=909665&highlight=AccelMethod+Intel&page=3)


But it is closed :-(

Any solutions or improvements up to now?

Greetz
Svlad

---

