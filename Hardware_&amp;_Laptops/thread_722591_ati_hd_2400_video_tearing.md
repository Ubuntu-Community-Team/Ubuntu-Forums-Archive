---
title: "ati hd 2400 video tearing"
date: 2008-03-12
forum: Hardware &amp; Laptops
---

### Post by john-d on 2008-03-12
hello, 
I bought myself a new laptop, an asus a8sr, I got about everything working with it, I just have an incredibly annoying problem: 
with whatever driver I am using (fglrx, radeon, radeonhd, and vesa) whatever distribution (I tried Kubuntu, arch and gentoo), with about every different X.org configuration possible, even with different versions of xorg, I get incredibly disturbing (but discrete) horizontal tearing while watching videos. I though it was a hardware related issue at first, so I reinstalled vista to check if I would get the same thing, but I experienced no such thing under vista.
I don't guess I am the first to get that, so if anyone has found a solution, please post it. Considering there is no way I am going user vista, I need to get that working fine, because without that my computer is as good as trash.
Thank you in advance.

---

### Post by fa2k on 2008-05-02
I have the same problem, but (disturbingly) for a media pc, rather than a laptop. Problem appears on both fglrx and radeonhd drivers, in all video modes (xv,gl,x11). Using 50Hz mode, the tearing is confined to a specific area, in 60Hz mode it is all over the screen, but not as noticeable. 

I ended up using the radeonhd driver from this repository (see Sofware Sources): 
```
URI: http://ppa.launchpad.net/tormodvolden/ubuntu
Distribution: hardy
Components: main

```
An older version of RadeonHD is available by default.
The package is xserver-xorg-video-radeonhd. I don't know if it was worth the trouble, it's not much better, and video acceleration is not supported.

I would go back to Vista in an instant if this was not also an internet gateway. I have no idea where to file bugs or similar, just hope it works out.

---

