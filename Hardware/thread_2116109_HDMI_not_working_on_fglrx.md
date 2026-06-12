---
title: "HDMI not working on fglrx"
date: 2013-02-14
forum: Hardware
---

### Post by AndreasZ on 2013-02-14
Hi everybody,

it might have been a mistake to pick an AMD APU in the first place, but what the hell.

Here's the deal:

- VGA works fine. No issues.
- HDMI works fine too, on TTYn 

Switching X on in the same resolution (fglrx active) screws everything up. Unfortunately, I can't even provide you with an error message, because X doesn't give me one. The only thing it does is tell me that it resumed the frambebuffer due to VT switch, when I check what's wrong switching to TTY1.

It seems to keep trying to get HDMI sync, but without any success. EDID works, modes are provided correctly every time, forcing a mode line does nothing. I could once "trick" it into working by switching around modes with BOTH VGA and HDMI connected and THEN leaving VGA disconnected.

Resuming after suspend destroyed my relief pretty quickly though.

I would provide you with logfiles, but I wouldn't know what to give you. It's an initial ati setup in xorg.conf, nothing special in there, fglrx module is loaded,

fglrxinfo output:

andreas@xbmc:~$ fglrxinfo 
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7540D
OpenGL version string: 4.2.11903 Compatibility Profile Context

glxinfo also lists all the glx extensions necessary.

I'm seriously out of options.

Hardware:

AMD A6-5400k (Radeon HD 7540D) on an ASRock FM2 A75 ITX board. I even played around in the bios, switched everything from performance to compatibility, tried installing the VERY latest catalyst 13.2 beta driver from amd.com - what am I missing?

If you guys need logfiles, just let me know. Just don't expect much, as I said, in my opinion they're pretty useless, even though I've always been convinced that there's nothing that can't be explained by thorough logfile analysis.

Any help appreciated.

Andreas

p.s.: Don't be fooled by the xbmc hostname. This box is running xbmcbuntu, but I installed ubuntu minimal, 12.10 and 12.04 to be sure this is not an xbmc issue.

---

### Post by AndreasZ on 2013-02-14
Update:

back to square one, re-installed XBMCbuntu, which is nothing but a 12.10 install with a few scripts and fglrx added to it.

I managed to trick xorg into syncing again, but only with VGA connected before and during boot. This is the resulting xorg log:

[http://www.lux-medien.com/xorg.log](http://www.lux-medien.com/xorg.log)

notice this part:

```

[   822.883] (II) fglrx(0): Hot-plug event occurs on device: 0:1:0
[   823.010] (II) fglrx(0): Cannot get EDID information for CRT1
[   823.010] (II) fglrx(0): xdl_xs113_atiddxDisplayScreenEnableDisplays
[   886.546] (II) fglrx(0): EDID vendor "SEC", prod id 42250
[   886.546] (II) fglrx(0): Using EDID range info for horizontal sync
[   886.546] (II) fglrx(0): Using EDID range info for vertical refresh
[   886.546] (II) fglrx(0): Printing DDC gathered Modelines:

```


....aaaaaand then there are lots of Modelines of course.

There seems to be no way to get this to work without having VGA connected first, adding a mode via xrandr on the fly and switch to 1920x1080 accordingly.

Still. Any help appreciated. I am already sick of it and considering sending everything back and switching to something intel/nvidia based.

Andreas

---

### Post by AndreasZ on 2013-02-15
Another Update: I booted the system with a short HDMI cable directly attached to the projector, without a post-processing AVR inbetween.

I get the correct EDID now, everything syncs, until I move around in the left-hand menu of XBMC. HDMI seems to lose sync, it flickers, and then it's back on with the next menu option selected.

NOTHING shows up in the Xorg log except for the modes listed. So I am really clueless about what is going on here. If noone replies or has any sort of idea, what might be the problem, I am gonna send the hardware back and get something nvidiaish.

Andreas

---

