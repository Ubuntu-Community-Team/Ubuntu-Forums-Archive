---
title: "How to use Hardy's nvidia drivers in Intrepid"
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by DinkyDogg on 2009-01-06
My sound just wouldn't work after the upgrade to Intrepid (2.6.27, i think), so I tried booting my old Hardy kernel (2.6.24), in which the sound works fine. I want to stay with Intrepid, but use the old kernel. The problem is, the Nvidia driver binaries that Intrepid uses don't work under the old kernel.

How can I use Hardy's restricted drivers in Intrepid, booting to the 2.6.24 kernel? 

Thanks for any help.

---

### Post by tuxxy on 2009-01-06
What version are the ones you want? v173 drivers should be offered along with v177 in Ibex anyway.

---

### Post by DinkyDogg on 2009-01-06
Thanks for the quick reply,

I tried that. I still got a bunch of errors and had to boot to low graphics mode when booting to the old kernel. Here's a section of it: ```
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

I was guessing that neither the 173 or 177 version offered through jockey on Intrepid worked for the older kernels.

Any ideas?

---

