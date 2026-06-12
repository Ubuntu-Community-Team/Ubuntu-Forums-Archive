---
title: "help needed in installing i915 driver"
date: 2005-07-21
forum: Hardware &amp; Laptops
---

### Post by mail2sona938 on 2005-07-21
i tried vesa driver, but the graphics is too slow and CPU eating. So I saw the instructions in 

[http://dri.freedesktop.org/wiki/Download#head-f3c794f007343b969bc570c5dd057212ece700be](http://dri.freedesktop.org/wiki/Download#head-f3c794f007343b969bc570c5dd057212ece700be) 
[http://dri.freedesktop.org/wiki/Download#head-f3c794f007343b969bc570c5dd057212ece700be](http://dri.freedesktop.org/wiki/Download#head-f3c794f007343b969bc570c5dd057212ece700be)

and tried to install, but when compiling, it said

[B]Compiling...
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.

[/B]

[I]dri.log file:

make DRM_MODULES=i915.o modules
make[1]: Entering directory `/home/sona/Desktop/dripkg/drm/linux-core'
+ ln -s ../shared-core/drm.h drm.h
+ ln -s ../shared-core/drm_sarea.h drm_sarea.h
+ ln -s ../shared-core/mga_dma.c mga_dma.c
+ ln -s ../shared-core/mga_drm.h mga_drm.h
+ ln -s ../shared-core/mga_drv.h mga_drv.h
+ ln -s ../shared-core/mga_irq.c mga_irq.c
+ ln -s ../shared-core/mga_state.c mga_state.c
+ ln -s ../shared-core/mga_ucode.h mga_ucode.h
+ ln -s ../shared-core/mga_warp.c mga_warp.c
+ ln -s ../shared-core/r128_drv.h r128_drv.h
+ ln -s ../shared-core/r128_drm.h r128_drm.h
+ ln -s ../shared-core/r128_cce.c r128_cce.c
+ ln -s ../shared-core/r128_state.c r128_state.c
+ ln -s ../shared-core/r128_irq.c r128_irq.c
+ ln -s ../shared-core/radeon_drv.h radeon_drv.h
+ ln -s ../shared-core/radeon_drm.h radeon_drm.h
+ ln -s ../shared-core/radeon_cp.c radeon_cp.c
+ ln -s ../shared-core/radeon_irq.c radeon_irq.c
+ ln -s ../shared-core/radeon_mem.c radeon_mem.c
+ ln -s ../shared-core/radeon_state.c radeon_state.c
+ ln -s ../shared-core/sis_drv.h sis_drv.h
+ ln -s ../shared-core/sis_drm.h sis_drm.h
+ ln -s ../shared-core/sis_ds.c sis_ds.c
+ ln -s ../shared-core/sis_ds.h sis_ds.h
+ ln -s ../shared-core/sis_mm.c sis_mm.c
+ ln -s ../shared-core/tdfx_drv.h tdfx_drv.h
+ ln -s ../shared-core/via_drm.h via_drm.h
+ ln -s ../shared-core/via_drv.h via_drv.h
+ ln -s ../shared-core/via_mm.h via_mm.h
+ ln -s ../shared-core/via_ds.h via_ds.h
+ ln -s ../shared-core/via_3d_reg.h via_3d_reg.h
+ ln -s ../shared-core/via_drv.c via_drv.c
+ ln -s ../shared-core/via_ds.c via_ds.c
+ ln -s ../shared-core/via_irq.c via_irq.c
+ ln -s ../shared-core/via_map.c via_map.c
+ ln -s ../shared-core/via_mm.c via_mm.c
+ ln -s ../shared-core/via_dma.c via_dma.c
+ ln -s ../shared-core/via_verifier.c via_verifier.c
+ ln -s ../shared-core/via_verifier.h via_verifier.h
+ ln -s ../shared-core/via_video.c via_video.c
+ ln -s ../shared-core/mach64_drv.h mach64_drv.h
+ ln -s ../shared-core/mach64_drm.h mach64_drm.h
+ ln -s ../shared-core/mach64_dma.c mach64_dma.c
+ ln -s ../shared-core/mach64_irq.c mach64_irq.c
+ ln -s ../shared-core/mach64_state.c mach64_state.c
+ ln -s ../shared-core/i915_drv.h i915_drv.h
+ ln -s ../shared-core/i915_drm.h i915_drm.h
+ ln -s ../shared-core/i915_irq.c i915_irq.c
+ ln -s ../shared-core/i915_mem.c i915_mem.c
+ ln -s ../shared-core/i915_dma.c i915_dma.c
+ ln -s ../shared-core/savage_drv.h savage_drv.h
+ ln -s ../shared-core/savage_drm.h savage_drm.h
+ ln -s ../shared-core/savage_bci.c savage_bci.c
+ ln -s ../shared-core/savage_state.c savage_state.c
rm -f linux
ln -s . linux
make -C /lib/modules/2.6.10-5-386/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
/home/sona/Desktop/dripkg/drm/linux-core/Makefile:279: *** CONFIG_X86_CMPXCHG needs to be enabled in the kernel.  Stop.
make[2]: *** [_module_/home/sona/Desktop/dripkg/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/sona/Desktop/dripkg/drm/linux-core'
make: *** [i915.o] Error 2[/I]
[SIZE=4]

Can anyone help me out....[/SIZE]

---

### Post by damonw5 on 2005-07-22
Have you tried using the "i810" driver instad of "vesa"? This worked great on my lappy with an i915...

---

### Post by shakin on 2005-07-22
I have an i915 on my Dell. I wrote a how-to about using the i810 driver and installing and configuring a tool called 855resolution, which is needed to make the driver work at decent resolutions.

[Check it out](http://www.ubuntuforums.org/showthread.php?t=27029)

---

