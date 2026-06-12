---
title: "[xubuntu] Radeon R9 280 won't boot without nomodeset or radeon.modeset=0"
date: 2020-05-01
forum: Hardware
---

### Post by sparx808 on 2020-05-01
Hi,

I've recently got a new computer and on a fresh install of Xubuntu 20.04, I'm unable to go past grub without editing the grub command to nomodeset or radeon.modeset=0.

According to [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) it is fully supported.

I installed in textmode, but I can see that the live image also doesn't work.

I have tried other live images (Debian, Ubuntu 16) and I have the same result so I don't think it is something specific to Xubuntu perhaps.

```
$ lspci -nn | grep -E 'VGA|Display'
0a:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280] [1002:679a]

```

Some things I have managed to work out:
```

$ dmesg | grep radeon
[    0.501514] [drm] VGACON disable radeon kernel modesetting.
[    0.501529] [drm:radeon_init [radeon]] *ERROR* No UMS support in radeon module!
[   23.487311] [drm] VGACON disable radeon kernel modesetting.
[   23.487331] [drm:radeon_init [radeon]] *ERROR* No UMS support in radeon module!

```

I tried to get the driver from the AMD website as a last resort but that sadly doesn't support 20.04 as of yet. Although research tells me this is ill advised in any case.

Any help much appreciated.

---

### Post by Yellow Pasque on 2020-05-01
What system or motherboard model is this? Is SecureBoot enabled? That can cause some strange issues.

> I tried to get the driver from the AMD website as a last resort but that sadly doesn't support 20.04 as of yet. Although research tells me this is ill advised in any case.

Ill advised indeed. It doesn't support your GPU.

---

### Post by sparx808 on 2020-05-03
Thanks for the reply!

My motherhood is an ASrock Fatal1ty Gaming ITX/ac 

Secure Boot is disabled.

---

### Post by sparx808 on 2020-05-03
I don't think my dmesg output from post #1 is all that relevant because the driver requires KMS...

---

