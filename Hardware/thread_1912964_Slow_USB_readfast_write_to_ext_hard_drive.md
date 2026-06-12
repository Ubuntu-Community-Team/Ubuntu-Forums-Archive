---
title: "Slow USB read/fast write to ext hard drive"
date: 2012-01-21
forum: Hardware
---

### Post by ahallubuntu on 2012-01-21
I'm troubleshooting a slow USB reading issue with an external hard drive (actually a USB HD dock) in Ubuntu 10.04, 32 bit, fully updated.

MSI G31TM-P21 motherboard, about 18 months old or so.

On the built-in USB ports (on the back), I get very slow USB reads of about 5MBps (according to a Nautilus copy and to hdparm -t) but fast writes of about 25MBps (according to Nautilus).

Plug in an old USB2 PCI card and things are much faster - closer to 18MBps, but this is a pretty old card, so that is probably about right.  Same enclosure attached to my Ubuntu 10.04 laptop reads at about 25Mbps. 

Booting 11.10 (from another hard drive) on same hardware also gives reads at the faster speeds.

I've ruled most of the obvious things out, then.  I know I could just dump my 10.04 install and upgrade, but I'd like to keep the LTS install for a while longer.

Any suggestions for how to debug this?  I've already looked at dmesg output and see no difference between plugging in the USB to a motherboard USB port vs. PCI card USB port.

Thanks!

---

