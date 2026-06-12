---
title: "Ubuntu 13.04 Failed to Detect Asus GT630-SL-2GD3-L Graphic Card"
date: 2013-08-28
forum: Hardware
---

### Post by Steve R. on 2013-08-28
I inserted [Asus GT630-SL-2GD3-L]("http://www.asus.com/us/Graphics_Cards/GT630SL2GD3L/") into the computer and rebooted. The card was not detected.  The display went to low resolution and did not identify the monitor.  I installed the Nvidia-current driver, which made things worse. I now only get a blank (black) screen.  (Other than the screen, the computer seems to be working OK as I can activate programs through the terminal.)  I attempted to fix this by removing the Nividia-current driver, reinstalling the Ubuntu desktop, and reinstalling Xorg; but the blank (black) screen issue was not resolved.

1. Has anyone had experience with the Asus GT630-SL-2GD3-L Graphic Card? Did it work?
2. How should this card be installed?
3. Any advice on how to fix the blank screen.

---------------------------------------------------------------------------------------------------------------------------------------------------
Good news of sorts. I have a second computer with an nvidia card already installed running Ubuntu 13.04.  I removed the existing nvidia card from that computer and installed the Asus GT630-SL-2GD3-L.  The  Asus GT630-SL-2GD3-L worked as expected and correctly identified the monitor. This would point to a defective nvidia driver install. How to fix?

---

### Post by Steve R. on 2013-08-29
Issue #3 was resolved. The blank (black) screen issue was resolved through this website:[ How To Reset Compiz And Unity In Ubuntu 12.10 Or 13.04]("http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html")

---

### Post by Steve R. on 2013-08-30
With all the tweaking and card swapping, the Asus GT630-SL-2GD3-L decided to start working.

---

