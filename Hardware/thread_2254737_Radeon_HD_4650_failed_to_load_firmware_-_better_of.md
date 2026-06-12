---
title: "Radeon HD 4650 failed to load firmware - better off just getting new card?"
date: 2014-11-29
forum: Hardware
---

### Post by I Use Dial on 2014-11-29
I can see a number of posts with regards to older ATI/AMD cards that are no longer supported. In Ubuntu 14.04 64-bit I have a VistionTek Radeon HD 4650 PCIe x16 video card installed. I can't run anything other than the built-in display at 1024x768.

I get the following:

```
$ dmesg | egrep 'drm|radeon'
[    5.527134] [drm] Initialized drm 1.1.0 20060810
[    5.591796] [drm] radeon kernel modesetting enabled.
[    5.591874] fb: conflicting fb hw usage radeondrmfb vs VESA VGA - removing generic driver
[    5.592565] [drm] initializing kernel modesetting (RV730 0x1002:0x9498 0x1545:0x4330).
[    5.592593] [drm] register mmio base: 0xFE9F0000
[    5.592596] [drm] register mmio size: 65536
[    5.592752] radeon 0000:01:00.0: VRAM: 512M 0x0000000000000000 - 0x000000001FFFFFFF (512M used)
[    5.592757] radeon 0000:01:00.0: GTT: 1024M 0x0000000020000000 - 0x000000005FFFFFFF
[    5.592760] [drm] Detected VRAM RAM=512M, BAR=256M
[    5.592763] [drm] RAM width 128bits DDR
[    5.593295] [drm] radeon: 512M of VRAM memory ready
[    5.593298] [drm] radeon: 1024M of GTT memory ready.
[    5.593313] [drm] Loading RV730 Microcode
[    5.593338] radeon 0000:01:00.0: Direct firmware load failed with error -2
[    5.593342] radeon 0000:01:00.0: Falling back to user helper
[    5.608499] r600_cp: Failed to load firmware "radeon/RV730_pfp.bin"
[    5.608505] [drm:rv770_init] *ERROR* Failed to load firmware!
[    5.608511] radeon 0000:01:00.0: Fatal error during GPU init
[    5.608517] [drm] radeon: finishing device.
[    5.630462] [drm] radeon: ttm finalized
[    5.630857] radeon: probe of 0000:01:00.0 failed with error -2
```

Would I be better off just getting a different card? Or is there some other driver I can't find that would work for me? Are the older Nvidia cards supported? I mostly just want a cheap, fanless card that is compatible with PCIe 2.0.

---

### Post by Mark Phelps on 2014-11-29
> Or is there some other driver I can't find that would work for me? 

Unfotunately, the fglrx driver no longer works with the Radeon HD 4x-series as AMD dropped Linux support for them last Summer. Ubuntu versions newer than 12.04.1 updated their X-servers to a newer version that is incompatible with the noe "legacy" Radeon HD 4x-series fglrx drivers.

You are stuck using the default open-source Radeon drivers -- which are installed by default.

IF you've tried to force the installation of fglrx drivers, you need to restore the original Radeon open-source drivers.

---

### Post by jeremy31 on 2014-11-30
Did you install linux-firmware?  Any result from ```
ls /lib/firmware/radeon/ | grep RV730
```

---

### Post by I Use Dial on 2015-02-03
The fglrx package is not installed.

```
# ls /lib/firmware/radeon/ | grep RV730
ls: cannot access /lib/firmware/radeon/: No such file or directory
```

Sorry for the necromancy. I coudln't get to this machine until just now, and ugh, it is so painful to use.

---

### Post by mastablasta on 2015-02-04
```
[    5.593338] radeon 0000:01:00.0: Direct firmware load failed with error -2
[    5.593342] radeon 0000:01:00.0: Falling back to user helper
[    5.608499] r600_cp: Failed to load firmware "radeon/RV730_pfp.bin"
[    5.608505] [drm:rv770_init] *ERROR* Failed to load firmware!
[    5.608511] radeon 0000:01:00.0: Fatal error during GPU init
```

the chip should be well supported by opensource drivers. you could try getting a newer kernel with hardware enablement stack. also try no modesetting boot option.

---

