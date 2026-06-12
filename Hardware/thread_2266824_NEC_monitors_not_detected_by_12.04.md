---
title: "NEC monitors not detected by 12.04"
date: 2015-02-25
forum: Hardware
---

### Post by nickdc on 2015-02-25
I've been running Ubuntu 12.04 since its release on a self-built desktop pc without any problems. My dual monitors were recognised and easily configured for an extended desktop. That pc is out of action pending diagnosis/repairs and I've had to dust off an even older one. It was running 10.04, which I've just upgraded to 12.04.5 with a live cd. The graphics card (Matrox G450) is not capable of dvi output (which the previous one was) but it does have twin vga outputs and the monitors (both NEC 20WGX2 Pro-BK) have inputs for both. I've checked the cable connections carefully. Both monitors display ok, with identical desktop on each, though not in optimum resolution, (and I suspect it's the display rather than a different software issue that prevents me seeing the bottom panel in classic gnome). But when I bring up the system monitor settings I'm shown a single monitor labelled 'laptop', and there's no way of enabling a single desktop spread across both screens. I've googled and read several threads, but haven't yet read anything that pertains to this particular situation (identical monitors on a single, dual monitor capable graphics card). Ubuntu clearly recognises the graphics card as < sudo lshw -C display > gives:

```
*-display               
       description: VGA compatible controller
       product: MGA G400/G450
       vendor: Matrox Electronics Systems Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 82
       width: 32 bits
       clock: 33MHz
       capabilities: pm agp agp-2.0 vga_controller bus_master cap_list rom
       configuration: driver=matrox_w1 latency=64 maxlatency=32 mingnt=16
       resources: irq:16 memory:dc000000-ddffffff memory:dfefc000-dfefffff memory:df000000-df7fffff memory:dfec0000-dfedffff
```


Can someone kindly point me in the right direction to get the displays set up properly?

---

