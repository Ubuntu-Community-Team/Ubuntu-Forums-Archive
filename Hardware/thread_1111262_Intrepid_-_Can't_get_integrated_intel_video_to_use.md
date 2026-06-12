---
title: "Intrepid - Can't get integrated intel video to use proper non-generic vga driver"
date: 2009-03-30
forum: Hardware
---

### Post by arcterex on 2009-03-30
Hey all... just realized that the reason I can't get compiz going on my 8.10 install is that the video driver it's using is the generic VGA, not the proper intel one. 

Hardware is a modern PC with Asus P5Q-EM using the integrated graphics driver, an X4500HD according to the asus page. My lspci info:

```

00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
        Subsystem: ASUSTeK Computer Inc. Device 8276
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at fe400000 (64-bit, non-prefetchable) [size=4M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at cc00 [size=8]
        Capabilities: <access denied>


```

When I run displayconfig-gtk and going into the graphics card section it shows 2 cards (wtf?) and both are set to 'vesa - Generic VESA-compliant video cards'.  So it's using generic VGA instead of the intel.  If I select intel or i810 from the dropdown and hit 'test' I just get 'configuration test failed'.  No indication of what failed of course :(

Any thoughts or ideas?

---

