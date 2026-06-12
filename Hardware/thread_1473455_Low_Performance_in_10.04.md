---
title: "Low Performance in 10.04"
date: 2010-05-05
forum: Hardware
---

### Post by mriedel on 2010-05-05
Having performance issues in 10.04 64bit. With Eclipse running, even opening drop-down menus seems a bit slow. HD playback is unenjoyably choppy (even 720p). No disk encryption.  This is with "extra" Visual Effects + some custom effects.

Performance is fine on Win7 as well as all previous versions of Windows I've ever used on that PC. No issues with previous versions of Ubuntu either, but that was a while ago and my graphics card has changed in the meantime. Was using an Nvidia GeForce 8800 back then.

```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          3962       3449        513          0        683       1365
-/+ buffers/cache:       1401       2561
Swap:         3906          1       3904
```

I don't know what's using up all that memory. According to System Monitor nothing is. Applications running were Chromium (running Grooveshark), Nautilus, Miro, KeePassX, Pidgin and Terminal.

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series
OpenGL version string: 3.2.9756 Compatibility Profile Context
```

```
$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: ATI Radeon HD 4800 Series
    GL_NV_conditional_render, GL_NV_copy_depth_to_color,
```

Any ideas?

Thanks in advance.

**Update:** With Visual Effects turned off, 720p HD playback is fine. With Visual Effects set to "normal" or higher it becomes choppy again.

Whatever is using up all of my RAM continues to do so even with Visual Effects turned off.

---

### Post by dabl on 2010-05-05
I'm an Nvidia user, so I'm not sharp on what goes on with ATI cards.

However, I think you're looking in the wrong direction -- I don't think it has anything to do with system memory (it could have something to do with graphics card memory).  If system memory was a constraint, there would be swap utilization, and there is not.

Probably it has more to do with CPU resources.  Open a terminal and run "top" or "htop" and observe what goes on there when you run your other packages, browse the web, run flash in the browser, etc. It should become obvious what is using the resources, and then that can be your research focus.

---

