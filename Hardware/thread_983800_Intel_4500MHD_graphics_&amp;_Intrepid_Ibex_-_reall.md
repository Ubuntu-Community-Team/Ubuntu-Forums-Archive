---
title: "Intel 4500MHD graphics &amp; Intrepid Ibex - really slow?"
date: 2008-11-16
forum: Hardware
---

### Post by beerbelly on 2008-11-16
Hi all,

Pretty new to the forums, but a happy Ubuntu user for quite some time. But, I got me a new laptop recently, and was fortunate enough to be able to install Intrepid right away; both arrived on the same day.

However, the Intel 4500MHD graphics chip makes everything feel really slow and sluggish. Maximizing/minimizing windows just doesn't feel right. The chipset should be fast enough to handle this stuff. Turning desktop effects on and off doesn't seem to make a difference, nor does switching between Compiz and Metacity (using something like Compiz Fusion Icon). The results remain the same: it feels like I'm running Ubuntu on a machine that's just too slow).

Searching the forums has learnt me a couple of things. First: there is no official or optimal driver for the new Intel 4-series of graphics chips yet. Second: I should consider myself lucky that I'm able to run Ubuntu at the correct resolution of 1280x800 at all...

Even though everything runs: is there a place I can follow progress on development of the new Intel drivers? As soon as they arrive, I'd love to install and try them, but for now I don't have any idea where to look.

Any help is much appreciated!

Jeroen

---

### Post by Mizzou_Engineer on 2008-11-29
Intel's Linux graphics website has the latest drivers:

[http://intellinuxgraphics.org/download.html]("http://intellinuxgraphics.org/download.html")

I just got a laptop with an Intel GM45 chipset. It works well enough with the xserver-xorg-video-intel 2.4.1 in Ubuntu 8.10.

---

### Post by Somatik on 2008-11-30
there are a few intrepid intel gfx issues:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/252094](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/252094)
[https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/288650](https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/288650)

---

