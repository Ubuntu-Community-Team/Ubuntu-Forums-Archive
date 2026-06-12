---
title: "Compiz Causing Crashes - Curious!"
date: 2008-10-20
forum: General Help
---

### Post by skullmunky on 2008-10-20
I'm getting some inexplicable crashes while using Compiz.  Here's my setup:

ubuntu 8.04 32bit with kde 3.5.9
athlon X2
quadro fx 1400, nvidia-glx-new, 169.12+2.6.24.12-16.34

I'm using compiz via the wonderful compiz-fusion-icon.  Generally everything works fine, but a few things consistently cause crashes:

1. when I put in a blank CD, and choose the option to burn with K3B, X crashes.
2. when I go to the System Settings->Appearance control panel, X crashes
3. when I go to the System Settings->Printer control panel, the whole computer shuts down.

The behavior is repeatable.  When using KWin instead of Compiz for the window manager, it does not happen.  

Any suggestions how to debug this?  I can't figure out what's so special about those apps that it would freak Compiz out that badly. :)

Here is the tail of my Xorg.log, if that means anything:

```

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x7e) [0x80c780e]
1: [0xb7ef6420]
2: /usr/bin/X(ProcPolyPoint+0x14a) [0x808aa9a]
3: /usr/bin/X [0x815075e]
4: /usr/bin/X(Dispatch+0x2cf) [0x808d8df]
5: /usr/bin/X(main+0x48b) [0x807471b]
6: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7c73450]
7: /usr/bin/X(FontFileCompleteXLFD+0x201) [0x8073a91]

Fatal server error:
Caught signal 11.  Server aborting

```

Any chance this could be a bug in something, worth filing, or do I just have something screwy in my configuration?

---

