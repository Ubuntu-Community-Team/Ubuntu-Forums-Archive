---
title: "Why doesn't nvidia upload drivers for all kernels released by ubuntu for signing?"
date: 2020-10-04
forum: Hardware
---

### Post by liubomirwm on 2020-10-04
In Windows there is the Windows hardware dev center, and you can sign your drivers to distribute via Windows Update. Why Canonical doesn't have (or it has??) a hardware dev center, where NVidia can upload their driver and build it. Why it HAS (is it mandatory to build it locally with DKMS??) to be built with DKMS on user's machine? Secure boot doesn't work that way because the driver isn't signed. 

[https://docs.microsoft.com/en-us/windows-hardware/drivers/develop/signing-a-driver-for-public-release#getting-a-whql-release-signature](https://docs.microsoft.com/en-us/windows-hardware/drivers/develop/signing-a-driver-for-public-release#getting-a-whql-release-signature)

---

### Post by CatKiller on 2020-10-04
If you don't use DKMS, the driver breaks on kernel upgrades. That was a problem in the early days of Ubuntu.

If you get your driver from Ubuntu's repositories, Canonical can sign it. If you get it from some other place, like a PPA or the Nvidia website, then they can't. You can sign any modules that you trust yourself, and enroll your Machine Owner's Key in your UEFI. If the modules are signed, by Canonical, or yourself, or someone else that your UEFI trusts, then they'll work with Secure Boot.

---

### Post by liubomirwm on 2020-10-06
So packages from archive.ubuntu.com/ubuntu focal-updates/restricted  amd64 Packages are actually signed? I think it's so because i checked  the driver nvidia.ko in /lib/modules/5.4.0-48-lowlatency/updates/dkms  and it was signed by Canonical. So it should be compatible with kernel  secure boot?

---

