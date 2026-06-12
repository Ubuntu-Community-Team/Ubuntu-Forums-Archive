---
title: "Bootup Issues"
date: 2008-11-01
forum: General Help
---

### Post by Megatog615 on 2008-11-01
My system boots fine. However, usplash does not start up correctly or sometimes not at all. Today I booted up Ubuntu without changing it previously and all I got on the screen were vertical cyan and red bars(very very strange indeed; in fact it scared the crap out of me). Other times I get no video, or just a text bootup(equivalent to removing "splash" from the kernel command line).

My system is as follows(with only the relevant bits shown):
CPU: AMD Athlon64 X2 5600+
GPU: NVIDIA Geforce 8800GTS 640MB
Ubuntu 8.10 for AMD64

I have the NVIDIA proprietary drivers installed(177), but that shouldn't be related, right?

Does usplash have issues with the 8800 series on AMD64? I am inclined to file a bug report if other people have the same issue as me(too many times I have filed a bug report but fixed the issue myself afterward).

My kernel command line arguments are just "quiet splash xforcevesa"(defaults).

---

