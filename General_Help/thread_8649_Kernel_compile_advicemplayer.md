---
title: "Kernel compile advice/mplayer"
date: 2004-12-19
forum: General Help
---

### Post by fuzzix on 2004-12-19
Hello all! Top distro - switched from Mandrake a week or two ago.

I picked up an mplayer build (from multiverse IIRC) which bombs out as follows:

```
$ mplayer
MPlayer 1.0pre5-3.3.4 (C) 2000-2004 MPlayer Team

CPU: Intel Celeron 2/Pentium III Coppermine,Geyserville 964.0 MHz (Family: 6, Stepping: 3)
Detected cache-line size is 32 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

Reading config file /etc/mplayer/mplayer.conf
Illegal instruction
```

The first thing that I notice is the fact that the proc speed is incorrect - It's a 700Mhz P3 Coppermine and looking at the CPU flags MMX, MMX2 and SSE should be implemented on my platform so I don't know what the illegal instruction might be...

...unless, I thought, it's due to the fact that the kernel is compiled for i386 rather than i686 so I got the 2.6.9 sources (again, via apt - deb unstable IIRC) and compiled successfully, apart from the proprietary nVidia GLX module - in fact anything that required GLX in any capacity segfaulted, so I couldn't check mplayer - no Illegal instruction, but a nice SIG11 this time.

I have an idea where the whole process might have failed, but I'd like some advice before trying again. Would I need to revert the current kernel to non-tainted state (remove the restricted modules package) or something else? Or should I just leave it be? "Just use xine and xmms" "Oh, OK"  ;) 

Perhaps this mplayer issue is the reason people are having issues with the moz/fox plugin. Thanks for any suggestions you might have.

---

### Post by diebels on 2004-12-28
uninstall mplayer-custom, and try mplayer-586 from debian-marillat

---

### Post by fuzzix on 2004-12-29
[QUOTE=diebels]uninstall mplayer-custom, and try mplayer-586 from debian-marillat[/QUOTE]
 Thanks! Did that a while back - should have pointed it out.

Still wondering what steps I need to take to compile a kernel, though.

---

