---
title: "Nvidia Black Screen on Boot"
date: 2009-11-25
forum: Hardware
---

### Post by StampU on 2009-11-25
Finally solved a problem with my Nvidia 9600M booting to a black screen with Nvidia drivers enabled on my HP laptop.  It has to do with a problem with my LCD's EDID.  I got the following error in Xorg.0.log:

(WW) NVIDIA(0): Unable to get display device DFP-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from DFP-0's EDID.

Running nvidia-xconfig --twinview got me close to working, but I only had a display on an external monitor.  My primary LCD was black.

I found a solution here: [http://www.nvnews.net/vbulletin/showpost.php?p=1911568&postcount=14](http://www.nvnews.net/vbulletin/showpost.php?p=1911568&postcount=14)

You have to specify your monitors timings manually. The post explains that you can use:
"Hint #2: you can easily calculate a specific modeline using "gtf".
I.e. "gtf 800 600 70" would calculate the modeline for 800x600@70Hz:"

Which will give you the modeline that you will need in you xorg.conf file.

Twinview help can be found here:
[http://http.download.nvidia.com/XFree86/Linux-x86/190.42/README/chapter-13.html](http://http.download.nvidia.com/XFree86/Linux-x86/190.42/README/chapter-13.html)
as well as searching these forums.

Good luck!

---

