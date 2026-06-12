---
title: "Rotating cube with Scroll wheel crashes X"
date: 2008-08-01
forum: General Help
---

### Post by dougie173 on 2008-08-01
I'm having a problem with the rotating cube.

If I rotate it using Ctrl+Alt Left or Right then the cube rotates correctly.

If I have no programs running then when I press the scroll wheel on the mouse then the cube rotates correctly, however as soon as I try this with any window open then it crashes gdm & X

I've searched the forum but been unable to find anything similar

My .xsession-errors file ended with the following message:-

```
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
[1217581851,000,xklavier.c:xkl_engine_start_listen/] 	The backend does not require manual layout management - but it is provided by the applicationICE default IO error handler doing an exit(), pid = 6896, errno = 0
```

And in my Xorg.log:-

```


Backtrace:
0: /usr/bin/X(xf86SigHandler+0x6a) [0x48402a]
1: /lib/libc.so.6 [0x7f90c9dc5100]
2: /usr/lib/dri/i915_dri.so [0x7f90b7193132]

Fatal server error:
Caught signal 4.  Server aborting

(II) AIGLX: Suspending AIGLX clients for VT switch
(II) intel(0): xf86UnbindGARTMemory: unbind key 0
(II) intel(0): xf86UnbindGARTMemory: unbind key 1
(II) intel(0): xf86UnbindGARTMemory: unbind key 2
(II) intel(0): xf86UnbindGARTMemory: unbind key 3
(II) intel(0): xf86UnbindGARTMemory: unbind key 4


```

Thanks in advance for any help

---

