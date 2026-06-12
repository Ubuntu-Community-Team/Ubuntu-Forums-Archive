---
title: "Tiny print area for HP Photosmart C7280 photo tray"
date: 2009-02-18
forum: Hardware
---

### Post by David Valentine on 2009-02-18
I am running Intrepid x64 on a couple of machines that access an HP Photosmart C7280, and am getting the same error on both.  I have added a photo printing queue for printing photos, and set the media size to "Photo or 4x6 index card", the printout mode to "photo (on photo paper)", and the media source to "Photo Tray".  When I go to print (from both GIMP and Image Viewer), I ensure the page set up is set to 4x6 photo paper.  Then when I attempt to print (file/print..), the size reported under image settings are a fraction of what they should be--instead of 6" high by 4"wide, they're 1.62" high by 1.21" wide.  I cannot increase the size, and "print preview" gives me a tiny little postage stamp of an image on screen.  When I print it anyway, the photo is both cropped and surrounded by huge margins (see attached).

I think this is a bug in CUPS, but I wanted to see if anyone else has run into something similar and found a workaround.  Thanks!

[edit1:] Everything else on the printer works perfect.
[edit2:] I have filed this as [bug #331265]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/331265").
[edit3:] After today's (2009.02.19) cups update, the behavior is much worse.  Each time I load an image and navigate to "page setup" in eye of gnome, the reported size of my 4x6 printing paper drops by ~50%.  It's now down to .01" x .01".  This happens whether I load the same or different image, and continues after a system restart.

---

### Post by David Valentine on 2009-03-24
Bump.  At least one other person has confirmed on the bug report that they are experiencing the same issue.  Any ideas?

---

