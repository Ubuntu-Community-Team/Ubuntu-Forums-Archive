---
title: "ATI Radeon 9600 low fps"
date: 2007-01-04
forum: Hardware &amp; Laptops
---

### Post by NeuroticKiss on 2007-01-04
Hi bascially I've installed and setup the ati drivers from ATI site and fglrxinfo gives this:

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.6234 (8.32.5)
```

However glxgears outputs this:

```
$ glxgears
1940 frames in 5.0 seconds = 387.827 FPS
1809 frames in 5.0 seconds = 361.795 FPS
1901 frames in 5.0 seconds = 380.176 FPS
1954 frames in 5.0 seconds = 390.775 FPS
1953 frames in 5.0 seconds = 390.578 FPS

```

And that is apparently very low for a 9600 card I've read compared to other peoples results.

Could anyone please help in maybe getting this higher or am I doing something wrong?

---

### Post by ajgreeny on 2007-01-04
I think so.  Even using the open source ati driver with a 9200SE card I get about 850 fps, and if I cover the glxgears window with the terminal, I get over 8000 fps.  I know this last count is more meaninless than most but it was never that good when i tried the fglrx driver in Breezy, the only time I ever got it to work at all.

---

### Post by Fitzy_oz on 2007-01-08
Is the composite extension still enabled in your xorg.conf?    You can try taking the colour bpp down, I haven't tried this and am not sure if you can with ATI Driver.  I have a 960se and get reasonable frame rates.

Try adding this line if it's not there already.
Section "Extensions"
             Option "Composite" "Disabled"
Endsection

:KS

---

