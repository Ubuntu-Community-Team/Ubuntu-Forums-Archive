---
title: "new problem with nvidia-glx"
date: 2007-04-19
forum: Hardware &amp; Laptops
---

### Post by Zyphrexi on 2007-04-19
Ok this problem was never resolved and feisty was closed, here is the link to the original thread.
[URL="http://ubuntuforums.org/showthread.php?t=413098"]
http://ubuntuforums.org/showthread.php?t=413098[/URL]

I'd like to continue the discussion here if possible, after doing what I said I'd do, there was no change.

---

### Post by volksolwagen57 on 2007-04-19
hey, do a search on synaptic download manager for "linux-restricted-module" without quotes of course and get the module that best fits your type of computer (most likely i386 for intel or just plain amd) mark these for installation and then download "nvidia-glx-legacy" driver. when you're done, just activate it and don't forget to hit CTRL+ALT+BACKSPACE to reload x-windows. i'm pretty sure this will work.
hope this helps.

---

### Post by Zyphrexi on 2007-04-20
I have all my lrm installed, and nvidia-glx-legacy doesn't provide for GeForce 4



[SIZE="3"]nvidia-glx-legacy description[/SIZE]
> 
NVIDIA binary XFree86 4.x/X.Org 'legacy' driver
These XFree86 4.x/X.Org binary drivers provide optimized hardware acceleration
of OpenGL applications via a direct-rendering X Server and supports the TNT,
TNT2, TNT Ultra, GeForce, and GeForce2 chipsets. AGP, TV-out and flat panel
displays are also supported.

[SIZE="3"]nvidia-glx-new description[/SIZE]

> NVIDIA binary XFree86 4.x/X.Org 'new' driver 
These XFree86 4.x/X.Org binary drivers provide optimized hardware acceleration
of OpenGL applications via a direct-rendering X Server and supports the  newer
GeForce, nForce and Quadro families of NVIDIA chipsets.  AGP, TV-out and
flat panel displays are also supported.

If you have a TNT, TNT2, or older GeForce, you may need the nvidia-glx-legacy
package instead of this one. [B]If you have a GeForce4, you may need the nvidia-glx
package.[/B]



---

### Post by Zyphrexi on 2007-04-22
that didn't help and I'm still having problems.

---

