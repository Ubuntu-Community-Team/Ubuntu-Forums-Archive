---
title: "Intel GMA 4500 MHD"
date: 2010-05-20
forum: Hardware
---

### Post by Kidfork on 2010-05-20
Okay so no matter WHAT I do i cannot get this thing to work. I have the latest drivers from the Ubuntu Repo. But no matter what I cannot get 3d acceleration. It doesn't show up in the System > Admin > Hardware Drivers tab. And all my games run funny. However glx gears is promising,

```
tyler@tyler-laptop:~$ glxgears
2762 frames in 5.0 seconds
2530 frames in 5.0 seconds
2855 frames in 5.0 seconds
```

---

### Post by mikewhatever on 2010-05-20
System->Admin-HD is for the restricted Nvidia/ATI drivers that aren't shipped on the cd. The card you use is powered by open source drivers by Intel, but the real problem is, the state of Intel graphics drivers for Linux is abysmal. Some are none existent, other are none functional, and the rest provide extremely poor user experience. In short, if you want to play games, ditch Intel graphics.

---

### Post by cascade9 on 2010-05-20
> KMS (Kernel Mode Setting) is a recent development, and requires that you have at least kernel 2.6.31 and Intel Xorg driver version 2.8. But newer is better. With the 2.6.32 kernel and Intel Xorg driver 2.9 you can expect full functionality including external displays and 3D acceleration. 

[http://www.thinkwiki.org/wiki/Intel_GMA_4500MHD](http://www.thinkwiki.org/wiki/Intel_GMA_4500MHD)

It should be working...doh :( 

BTW, +1 to mikewhatever....intel video is alwaysa bad choice if you want to play game.

---

