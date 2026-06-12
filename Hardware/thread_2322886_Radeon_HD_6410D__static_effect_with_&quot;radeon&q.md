---
title: "Radeon HD 6410D : static effect with &quot;radeon&quot; opensource driver"
date: 2016-05-01
forum: Hardware
---

### Post by magowiz82 on 2016-05-01
Hi,
since upgrade to ubuntu 16.04 xenial LTS, the system wants to remove fglrx-core, so I removed it, I read after that 16.04 dropped support to fglrx binary drivers and I need to use open source radeon driver, anyway, on next reboot, the only thing I get from my GPU is a static tv effect (like the old analogic tv).
I read in this page [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) that my card should be supported, infact here it is the output from lspci :
```
$ lspci -nn | grep VGA
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Sumo [Radeon HD 6410D] [1002:9645]

```
Infact Sumo chipset is listed in fully supported devices.
The last lines of dmesg tells :
```
[   74.117110] radeon 0000:00:01.0: ring 0 stalled for more than 10376msec
[   74.117126] radeon 0000:00:01.0: GPU lockup (current fence id 0x0000000000000002 last fence id 0x0000000000000004 on ring 0)
[   74.117252] [drm:r600_ib_test [radeon]] *ERROR* radeon: fence wait failed (-35).
[   74.117285] [drm:radeon_ib_ring_tests [radeon]] *ERROR* radeon: failed testing IB on GFX ring (-35).

```

What do you suggest ? Tell me if you need further information.

---

### Post by magowiz82 on 2016-05-07
bump

---

