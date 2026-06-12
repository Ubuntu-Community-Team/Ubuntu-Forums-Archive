---
title: "Having Trouble With Radeon 6870"
date: 2018-02-15
forum: Hardware
---

### Post by bradshaw on 2018-02-15
Ubuntu detects it and I do get a picture from it but I don't think I am using the correct drivers. Is there a way I can test this? I've tried looking for driver information and I'm getting results for previous LTS releases for proprietary drivers and this like for open source drivers that I am having trouble understanding

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

I'm not sure what to do here or what output I should paste. 

What I do know, from using applications, is that my intel integrated graphics is doing a better job. How can I verify that I have the right drivers installed and that I am getting the performance I am supposed to get?

---

### Post by QIII on 2018-02-15
Hello!

What release of Ubuntu are you running?

---

### Post by bradshaw on 2018-02-15
16.04

---

### Post by QIII on 2018-02-15
Thanks.

Would you post the results of 

```
lsmod | grep radeon
```

?

---

### Post by Yellow Pasque on 2018-02-15
```
glxinfo | grep string
```

You want to see "Gallium 0.4 on AMD (something)" for the renderer string.

---

### Post by bradshaw on 2018-02-17
> **QIII said:**
> Thanks.

Would you post the results of 

```
lsmod | grep radeon
```

?

radeon               1507328  3
i2c_algo_bit           16384  1 radeon
ttm                    98304  1 radeon
drm_kms_helper        151552  1 radeon
drm                   352256  6 radeon,ttm,drm_kms_helper

> **Temüjin said:**
> ```
glxinfo | grep string
```

You want to see "Gallium 0.4 on AMD (something)" for the renderer string.

server glx vendor string: SGI
server glx version string: 1.4
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
OpenGL vendor string: X.Org
OpenGL renderer string: AMD BARTS (DRM 2.49.0 / 4.10.0-37-generic, LLVM 5.0.0)
OpenGL core profile version string: 3.3 (Core Profile) Mesa 17.2.8
OpenGL core profile shading language version string: 3.30
OpenGL version string: 3.0 Mesa 17.2.8
OpenGL shading language version string: 1.30
OpenGL ES profile version string: OpenGL ES 3.0 Mesa 17.2.8
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.00

---

### Post by Yellow Pasque on 2018-02-17
Well, I guess they don't print the "Gallium 0.4 part" anymore, but everything looks correct there. Is there a specific application the 6870 is struggling with?

---

### Post by bradshaw on 2018-02-17
I have integrated graphics

server glx vendor string: SGI
server glx version string: 1.4
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) HD Graphics 530 (Skylake GT2) 
OpenGL core profile version string: 4.5 (Core Profile) Mesa 17.2.8
OpenGL core profile shading language version string: 4.50
OpenGL version string: 3.0 Mesa 17.2.8
OpenGL shading language version string: 1.30
OpenGL ES profile version string: OpenGL ES 3.2 Mesa 17.2.8
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20

And it does much better? I thought this card would've been an improvement. Specs for the card says OpenGL 4.1 but it doesn't seem to be the case for the card as it is now on my system?
[http://hwbench.com/vgas/radeon-hd-6870-vs-hd-graphics-530-skylake-gt2](http://hwbench.com/vgas/radeon-hd-6870-vs-hd-graphics-530-skylake-gt2)

---

### Post by Yellow Pasque on 2018-02-17
> And it does much better?
Be more specific. What are you having issues with: video playback, web browsing, games, all of the above?
If you want, you can try the absolute latest 3D driver (it's unofficial, so it's at your own risk, of course): [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers/](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers/)

> Specs for the card says OpenGL 4.1 but it doesn't seem to be the case for the card as it is now on my system?
[https://www.phoronix.com/scan.php?page=news_item&px=R600g-Soft-FP64-2018-Alive](https://www.phoronix.com/scan.php?page=news_item&px=R600g-Soft-FP64-2018-Alive)

If you really have a program that requires OpenGL 4, you can try and override the version and see what happens:
```
MESA_GL_VERSION_OVERRIDE=4.1 MESA_GLSL_VERSION_OVERRIDE=410 <program name>
```

---

