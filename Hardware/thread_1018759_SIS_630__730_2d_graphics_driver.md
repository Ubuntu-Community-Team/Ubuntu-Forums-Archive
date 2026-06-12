---
title: "SIS 630 / 730 2d graphics driver"
date: 2008-12-22
forum: Hardware
---

### Post by gururise on 2008-12-22
I just installed Ubuntu on a spare machine that has embedded SIS 630 graphics.  I just want to view some videos and browse the internet on this machine, but the graphics are excruciatingly slow with the stock x.org drivers. I can see the windows re-draw at 1280x1024 resolution.

I know there exists a 2d driver for the SIS chipsets at [http://www.winischhofer.eu/linuxsisvga.shtml]("http://www.winischhofer.eu/linuxsisvga.shtml")

They are for older X.org versions.  Has anyone been able to get those drivers compiled for Intrepid and X.org 7.4?? :confused::confused::confused:

---

### Post by prshah on 2008-12-22
> **gururise said:**
> Has anyone been able to get those drivers compiled for Intrepid and X.org 7.4??

You can install them by opening a terminal (Applications-Accessories-Terminal) and giving the command ```
sudo apt-get install xserver-xorg-video-sis
``` (or simply [click here]("apt://xserver-xorg-video-sis"))

---

