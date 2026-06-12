---
title: "No configuration of graphic's card size"
date: 2011-10-20
forum: Hardware
---

### Post by BlackS3th on 2011-10-20
lshw 




*-display:0
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:44 memory:fea00000-feafffff memory:e0000000-efffffff


It should give me as a result the size of the card but it dosent.

Also from glx gears i get 60 fps... that cant be real can it?

---

### Post by papibe on 2011-10-20
What information are you trying to get?

When you talk about "size of the card", Do you mean resolution?

If so, try this:
```
xrandr
```
Hope it helps,
Regards.

---

### Post by BlackS3th on 2011-10-20
example: Video Card: 64 MB with 1.1 Pixel Shader <-- (pixel shader is to much)

Also what do you think about the fps? 60fps is too low isnt it?

your command gave me..

Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 304mm x 190mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
DVI1 disconnected (normal left inverted right x axis y axis)
TV1 disconnected (normal left inverted right x axis y axis)

---

### Post by papibe on 2011-10-20
I believe now you want to find out the video card memory RAM size. Is that so? Then, check this [tutorial]("http://www.cyberciti.biz/faq/howto-find-linux-vga-video-card-ram/").

> **BlackS3th said:**
> Also what do you think about the fps? 60fps is too low isnt it?
Well, you don't have exactly a graphic card per se, but a motherboard with integrated graphics, so for me, it looks good.

Tell us how it goes,
Regards.

---

### Post by BlackS3th on 2011-10-20
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c) (prog-if 00 [VGA controller])
	Subsystem: Dell Latitude D630
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at fea00000 (64-bit, non-prefetchable) [size=1M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]


Thanks friend ... Although i wonder.

I have a dell latitude D630. (i actually got it second hand).
in tech specs of the laptop says:
NVIDIA®  Quadro NVS 135M or Intel® Graphics Media Accelerator X3100 (Up to 256MB shared)...

could they remove the card before selling it to me :( ?


oh .... The GMA X3100 graphics core is an intelligent and responsive graphics engine built into the chipset that is on the motherboard. This integration provides incredible visual quality, faster graphics performance and flexible display options. . .

---

### Post by BlackS3th on 2011-10-20
Yeah .. maybe not fast enough ... Thnx btw!

One more question if you may.
How do i reward people who help me? :P

---

### Post by papibe on 2011-10-20
Those specs mean that are 2 models, one standard with the integrated graphics, and another (may be pricier) with the Nvidia card.

Unless the previous owner was an competent computer technician, I doubt he/she removed the card.

BTW, [here]("http://www.notebookcheck.net/Intel-Graphics-Media-Accelerator-X3100.2176.0.html") you can see that the Graphics Media Accelerator (GMA) X3100 is an integrated (onboard) graphic chip on the Mobile Intel 965GM.

Kind Regards.

---

