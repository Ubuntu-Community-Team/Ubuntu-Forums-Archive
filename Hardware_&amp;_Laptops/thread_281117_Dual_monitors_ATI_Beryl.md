---
title: "Dual monitors ATI Beryl"
date: 2006-10-20
forum: Hardware &amp; Laptops
---

### Post by jokr004 on 2006-10-20
OK, I just got dual monitors working with my ATI card using MergedFB which is running great, the only problem is that when I try to run Beryl, there is no desktop, and the cube workspace only takes up half of the seccond monitor.  Now I know that Beryl can run with twinview, but is it possible with mergedFB?

---

### Post by pinworm on 2006-12-12
i think im having the exact same problem.  at least beryl doesnt crash the computer, but its extremely buggy and ugly.  also the problem with displaying partially on the second monitor happens with certain screensavers as well. i think its due to hitting a max texture size limitation on the video card.

---

### Post by scottDkoDer on 2006-12-29
I was also perplexed by this problem. So I did some research and found that Xgl doesn't like higher resolutions on some cards.  Try setting the MetaModes for MergedFB and modes in the screen section to 640.
> :
Section "Device"
             Driver "ati"
             ...
             Option "MetaModes" "640x480-640x480 640x480"
             ...
EndSection

Section "Screen"
...
              SubSection "Display"
              ...
              Modes "640x480"
              ...
...
EndSection

Section "Screen"
...
              SubSection "Display"
              ...
              Modes "640x480"
              ...
...
EndSection

After you get beryl running on one screen, and then two, you can tweak your xorg settings to see your card's highest supported resolution for Xgl.:cool:

---

