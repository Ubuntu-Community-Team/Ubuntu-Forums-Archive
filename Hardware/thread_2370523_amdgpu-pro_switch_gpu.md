---
title: "amdgpu-pro switch gpu"
date: 2017-09-04
forum: Hardware
---

### Post by azim3 on 2017-09-04
Hello all,
I have install amdgpu-pro 17.30 with command ./amdgpu-pro-install --px ( I use --px because withouot --px I cannot login after install)
Now everything looks good. output from sudo lshw -C video is: 
```
sudo lshw -C video  *-display               
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:280 memory:de000000-deffffff memory:b0000000-bfffffff ioport:f000(size=64) memory:c0000-dffff
  *-display
       description: Display controller
       product: Topaz XT [Radeon R7 M260/M265]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: c3
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list rom
       configuration: driver=amdgpu latency=0
       resources: irq:281 memory:c0000000-cfffffff memory:d0000000-d01fffff ioport:e000(size=256) memory:df200000-df23ffff memory:df240000-df25ffff
```
My discrete video cart is R7 M445.
BUT Output from xrandr --listproviders is: 
```
xrandr --listprovidersProviders: number : 1
Provider 0: id: 0x46 cap: 0x9, Source Output, Sink Offload crtcs: 4 outputs: 3 associated providers: 0 name:Intel
```
I cannot see AMD card here...
My question is: How to use my discrete cart now with this driver ? How can I run app with AMD card ? 
Thanks all :)

---

