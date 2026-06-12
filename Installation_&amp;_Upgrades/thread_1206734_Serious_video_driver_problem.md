---
title: "Serious video driver problem"
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by litlfrog on 2009-07-07
I installed Ubuntu on an HP Pavilion 761n. Here's what I get for a video controller when I run lspci
nVidia Corporation NVCrush11 [GeForce2 MX Integrated Graphics] (rev b1)

I tried installing the nVidia accelerated graphics driver (version 96) through System -> Hardware Drivers. It worked for about three minutes, then booted me back to a login screen. When I got back in, there were lines of multicolored distortion around the screen and menus would appear far away from where I was clicking. After some trial and error, I figured out how to disable the nVidia driver and go back to the default.

It's obviously nVidia onboard video, but I'm torn here. I don't want to use the kludgy video driver that comes with Ubuntu, but I don't want to risk not being able to see my screen once I start. What's the next step here?

---

### Post by litlfrog on 2009-07-07
Never mind, I couldn't wait for an answer on this. I stuck in an ATI Radeon 9000 card.

---

