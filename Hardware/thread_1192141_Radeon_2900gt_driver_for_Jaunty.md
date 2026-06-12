---
title: "Radeon 2900gt driver for Jaunty"
date: 2009-06-19
forum: Hardware
---

### Post by h2z on 2009-06-19
I've finally reinstall ubuntu, hoping everything runs smooth this time (8.04 was a real pain) but it seems I can't find a good driver for my Sapphire Radeon 2900GT video card. Using EnvyNG, I installed the recommended driver but I have the little "Unsupported hardware" thingy on the lower right side of the screen. Running "fglrxinfo" yields:

```

OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2900 GT
OpenGL version string: 2.1.8575

```

Also, I get about 8k FPS running glxgears (~200 with no driver installed). Computer hardware is AMD X2 4200+, 2 gig ram, Asus M2A-VM motherboard. 

Trying to load catalyst control center does nothing and when opening "display", I get a blank window. What do I do now?

---

### Post by h2z on 2009-06-19
I've also tried to manually install the 9.6 driver from ati.com with almost the same results: glxgears now shows ~8.5k FPS but I still have "unsupported hardware" showing. 


```

stefan@stefan-desktop:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately 1/30427 the monitor refresh rate.
42926 frames in 5.0 seconds = 8585.039 FPS
43720 frames in 5.0 seconds = 8743.970 FPS
42845 frames in 5.2 seconds = 8211.957 FPS
43674 frames in 5.0 seconds = 8734.748 FPS
43790 frames in 5.0 seconds = 8757.989 FPS
43282 frames in 5.0 seconds = 8656.395 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 38 requests (38 known processed) with 0 events remaining.
stefan@stefan-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2900 GT
OpenGL version string: 2.1.8673

stefan@stefan-desktop:~$ glxinfo |grep direct
direct rendering: Yes
stefan@stefan-desktop:~$ uname -r
2.6.28-13-generic

```

---

### Post by h2z on 2009-06-19
I've done some more testing, I get barely 2k FPS when using "normal" visual effects. Running [compiz-check](http://forlong.blogage.de/entries/pages/Compiz-Check) results in:

```

stefan@stefan-desktop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Device 9405
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

```

---

