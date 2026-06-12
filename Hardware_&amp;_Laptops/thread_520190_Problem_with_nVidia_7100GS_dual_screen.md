---
title: "Problem with nVidia 7100GS dual screen"
date: 2007-08-07
forum: Hardware &amp; Laptops
---

### Post by warhead on 2007-08-07
Played around with the nvidia-settings app but it won't let me enable twinview so then I went and edited the xorg.conf file:

Mainly added these lines to the Devices section

    Option         "TwinView" "True"
    Option         "TwinViewOrientation" "RightOf"
    Option         "UseEdidFreqs" "False"
    Option         "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
    Option         "SecondMonitorHorizSync" "30-81"
    Option         "SecondMonitorVertRefresh" "60-75"
    Option         "UseDisplayDevice" "DFP,CRT"

Now the log will tell me that it can't find anything on the DFP (using a DVI-VGA converter on the 2nd output), so I tried "CRT-0,CRT-1" and it will tell me it can't find CRT-1.

Another thing is that as soon as I connect the 2nd monitor, I noticed that the first would dim and it would immediately give me a cloned display.

This leads me to think that I've actually gotten ripped off on a cheapo version of the 7100GS that doesn't actually have 2 individual outputs but instead just 2 linked outputs.

I guess the only way to find out is to put this card on a windows machine and see if it can do dual monitor on that. But no windows available, so does anyone else have other suggestions I can try?

Thanks

---

### Post by warhead on 2007-08-07
Sorted, whacked in another video card with dual output and it worked right off the bat.

I guess my theory was right on that 7100GS, took it out and saw a cable linking the DVI to the D-SUB output.

---

