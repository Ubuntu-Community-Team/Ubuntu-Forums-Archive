---
title: "No Nvidia driver for ubuntu (hence, no GUI)"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by dacool25 on 2009-04-29
I'm trying to install Ubuntu Desktop onto one of the servers at school for a project. 

Unfortunately, I don't think that there is a driver that the installer can use to start the GUI so everything runs in text.  I'm fine with that, however once I get it installed, How can I install the correct driver and get a working GUI?

I believe that the video card (or the two in parallel) are currently using the dell-nvidia-9755-4dkms driver in red hat, but again, we're trying to put ubuntu onto it.

Any help is much appreciated

---

### Post by bubba_169 on 2009-04-29
Usually if the correct driver isn't found the display will fall back to vesa which is very basic but should show a gui never the less. What actually happens when you try to boot does it just drop you straight to a command line? if so try typing startx and see what happens...

EDIT: Just a thought, did you by any chance download the alternate install cd instead of the desktop install cd? The alternate uses a text installer by default anyway but once its installed it will boot into a gui.

---

### Post by dacool25 on 2009-04-29
I'll give that a try.

Just out of curiosity, how would I try the vesa driver during installation?

---

### Post by bubba_169 on 2009-04-29
I think it should use vesa automatically if it can't find the right driver for you? If you're seeing a text based installation program its a high chance you have the alternate install cd?

---

