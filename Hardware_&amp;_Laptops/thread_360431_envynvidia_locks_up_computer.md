---
title: "envy/nvidia locks up computer"
date: 2007-02-13
forum: Hardware &amp; Laptops
---

### Post by jabster on 2007-02-13
Hi.

I am having a bit of a problem with  envy and my FX-6200-128M video card.

I am running the latest kernel on kubuntu edgy, and wanted to get the latest nvidia drivers, so I grabbed envy, which seemed a good way of keeping up to date.

I downloaded and installed envy, and then ran it (via su). When I started the X-server, I got nothing, so I rebooted. I then got an X error telling me that it failed to load modules nvidia & glx, no drivers available. Fatal server error: no screens found.

So, I ran envy again, and now I am getting the pretty nvidia splash screen, but then the whole system freezes up, and I have to do a hard reboot.

Checking the Xorg log, shows:
(WW) NVIDIA(0): Wait (0,6,0x8000,0x00000520,0x00000520)
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX

Any ideas here?

If you need any further log files or output commands, let me know and I'll oblige.

thanks,
john

p.s. This might matter: my whole reason for going to nvidia driver was that my system kept freezing while using the nv driver. I could move the mouse, but that was about it. I was hoping changing to the nvidia driver would solve that problem.

---

