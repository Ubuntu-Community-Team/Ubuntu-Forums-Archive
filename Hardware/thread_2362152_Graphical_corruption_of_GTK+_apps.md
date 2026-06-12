---
title: "Graphical corruption of GTK+ apps"
date: 2017-05-24
forum: Hardware
---

### Post by joelittlejohn on 2017-05-24
I'm having some major trouble with GTK+ apps like gedit, gnome-calculator and meld. The canvas/background/text area of all these apps is completely corrupted and not drawn properly. This makes them unusable. Here's an example, see how the gedit text area is filled with corrupted pixels from the browser:

[https://pasteboard.co/aiiaLvEOc.png](https://pasteboard.co/aiiaLvEOc.png)

When I open an app like gedit, the text area shows a corrupted copy of what was below. I can cause the corrupted area to change by dragging the window borders around, but I can't fix it.

I'm using a Dell XPS 9360 (13") with Intel HD 620 graphics. I'm using Ubuntu 17.04 and the i915 driver. Output from lshw -c video:

```
  
*-display
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:277 memory:db000000-dbffffff memory:90000000-9fffffff ioport:f000(size=64) memory:c0000-dffff

```

I have found some evidence online that using 'xua' or 'blt' instead of 'sna' will fix some graphical corruption problems. I've tried this (via Xorg configuration) but it had no effect.

I'm really stuck now. This has only started happening in the last week or so so I think a driver or kernel update has caused this to start. I've tried everything I can find via Google and next step is a complete fresh reinstall :(

---

### Post by jeegiz on 2017-08-21
It's the fault of the ~/.xinputrc file, see [https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/1620806](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/1620806)

After deleting this file, and logout/login problem is gone.

---

