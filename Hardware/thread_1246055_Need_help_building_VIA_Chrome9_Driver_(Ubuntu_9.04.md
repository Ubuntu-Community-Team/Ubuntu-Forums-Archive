---
title: "Need help building VIA Chrome9 Driver (Ubuntu 9.04)"
date: 2009-08-21
forum: Hardware
---

### Post by the_dark_light on 2009-08-21
Hi all,

I've recently installed Ubuntu 9.04 (Desktop) on an HP 2133 mini-note and I'm looking to enable some of the compiz-fusion type desktop effects (I don't hold out much hope of bendy windows etc but the integrated graphics may be able to handle basic compositing)

The 2133 uses a VIA Chrome9 HC graphics controller (From my research it seems to be a VX800 type)

I've downloaded the VIA drivers but I'm completely lost.  I've built VIA Solomon wireless drivers before, which was a simple:

./configure
make
make install
depmod -a

The instructions for installing Chrome9 drivers look more involved and seem to involve making modifications to kconfig.

```
    Step 1: Get kernel source and put them under /usr/src/linux 
    Step 2: Copy FBDev to proper location.
            # cp -a FBDev /usr/src/linux/drivers/video/via
    Step 3: Modify Makefile and Kconfig under /usr/src/linux/drivers/video:
        add line to Makefile
	        "obj-$(CONFIG_FB_VIA)              += via/"

        add below lines to Kconfig
           config FB_VIA
               tristate "VIA UniChrome (Pro) and Chrome9 display support"
               depends on FB && PCI 
               select FB_CFB_FILLRECT 
               select FB_CFB_COPYAREA
               select FB_CFB_IMAGEBLIT 
               select FB_SOFT_CURSOR 
 
           help
               This is the frame buffer device driver for Graphics
               chips of VIA UniChrome Family(CLE266, PM800 / CN400 / CN300,
                                             P4M800CE / P4M800Pro / CN700,
                                             VN800 / CX700 / VX700, K8M890,
                                             P4M890 / CN896 / P4M900, VX800)
               Say Y if you have a VIA UniChrome graphics board. To compile
               this driver as a module, choose M here: the module will be
               called viafb.
```

Has anyone installed this driver before and can explain how this works?

---

