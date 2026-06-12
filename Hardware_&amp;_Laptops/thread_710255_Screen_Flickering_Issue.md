---
title: "Screen Flickering Issue"
date: 2008-02-28
forum: Hardware &amp; Laptops
---

### Post by rhgore12 on 2008-02-28
I have loaded Ubuntu 7.10 on my Micron PC Transport T2200 laptop.  My computer has the following specifications:
1.7-GHz/600-MHz Intel Pentium M
512MB of DDR333 SDRAM
Graphics Card - ATI Mobility Radeon 9000 with 64MB dedicated graphics memory
Video Card - NVIDIA Quadro Video Driver

My problem is that the brightness display (pictured below) pops up when I log in and it will not go away.  The brightness bar continuously moves and the screen flickers terribly.  The screen is not stable and dims and brightens rapidly, and the brightness display blocks anything on the screen.  Everything seems to be working except for this annoying problem.  I was wondering if anyone has any ideas on how to fix this issue.   
 
[IMG]http://farm1.static.flickr.com/219/478661199_a6bff411e1.jpg[/IMG]

---

### Post by taurus on 2008-02-28
What if you reconfigure your X server, would that cure the problem?

Open a terminal and run

Applications -> Accessories -> Terminal
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo dpkg-reconfigure -phigh xserver-xorg
```
When it's done, you can restart X again with <Ctrl><Alt>Backspace.

---

