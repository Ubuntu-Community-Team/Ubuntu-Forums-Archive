---
title: "Unable to boot 64bit without maxcpus=1 or mem=4096M"
date: 2011-05-20
forum: Hardware
---

### Post by bobbydee on 2011-05-20
Hope someone can help me,

It's a wierd motherboard - Arima NM463. Currently running with 2xOpteron 2354's and 16 gig of ram.

32 bit natty: fine
Windows 7 x64: fine

64 bit natty:

using either maxcpus=1 or mem=4096M will allow the system to boot but obviously missing cpu's or memory,

if neither is specified the boot hangs around: Trying to unpack rootfs as initramfs.

BIOS has: ACPI SRAT enabled, but IOMMU disabled (makes no difference either way)

The only other piece of information I have is that the last Ubuntu to boot cleanly in 64 bit is 9.04.

---

