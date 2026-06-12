---
title: "Intel video card driver"
date: 2009-10-09
forum: Hardware
---

### Post by petersohn on 2009-10-09
My Intel video card driver works very sluggishly in Jaunty. I could manage to have an acceptable performance with the drivers at [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/) and the 2.6.31 kernel. When Karmic beta came out, I tried the live CD and saw that it works better, so I upgraded my system to Karmic. It screwed up my boot partition, so I had to reinstall Jaunty completely. It worked fine, and the video card drivers from launchpad worked a bit better than the old drivers. Then I tried to install the new kernel again, but it didn't work. After that, the graphics didn't even work under the old kernel, even after removing the new kernel, so I had to reinstall everything again.

And here comes the main problem. Now even if I install the new video card drivers, it screws up the graphics. Reinstalling the old drivers work however.

```
$ glxinfo | grep render
get fences failed: -1
param: 6, val: 0
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 945GM GEM 20090326 2009Q1 RC2 x86/MMX/SSE2
```

---

### Post by Ar(_Zer{} on 2009-10-09
> **petersohn said:**
> My Intel video card driver works very sluggishly in Jaunty. I could manage to have an acceptable performance with the drivers at [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/) and the 2.6.31 kernel. When Karmic beta came out, I tried the live CD and saw that it works better, so I upgraded my system to Karmic. It screwed up my boot partition, so I had to reinstall Jaunty completely. It worked fine, and the video card drivers from launchpad worked a bit better than the old drivers. Then I tried to install the new kernel again, but it didn't work. After that, the graphics didn't even work under the old kernel, even after removing the new kernel, so I had to reinstall everything again.

And here comes the main problem. Now even if I install the new video card drivers, it screws up the graphics. Reinstalling the old drivers work however.

```
$ glxinfo | grep render
get fences failed: -1
param: 6, val: 0
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 945GM GEM 20090326 2009Q1 RC2 x86/MMX/SSE2
```

Why don't you try installing a Karmic Beta system as your main OS? It's very stable now.

---

### Post by petersohn on 2009-10-09
As I said, I tried, but there is the bug with fsck, and I can't use it until it is fixed.

---

