---
title: "Nvidia installer conflict solution"
date: 2012-12-04
forum: Hardware
---

### Post by dbbolton on 2012-12-04
**Note: this problem only occurs if you installed the nvidia driver with nvidia's installer. If you used the default Ubuntu method (jockey/apt), this problem should not exist.**

Today, I logged in to Cinnamon to discover that I had *no* window manager or panel, but I could launch Nautilus from the desktop. My .xsession-errors told me that Clutter had crashed due to a fatal error, so I assumed that something happened to my graphics driver (I installed version 304.60 with the nvidia installer because jockey failed repeatedly).

I re-ran the nvidia installer which told me the installation had been altered (by apt, I imagine). The file in question was **/usr/lib/libOpenCL.so**, a symlink.

To fix this conflict, find out what is available:
```
find /usr/lib -iname '*opencl*'                                         
/usr/lib/libnvidia-opencl.so.1
/usr/lib/libOpenCL.so.1.0.0
/usr/lib/libOpenCL.so
/usr/lib/libOpenCL.so.1.0
/usr/lib/libnvidia-opencl.so.304.60
/usr/lib/libOpenCL.so.1

```In this case **libnvidia-opencl.so.304.60** is my only option. Now to fix the symlink:
```

mv /usr/lib/libOpenCL.so /usr/lib/libOpenCL.so.orig
ln -s /usr/lib/libnvidia-opencl.so.304.60 /usr/lib/libOpenCL.so
```Now restart X:
```
/etc/init.d/mdm restart
```And you should be good to go. I made myself a script to save myself the trouble of going through this process every time X is updated, located [here]("https://github.com/dbb/scripts/blob/master/nvidia-opencl-fix.pl").

Note: there was also a similar problem invoving **/usr/lib/xorg/modules/extensions/libglx.so**, but I have not seen it in recent versions of Ubuntu. I also made a script for it [here](https://github.com/dbb/scripts/blob/master/nvidia-glx-fix.pl).

I recommend that you fix this problem manually as I outlined above. If you choose to use my scripts, you do so at your own risk.

---

