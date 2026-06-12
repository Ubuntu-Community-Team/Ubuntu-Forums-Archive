---
title: "AMDGPU+GCN1.1 no longer boots in 19.04"
date: 2019-05-16
forum: Hardware
---

### Post by dc740 on 2019-05-16
Hi,
AMDGPU driver was working fine on previous kernel (4.18.0-17-generic) with my GPU (Sapphire AMD R9 390X Tri-X OC 8GB).
I upgraded to Ubuntu 19.04 and the new kernel no longer boots (I get a black screen after grub)

I tried disabling DPM and DC from the amdgpu driver, it still fails to boot.

These are my kernel parameters when using AMDGPU. I can confirm they work OK on the previous kernel
GRUB_CMDLINE_LINUX_DEFAULT="radeon.cik_support=0 amdgpu.cik_support=1 radeon.si_support=0 amdgpu.si_support=1 amdgpu.dc=1 amdgpu.dpm=1"

The kernel that fails to work is the 5.0 from the default 19.04. Today I upgraded to get the latest patches and I have exactly the same problem.
Current version:
5.0.0-15-generic

I can confirm that removing my custom kernel parameters and using the default radeon driver seems to work, but I also lose the only important thing I care about in my desktop: Vulkan support


Is anyone else having the same issues?

---

### Post by mastablasta on 2019-05-17
have you reported this on launchpad?
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

