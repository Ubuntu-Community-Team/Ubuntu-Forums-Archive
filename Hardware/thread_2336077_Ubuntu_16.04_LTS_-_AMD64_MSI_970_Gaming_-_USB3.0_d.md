---
title: "Ubuntu 16.04 LTS - AMD64 MSI 970 Gaming - USB3.0 does not work"
date: 2016-09-04
forum: Hardware
---

### Post by nadamsieee on 2016-09-04
The USB 3.0 ports on my [MSI 970 Gaming motherboard]("https://us.msi.com/Motherboard/970-GAMING.html") (and also the front panel of my case) do not work out of the box.

The USB 2.0 ports work just fine.

Build:
  > Ubuntu 16.04 LTS (fresh install on 3-Sep-2016)
  > AMD FX(tm)-8350 Eight-Core Processor × 8
  > Motherboard: MSI 970 Gaming

In BIOS, I have the following settings:
  > Disabled XHCI hand off in BIOS
  > Disabled EHCI hand off in BIOS
  > Disabled Legacy USB Support in BIOS

---

### Post by nadamsieee on 2016-09-04
**SOLUTION**:

Edit the **GRUB_CMDLINE_LINUX** parameter in **/etc/default/grub** as follows:

> GRUB_CMDLINE_LINUX="iommu=soft"

Then run this command in the terminal:

> sudo update-grub

Finally, **reboot** your machine.

**EXPLANATION**:

[https://www.kernel.org/doc/Documentation/x86/x86_64/boot-options.txt](https://www.kernel.org/doc/Documentation/x86/x86_64/boot-options.txt)

> 
AMD64 specific boot options

IOMMU (input/output memory management unit)

 General iommu options:

    **off** Don't initialize and use any kind of IOMMU.

    **noforce** Don't force hardware IOMMU usage when it is not needed. (default).

    **force** Force the use of the hardware IOMMU even when it is not actually needed (e.g. because < 3 GB memory).

    **soft** Use software bounce buffering (SWIOTLB) (default for Intel machines). This can be used to prevent the usage of an available hardware IOMMU.

I found this solution on this bug report: [https://bugs.launchpad.net/ubuntu/+source/external-storage-manager/+bug/1447267](https://bugs.launchpad.net/ubuntu/+source/external-storage-manager/+bug/1447267)

---

