---
title: "Intel GMA 950"
date: 2007-11-14
forum: Hardware &amp; Laptops
---

### Post by reica on 2007-11-14
Feisty does not seem to have support for the Intel GMA 950.
Is there a fix for this?
Does Gutsy have built-in support for this chip?
I want to run a screen resolution of 1440x900 on Inspiron 6400 with the Intel GMA 950.
Are there drivers available somewhere?
Help appreciated.
Rein

---

### Post by daengbo on 2007-11-14
Sadly, the two GMA 950s that I have are limited to only 8MB shared-RAM video. That limits the display, but yours should work within the resolution you want even at 8MB(1440*900*32bits/8bits-per-byte). The GMA was supported in Feisty out of the box with the i810 driver, though I never got the intel driver to work for me. Gutsy works OOTB, too.

If your video is not working, there is some other problem.

---

