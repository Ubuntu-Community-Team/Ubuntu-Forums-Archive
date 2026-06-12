---
title: "xserver-xorg-video-radeon"
date: 2009-11-03
forum: Hardware
---

### Post by barna on 2009-11-03
Hi,

Since ubuntu-7.10 I gave a chance to every release, but none of them were capable of handling all my hardware on a 5-year old toshiba satellite.
Now, 9.10 seemed to be OK (several weeks of testing, although at the beginning there were problems with the graphics driver, like agonizingly slow panning in a CAD software in 2D, and slow video playback, but this was solved after an update of xserver-xorg-video-radeon). So finally I erased 7.10 and installed 9.10. 

I am using VariCAD for mechanical design. It is now working fine, except if I change desktop. When changing back to the desktop where VariCAD is running, its 3D screen is frozen, does not respond to the mouse, etc. I guess this is a driver issue, and not an app issue.Any idea?

Thanks

---

### Post by barna on 2009-11-05
I regret very much not having kept the good old Ubuntu-7.10...
I have also the following problem with (probably) the video driver when connecting to a video projector:

Although under ubuntu 7.10 and ATI's fglrx driver, I could not use the
Fn+F5 keys to switch between external VGA and the notebook's monitor, but if I changed it under Windows, then rebooting to ubuntu-7.10 was fine.
Now, whatever I do, there is no video output on the notebook's monitor, and the video projector connected to the VGA output is flickering: it is changing with a period of about 1s between 3 states: 2 different aspect ratios, and the 'No signal' blank screen. The projector works perfectly under Windows, so it's not a hardware issue.

xserver-xorg-video-radeon:
1:6.12.99+git20090929.7968e1fb-0ubuntu1

(--) PCI:*(0:1:5:0) 1002:4437:1179:ff10 ATI Technologies Inc Radeon Mobility 7000 IGP rev 0, Mem @ 0xa0000000/134217728, 0xe0000000/65536, I/O @ 0x0000c000/256, BIOS @ 0x????????/131072

---

