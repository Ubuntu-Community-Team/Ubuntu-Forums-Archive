---
title: "Bad fps and hz (ati)"
date: 2005-08-23
forum: Hardware &amp; Laptops
---

### Post by Farner on 2005-08-23
Hello.
I just installed ubuntu on this computer: amd64 3500+, ati x850xt (pci-express), 1024ram. I dont use the amd64 version of ubuntu.
First I couldnt startx so I tried with this: sudo apt-get install xorg-driver-fglrx , but it still didnt work. So I search abit on the forum and I tried replacing Driver "ati" to "radeon" in the /etc/X11/xorg.conf and now x started.
But when I run glxgears I get like 800fps. Thats the same fps I that I have on a AMX athlonxp 1900+ with geforce2 mx400 and 512ram. So I figured this cant be right.

And I also have a Samsung Syncmaster 959NF and are currently running the res. 1600*1200. But I want it to use 85hz, instead of 60 hz that it's using atm.

EDIT: Fixed the Hz problem, but still have the fps problem. :(
EDIT2: I downloaded the latest drivers from ati's homepage, and changed now from "radeon" to "fglrx" (I couldnt use fglrx before, cus then I would get the same error that I had with the "ati" setting). But now I had about 300fps less, I had about 500 fps in glxgears. :(

---

