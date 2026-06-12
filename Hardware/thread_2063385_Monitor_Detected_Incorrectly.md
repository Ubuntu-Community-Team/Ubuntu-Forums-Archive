---
title: "Monitor Detected Incorrectly"
date: 2012-09-26
forum: Hardware
---

### Post by chrisinpants on 2012-09-26
My Dell monitor is detected as a 15 inch but it's actually 17. I'm also getting problems displaying some games properly (eg true combat elite, although et runs fine) with the right side of the screen cut off. Playing with the video settings in game makes no difference, full screen or not. I'd like to see if I can get my full 17 inches on display in the system settings and see where that goes. My xorg.0.log:

[http://paste.ubuntu.com/1229712/](http://paste.ubuntu.com/1229712/)

One thing I noticed when browsing the log, a discrepancy perhaps (??):

......

[ 15210.244] (II) intel(0): clock: 78.8 MHz   Image Size:  300 x **225** mm

......

[ 15210.245] (II) intel(0): Kernel page flipping support detected, enabling
[ 15210.245] (**) intel(0): Display dimensions: (300, **230**) mm
[ 15210.245] (**) intel(0): DPI set to (86, 84)



I've tried running under different desktops too (lubuntu) with no change in the issue.

---

