---
title: "Intel graphics driver doing nothing! Installed them, now what?"
date: 2013-07-04
forum: Hardware
---

### Post by DrClone on 2013-07-04
Hello,

I am a 4 days old Ubuntu user, and I am so tired and fed up with this problem with lacking of solutions. I had installed Ubuntu 13.04 onto my HP Slate 2 which installs successfully, except for one tiny problem...the graphics driver. 

The desktop and interface are EXTREMELY SLOW, almost unresponsive and my tablet gets really hot. When I went to check my graphics driver, it is stuck at Gallium 0.4 on llvmpipe(LLVM 3.2, 128bits).

so...I did this to check for hardware acceleration:


/usr/lib/nux/unity_support_test -p
Everything came [COLOR=#008000]yes[/COLOR] except "Not software rendered: [COLOR=#ff0000]no[/COLOR]" and "Unity 3d supported: [COLOR=#ff0000]no[/COLOR]"

Info on OpenGL

OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.2, 128 bits)
OpenGL version string: 2.1 Mesa 9.1.1

THEN I went to check my hardware list by performing:

lspic | grep VGA

And...boom! It reveals my Intel graphics card as "Intel Corporation Device 4102 (rev 04)"

Then I did some research and it is INTEL GMA 600 which all these kernal are from: [http://cateee.net/lkddb/web-lkddb/DRM_PSB.html](http://cateee.net/lkddb/web-lkddb/DRM_PSB.html)

The bad thing...the code or whatever it is is not up on the website.

What can I do! How can I activate my graphics card? Why is the driver showing up as software when I have Intel graphics card installed?

Hardware specification:

HP SLATE 2

INTEL ATOM Z670 1.5 GHZ
2 GB RAM
INTEL GMA 600
32GB SSD
1024x600 TN PANEL

---

### Post by TenPlus1 on 2013-07-04
Linux tries it's best with the GMA 500 and 600 series drivers which tend to work eventually after a lot of time and work...  You may want to read this: [http://comments.gmane.org/gmane.org.user-groups.linux.tolug/59516](http://comments.gmane.org/gmane.org.user-groups.linux.tolug/59516)

---

### Post by Yellow Pasque on 2013-07-04
Poulsbo? Good luck with that... [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

---

### Post by DrClone on 2013-07-04
Since GMA 500 is based on the same PowerVR SGX535. The only difference is the clock speed which the GMA 500 only have 200Mhz while GMA 600 have 400 Mhz, do you think that this driver would work for GMA 600?

---

### Post by DrClone on 2013-07-04
Ahhh screw it, I'm selling this tablet and go grab Acer W500 since it's only $300 and for full Ubuntu/Windows 8 support.

---

