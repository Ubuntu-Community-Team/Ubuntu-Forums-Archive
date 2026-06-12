---
title: "intel onboard GPU driver incorrectly using llvmpipe"
date: 2013-10-27
forum: Hardware
---

### Post by cjtech on 2013-10-27
Hey Guys, 

Need some assistance with my media server, I don't usually do heaps of linux so need a hand.

ubuntu is installing the incorrect intel haswell driver for my integrated video, how do I correct using the CLI? All the guides I have found on the net reference the intel graphical utility.

-Video Settings
--GPU: Gallium 0.4 on llvmpipe (LLVM 0x301)
--Screen resolution: 1680x1050@59.95Hz - Full screen
--OpenGL vendor: vmware, inc.
--OpenGL version: 2.1 Mesa 9.0.3

It should be..

-Video Settings
--GPU: Mesa DRI Intel Haswell
--OpenGL Vendor: intel open source technology center
--OpenGL Version: 3.0 Mesa 9.2.1

---

### Post by Yellow Pasque on 2013-10-27
Post /var/log/Xorg.0.log (make sure you use code tags or use a pastebin since it's a lot of text).

---

### Post by cjtech on 2013-10-27
Thanks,

[http://pastebin.com/km2BFH5z](http://pastebin.com/km2BFH5z)

Ive tried multiple version of ubuntu and also installed 3.10 kernel (nothing I have tried made a difference), however my knowledge with linux is limited.

All I was trying to do was setup a HTPC with xbmc but the CPU is going at 100% due to this driver issue.

---

### Post by Yellow Pasque on 2013-10-27
Ok, let me see if I got this.. You have Ubuntu 12.04.x and you installed a new kernel (3.11.x) to make Haswell function, correct? If so, then you'll need some other components updated to get 3D acceleration. Most of what you need (newer libdrm, newer intel ddx driver, newer mesa, etc.) can be obtained from xorg-edgers PPA: [https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=precise](https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=precise)
Even with xorg-edgers, I'm not sure if the libva in Precise is new enough to give you VA-API video decode accel on a Haswell.

Depending on how much time/effort you've put in the current install, it may be easier/quicker just to do a fresh install of buntu 13.10 rather than try to shoehorn a bunch of newer components into Precise..

---

### Post by cjtech on 2013-10-27
13.10 here I come then, although I believe I had same issue on 3.10, but easier to solve you think?

Well by the same issue, it defaulted to use the llvmpipe however I didn't do much troubleshooting on it though.

---

