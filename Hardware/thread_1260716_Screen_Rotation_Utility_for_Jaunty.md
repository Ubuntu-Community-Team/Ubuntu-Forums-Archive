---
title: "Screen Rotation Utility for Jaunty?"
date: 2009-09-07
forum: Hardware
---

### Post by MiniStephan on 2009-09-07
Hello everyone.  I'm using an older tablet PC, and I finally made the switch to Ubuntu.  The only real problem I'm having is that I can't seem to find a screen rotation utility so that I can use my tablet like a tablet without turning around my computer!

Any suggestions?  I'd also like to be able to use my stylus 'eraser', if someone can tell me how to configure that.  I'm using a Toshiba Tecra M4 Tablet.

I have found Cellwriter, though, and that seems like it will help once I get the rotation down.

---

### Post by Favux on 2009-09-07
Hi MiniStephan,

For rotation method 1 or method 3 on the Rotation HOW TO here:  [http://ubuntuforums.org/showthread.php?p=6274392#post6274392](http://ubuntuforums.org/showthread.php?p=6274392#post6274392) will probably work.  I think you have nVidia video so you probably have to add:
```
Option		"RandRRotation"  "on"
```
to your xorg.conf as described in Appendix 1.

Eraser only works in a few programs like Gimp and Inkscape.  To configure them see near the bottom here:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

You'll probably want to look at Xournal too.

Hope this helps.

---

