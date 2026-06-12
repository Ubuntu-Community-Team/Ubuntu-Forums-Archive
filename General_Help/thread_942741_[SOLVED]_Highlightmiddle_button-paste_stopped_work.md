---
title: "[SOLVED] Highlight/middle button-paste stopped working, how to fix/check?"
date: 2008-10-09
forum: General Help
---

### Post by HousieMousie2 on 2008-10-09
I have become VERY used to being able to just highlight some bit of text then hit both left and right mouse buttons to paste, but for the most part it has stopped working.

I have no idea how to trouble shoot this... I read something about it being an effect of the xserver, but don't know where to start looking to see if I can pin point and fix the problem... or even if it is truly the xserver's domain.

I am using a Logitech Marble mouse, that has a USB plug, but I use the adapter to plug it into the PS/2.

I had to install the nVidia driver for my graphics card with the xserver shut off... so perhaps this is the cause of the change?  How do I find out/fix it?

Any ideas?

---

### Post by HousieMousie2 on 2008-10-10
uh, never mind, I found it.  Somehow the xorg.conf entry for emulating middle button had been reset to 'no' changed it to 'yes' and all is well.

---

