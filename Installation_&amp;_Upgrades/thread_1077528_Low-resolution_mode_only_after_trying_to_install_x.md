---
title: "Low-resolution mode only after trying to install xen"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by Siretu on 2009-02-22
Well, after breaking my own rule of taking a backup of things, I installed Xen, or rather, I tried.

The exact command I used, I think was: sudo aptitude install ubuntu-xen-desktop bridge-utils

I followed a guide somewhere that then told me to reboot, and so I did. When it starts again, the gui is lost and it tells me to login. It starts flashing and then the error box comes up that tells me something is broken and I get the options to run in low-resolution, configure or troubleshoot.

Troubleshoot didn't work out for me, since I don't know what I'm looking for. Configure didn't work, I tried using default configuration but got the same problem, got no backup configuration and reconfiguring doesn't seem to work either.

I then ran in low-resolution mode and got a 1280x1024 resolution. I'm on a widescreen and usually have like 1900xSomething.

I removed the xen package but the problem is still there(At least I think it got removed, I used sudo aptitude remove ubuntu-xen-desktop bridge-utils)

What could be the root of this problem? Could it be something in my xorg.conf file? 

Please note than I'm not at all advanced. Also, if you need some more info, just tell me.

---

### Post by cariboo on 2009-02-22
Can you start with a previous kernel and get to your desktop?

Jim

---

### Post by Siretu on 2009-02-22
I can already get to my desktop when I choose the low-resolution mode. 

After some more research, I've come to the conclusion that there's something wrong with my graphic drivers after the installation. 

My graphic drivers are turned off and I can't seem to activate them.

Also, here's the error I get on startup:
```

(EE)NVIDIA(o): Failed to load the Nvidia kernel module!
(EE)NVIDIA(o) ***Aborting***
(EE)Screen(s) found, but none have a usable configuration

```

How do I load with a previous kernel?

---

### Post by Siretu on 2009-02-22
After some more research, I found the problem. Apparently I broke my kernel and my current kernel doesn't go well with NVIDIA which causes the low-resolution mode.

How can I change the kernel?

---

