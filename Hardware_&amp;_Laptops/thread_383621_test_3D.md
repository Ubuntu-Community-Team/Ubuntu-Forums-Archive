---
title: "test 3D"
date: 2007-03-13
forum: Hardware &amp; Laptops
---

### Post by pappy on 2007-03-13
Hi 
I just Installed Kubuntu Edgy. I finished updating the system, installed the nvidia drivers and all seem OK. Can someone tell me how to test if i have 3D acceleration enabled? I run glxgears but it was not very clear.
Thank you

---

### Post by matburton on 2007-03-14
Well if the gears are really jerky that's normally a bad sign ;)
otherwise
```
glxgears -printfps
```
should show you the frame rate. I get about 750 with my i915 with beryl running as well.

You can also have a play around with the screen savers and see if you get slowdown with the OpenGL ones.

Hope that helps!

---

### Post by jhenager on 2007-03-14
Hmmm, I have an 820 and am doing better than that.
jeff@jeff-desktop:~$ glxgears -printfps
5426 frames in 5.0 seconds = 1085.167 FPS
5648 frames in 5.0 seconds = 1129.234 FPS
4884 frames in 5.0 seconds = 976.752 FPS
5592 frames in 5.0 seconds = 1118.387 FPS
5594 frames in 5.0 seconds = 1118.639 FPS
5531 frames in 5.0 seconds = 1106.030 FPS
5590 frames in 5.0 seconds = 1117.873 FPS

Not to say I got a screaming eagle here. Look at my machine specs in my sig.

---

### Post by Motoxrdude on 2007-03-14
```
glxinfo | grep direct
```
If it says "direct rendering: Yes" you are in good shape ;)

---

### Post by matburton on 2007-03-14
> **Motoxrdude said:**
> ```
glxinfo | grep direct
```
If it says "direct rendering: Yes" you are in good shape ;)
Well that would be the quick, easy and accurate way ;) hehe

> **jhenager said:**
> 
Hmmm, I have an 820 and am doing better than that.
jeff@jeff-desktop:~$ glxgears -printfps
5426 frames in 5.0 seconds = 1085.167 FPS
5648 frames in 5.0 seconds = 1129.234 FPS
4884 frames in 5.0 seconds = 976.752 FPS
5592 frames in 5.0 seconds = 1118.387 FPS
5594 frames in 5.0 seconds = 1118.639 FPS
5531 frames in 5.0 seconds = 1106.030 FPS
5590 frames in 5.0 seconds = 1117.873 FPS


I'm not able to get near that because I have an _[[COLOR="Blue"]Nvidia driver issue[/COLOR]]("http://www.ubuntuforums.org/showthread.php?p=2271145#post2271145")_ :(
So if anyone can help with that it would be much appreciated!

---

### Post by pappy on 2007-03-15
Thanks for the help. the glxinfo | grep direct
shows direct rendering yes so i think i'm OK. and here is some output from glxgears

24313 frames in 5.0 seconds = 4862.472 FPS
25303 frames in 5.0 seconds = 5060.577 FPS
25582 frames in 5.0 seconds = 5116.365 FPS
24627 frames in 5.0 seconds = 4925.366 FPS
27385 frames in 5.0 seconds = 5476.894 FPS
32150 frames in 5.0 seconds = 6429.976 FPS
32644 frames in 5.0 seconds = 6528.775 FPS

is this good?
Now if i can manage to make beryl work i'll be a happy linux user :) Oh and something else i don't have the nvidia panel although the drivers are installed. Can someone help with this?
regards

---

### Post by girard on 2007-03-18
> **Motoxrdude said:**
> ```
glxinfo | grep direct
```
If it says "direct rendering: Yes" you are in good shape ;)
Hi! I get this message when i do the glxinfo | grep direct

:~$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
girard@girard-desktop:~$ 

what does it mean? i'm actually just trying out how to use linux on this pc before i install it on my own.. so i don't mess up my own stuff. lol. that's why i'm not really sure whether this system's hardware is equipped with some of the requirements. BTW what does glxinfo | grep direct do? or what does it mean? i'm self-studying so i'd like to know what the commands we copy and paste do. thank you.

---

