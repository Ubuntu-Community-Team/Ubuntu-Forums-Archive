---
title: "Hybrid Graphics / HDMI Screen redraw Wierdness"
date: 2014-10-19
forum: Hardware
---

### Post by sgparry on 2014-10-19
Hi All,
I have searched extensively on this problem but have not encountered a work solution yet. Please can someone help?

I have HP tm2 2050ea laptop. It has hybrid Intel / AMD graphics. It is caught between generations in that it seems to have neither a fully muxed nor muxless design. To give you some idea of what I mean:
- Using early vga_switcheroo, The screen display on the panel cannot be seen unless power is applied to the integrated Intel graphics
- The HDMI only functions when the discrete graphics is powered on - this applies under both Ubuntu and Windows
- The proprietary closed source AMD drivers throw errors about the machine having no hardware mux BUT
- vga_switcheroo recognises the mux and appears to function.

The problem I have is that I want to use an external monitorwith the Radeon open source driver, I get serious redraw issues on the HDMI display. Screen updates are always a mouse mouse or key press behind. It makes the system practically unusable.
I  cannot test the closed source AMD driver because no matter which version or instructions I use, I get a dead system with no graphics output.

Any ideas please
Thanks in advance
sgparry

---

