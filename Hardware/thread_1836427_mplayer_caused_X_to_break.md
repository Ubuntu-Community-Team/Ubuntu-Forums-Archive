---
title: "mplayer caused X to break?"
date: 2011-08-31
forum: Hardware
---

### Post by wecing on 2011-08-31
Currently I have both ATI HD 6470M and Intel i5(Intel Graphics HD 3000) on my laptop. Version of my kernel is 2.6.38(so the Intel Graphics chip is somewhat working). I did not install the close-source ATI graphic card driver.

Every time I try to play videos, X will just gone dead, but the audio part was always still working. I also tried to use xv and SDL as the video output, but they make no difference.

I tried running some simple SDL programs. It worked, but starts up extremely slow.

Here is some info that may help:
> wecing@D5:~$ glxinfo
name of display: :0.0
Unrecognized deviceID 116
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  21
  Current serial number in output stream:  24

wecing@D5:~$ sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: NI Seymour [AMD Radeon HD 6470M]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:51 memory:a0000000-afffffff memory:c6500000-c651ffff ioport:5000(size=256) memory:c6520000-c653ffff
  *-display
       description: VGA compatible controller
       product: Sandy Bridge Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:48 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:6000(size=64)

wecing@D5:~$ lsmod | grep radeon
radeon                717227  0 
ttm                    52155  1 radeon
drm_kms_helper         26893  2 radeon,i915
drm                   165567  5 radeon,i915,ttm,drm_kms_helper
i2c_algo_bit           12834  2 radeon,i915
power_supply           13475  3 radeon,battery,ac
i2c_core               23725  7 radeon,videodev,i915,i2c_i801,drm_kms_helper,drm,i2c_algo_bit

---

