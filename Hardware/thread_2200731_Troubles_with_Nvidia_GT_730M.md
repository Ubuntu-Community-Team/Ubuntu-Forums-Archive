---
title: "Troubles with Nvidia GT 730M"
date: 2014-01-20
forum: Hardware
---

### Post by mortemdei on 2014-01-20
I have an Ideapad U430p and this laptop was giving some trouble with the GPU. After sometime I managed to make it work with the instructions here: [http://ubuntuforums.org/showthread.php?t=2178884&page=2](http://ubuntuforums.org/showthread.php?t=2178884&page=2), but I had to uninstall recently and when I tried to reinstall following the same instructions it did not work, I'm back with the same 

```
IdeaPad-U430-Touch:~$ optirun glxgears
[ 9679.067991] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(GPU-0): Failed to initialize the NVIDIA GPU at PCI:9:0:0.  Please

[ 9679.068093] [ERROR]Aborting because fallback start is disabled.
```

The only thing that almost worked was installing the 304 drivers with the xorg-edgers repository disabled, then adding that repository and upgrading. But that only made a few programs run, the rest crashed with a warning that libGl.so wasn't found. Installing nvidia-prime also doesn't work, it boots to a low-quality mode that says the video card is not configured correctly.

I read there was some problem with the new Drivers in the xorg-edgers repo, could this be the reason? what else could I try?

---

