---
title: "Broken Graphics Acceleration Toshiba A105"
date: 2011-04-16
forum: Hardware
---

### Post by SigmaSanti on 2011-04-16
Hi,
I am having trouble when trying to enable accelerated graphics in Ubuntu.
Whenever I try to run compiz, or unity (in Ubuntu netbook) the screen freezes and leaves me only with the background and a (movable) cursor, with everything else missing. I have to run "sudo gdm service stop" to stop and restart gdm, when I login again compiz has been disabled. 
I have a toshiba satellite A105 with a Radeon express 200M.
Any help is appreciated.

Tried some other methods, seems that running compiz slows the rendering down to the point where it appears frozen.

---

### Post by SigmaSanti on 2011-04-16
Never mind, solved it with nomodeset at boot.

---

