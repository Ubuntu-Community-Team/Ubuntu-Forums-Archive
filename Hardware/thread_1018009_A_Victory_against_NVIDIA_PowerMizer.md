---
title: "A Victory against NVIDIA PowerMizer"
date: 2008-12-21
forum: Hardware
---

### Post by interim descriptor on 2008-12-21
In my experience, PowerMizer is a "feature" that only causes headaches. It's awful that it's not user-configurable.

I just figured out how to trick PowerMizer into thinking that the AC adapter is always plugged in, which FINALLY allows me to get a decent framerate for Compiz.

In my xorg.conf, I just add the following line:
```
Option "ConnectToAcpid" "false"
```

This frees my Dell XPS m1730's GeForce 8700M GT SLI cards from being stuck in the lowest performance level, when using battery power.

Unfortunately, Adaptive Clocking is still enabled, and I cannot reliably make my GPUs stay at their highest performance level, without scripting a call to "nvidia-settings -q all" every 25 seconds. This would be fine, were it not for the fact that this causes a framerate hiccup, and worse, xruns in my low-latency professional music software, or, in lay terms, the audio would skip during a music performance, which isn't remotely acceptable.

Furthermore, to get the best performance, I must disable SLI, which is stupid.

I'm using the latest beta drivers, 180.16.

NVIDIA: Please please PLEASE **PLEASE** fix your drivers so:
[LIST=1]
[*]One can set the clocking properties directly, without performing goofy hacks
[*]Calling nvidia-settings doesn't cause framerate spikes or audio skippage
[*]The driver behaves correctly in a realtime linux kernel
[/LIST]

---

