---
title: "Multi-monitor config with Nvidia drivers"
date: 2012-05-10
forum: Hardware
---

### Post by arfink on 2012-05-10
Hi, I am running an Nvidia GPU, and running LSPCI reports its model as this:
```
02:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 8400 GS] (rev a2)

```

When I was running the live version of Ubuntu 12.04 I was able to set up a multi-monitor configuration with ease through the Displays dialog box, including the ability to set what monitors I want panels on. I was also able to set my Wacom tablet to only work on one of my monitors.

When I did a full install and put on the Nvidia proprietary drivers it screwed up all the configuration options. The display dialog no longer shows two monitors, but only one. My Wacom tablet can no longer be made to work on one display, but instead draws all over both of them. Also the displays are only mirrored, not unique, making them useless. 

I have tried to figure out how to make it work with Nvidia's configration tool, but it's such a useless piece of garbage. Anyone know a fix or workaround?

---

