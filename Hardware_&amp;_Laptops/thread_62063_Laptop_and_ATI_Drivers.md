---
title: "Laptop and ATI Drivers"
date: 2005-09-03
forum: Hardware &amp; Laptops
---

### Post by DarkAlpha on 2005-09-03
Hi. I'm new to Ubuntu and have to admit I'm impressed so far. The support sites seem great and I've already fixed a load of small problems using the wiki and stickies on this forum.

I'm now having problems with fglrx and my ATI Radeon Moblity X700 graphics card. I've followed instructions in [http://ubuntuforums.org/showthread.php?t=24557](http://ubuntuforums.org/showthread.php?t=24557) as well as the BinaryDriverHowTo/ATI page of the wiki. I can get everything to work fine, just as long as i set "Driver "ati"" rather than "Driver "fglrx"". When using fglrx X won't start and I'm dropped into a command line.

The XOrg.0.log file looks fine, except for this section : 

```
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
```

Any help greatly appreciated.

(using Ubuntu 5.04 Arch AMD64)

---

### Post by mlord on 2005-09-03
So, what problem do you want help with??

If everything is working fine, leave it alone!

Cheers

---

### Post by s_p_a_r_k_y on 2005-09-03
mlord, I believe he wants 3d accelleration. 

To answer the question commend out the line that has glcore in it, I think its not supposed to be loaded. Also make sure that the module is loaded
```
sudo modprobe fglrx 
```

---

