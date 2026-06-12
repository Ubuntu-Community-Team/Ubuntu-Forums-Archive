---
title: "video card outputs larger resolution than TV accepts"
date: 2009-06-08
forum: Hardware
---

### Post by sp0tz on 2009-06-08
I have a new computer with an Nvidia GeForce N9400GT running Ubuntu 9.04 (I just installed it today). The video card's box says 1080P HD display support and HDMI ready. My hdtv does not have a hdmi input, so I put an hdmi-Dvi-D converter on an HDMI cable and plugged it all in. The computer WILL output video to the TV, but a larger picture than the TV can handle, I guess. It looks like the sides and top of the picture have been cut off. The proprietary drivers are installed on the computer, and it works fine when hooked up to a monitor, but the sides and top appear to be cut off when I hook it up to the HDTV, whether I set the resolution to 1080, 720, or 480 (vertical). I've been using the nvidia-settings tool to set the resolution, etc. Is there any way I can get this card to output a usable image to the TV?

Oh, also, If you're wondering why I don't just run a DVI cable from the card to the TV, it's because my TV is the one device in the world that uses the DVI-D interface. I was lucky to find a converter that uses it.

---

### Post by sp0tz on 2009-06-09
bump. I've been trying to output a decent resolution to this friggin' tv for about a year. please help?

edit: putting this here for reference. Will try.
[gewitty]("http://ubuntuforums.org/showthread.php?t=1132763") said:
> The problem was that the Nvidia driver was not reading the EDID information being sent by the monitor. This caused it to revert to a basic VESA setup.

The solution was to get a copy of the raw binary EDID file from the manufacturer (Edge10) and force the Nvidia driver to use this by modifying the Xorg.conf file, as per the Nvidia ReadMe (Appendix B) instructions.

This involves adding the following line to the Device section of the Xorg.conf file:

Option "CustomEDID" "DFP:/tmp/edid.bin" (or whatever your filename and path actually are).

This obviously works for pretty much any Nvidia card and any monitor where the EDID information is not being read correctly.

Hope that helps anyone else who's been tearing their hair out with the same problem.

---

