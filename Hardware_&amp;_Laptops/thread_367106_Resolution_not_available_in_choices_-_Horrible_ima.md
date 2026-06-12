---
title: "Resolution not available in choices - Horrible image in external tft - Lenovo V100"
date: 2007-02-21
forum: Hardware &amp; Laptops
---

### Post by cmavr8 on 2007-02-21
My laptop has a 1280x800 wide display so I got a 19" TFT display of the same aspect ratio (widescreen, 1440x900).

When reconfiguring xorg I select 1280x800, 1280x1024 and 1440x900.

Inside xserver, in screen resolution preferences I can select: 1280x1024, 1280x800, 1024x768, 800x600, 640x480.


1280x1024 works, image stretched but fully viewable. TFT recognizes it as 1280x1024.


1280x800 results in normal image (not stretched) but trimmed top and bottom. TFTrecognizes it as 1280x768.

What the f*** is going on? I've been reading and playing with xorg.conf all day...

Please note that I have the TFT connected all the time, even when reconfiguring xorg. So the gpu thinks there is no laptop's display (remains turned off all the time). If I get the TFT right I will make mods to xorg.conf to clone image to both monitors...

Also, for reference, laptop is a Lenovo 3000 V100 with Intel 945GM Express graphics card. I have installed the Intel driver, I told xorg to use it (i810 intstead of vesa) and I have added Vertical and Horizontal values (for LG 19" 194wt it is 30-83 and 56-75, right? Auto reconfiguration said 30-90 and 50-60 but I corrected them...)

Any ideas?

Thanks

---

### Post by veloce on 2007-02-21
You also need to install "915resolution" this fixes the bios to make the non-standard resolutions available.  See:

[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by cmavr8 on 2007-02-22
Dear reader, please see [http://ubuntuforums.org/showthread.php?t=362463&page=2](http://ubuntuforums.org/showthread.php?t=362463&page=2) where the conversation continues...

---

