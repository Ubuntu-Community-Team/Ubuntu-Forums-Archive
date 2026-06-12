---
title: "Ubuntu 16.04.3 (64 bit) amdgpu"
date: 2017-08-12
forum: Hardware
---

### Post by lee48 on 2017-08-12
I upgraded my kernel to mainline 4.12.x and got a bunch of firmware warnings that seem related to my video hardware. But, I haven't found a source for the firmware. lspci gives VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Carrizo (rev c5). I've tried installing the amdgpu-pro software and that didn't help.

```
W: Possible missing firmware /lib/firmware/amdgpu/vega10_smc.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega10_asd.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega10_sos.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega10_rlc.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega10_mec2.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega10_mec.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega10_me.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega10_pfp.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega10_ce.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega10_sdma1.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega10_sdma.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega10_uvd.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega10_vce.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/polaris11_k_smc.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/polaris10_k_smc.bin for module amdgpu
```

---

