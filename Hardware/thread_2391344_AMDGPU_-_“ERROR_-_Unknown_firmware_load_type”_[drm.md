---
title: "AMDGPU - “ERROR - Unknown firmware load type” [drm:amdgpu_ucode_get_load_type"
date: 2018-05-08
forum: Hardware
---

### Post by Kanfused on 2018-05-08
[B]drm:amdgpu_ucode_get_load_type [amdgpu]] *ERROR* Unknown firmware load type

[/B]This is on a Ubuntu 17.10 running on an HP 15 hybrid graphics laptop.

  Is this something to worry about? As I understand, this is DRI module  and amdpgu ucode (microcode) loading. When I checked the log, it seems  everything is loading fine, including switcheroo (hybrid graphics). But,  this error message showing ucode?

Log:
```


] amdgpu 0000:01:00.0: enabling device (0400 -> 0403)
[    1.946708] [drm:amdgpu_ucode_get_load_type [amdgpu]] *ERROR* Unknown firmware load type
[    1.965186] amdgpu 0000:01:00.0: VRAM: 2048M 0x000000F400000000 - 0x000000F47FFFFFFF (2048M used)
[    1.965187] amdgpu 0000:01:00.0: GTT: 256M 0x0000000000000000 - 0x000000000FFFFFFF
[    1.965191] [drm] Detected VRAM RAM=2048M, BAR=256M
[    1.965192] [drm] RAM width 64bits DDR3
[    1.965249] [drm] amdgpu: 2048M of VRAM memory ready
[    1.965250] [drm] amdgpu: 3072M of GTT memory ready.
[    1.965958] amdgpu 0000:01:00.0: PCIE GART of 256M enabled (table at 0x000000F400040000).
[    1.966013] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.966013] [drm] Driver supports precise vblank timestamp query.
[    1.966081] [drm] amdgpu: dpm initialized
```

---

