---
title: "eSata external drive wont connect"
date: 2014-06-19
forum: Hardware
---

### Post by adlin5000 on 2014-06-19
I just got an external enclosure that has a eSata port. The drive will connect with the usb but not the eSata.
Here is the dmesg output:

```
[  932.807376] ata8: exception Emask 0x10 SAct 0x0 SErr 0x190002 action 0xe frozen
[  932.807383] ata8: irq_stat 0x80400000, PHY RDY changed
[  932.807388] ata8: SError: { RecovComm PHYRdyChg 10B8B Dispar }
[  932.807398] ata8: hard resetting link
[  933.531306] ata8: SATA link down (SStatus 0 SControl 300)
[  933.531322] ata8: EH complete
[  939.143868] ata8: exception Emask 0x10 SAct 0x0 SErr 0x4050000 action 0xe frozen
[  939.143876] ata8: irq_stat 0x80400040, connection status changed
[  939.143881] ata8: SError: { PHYRdyChg CommWake DevExch }
[  939.143891] ata8: hard resetting link
[  945.716782] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.1 domain=0x0000 address=0x0000000036320440 flags=0x0070]
[  945.716792] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.1 domain=0x0000 address=0x0000000036320450 flags=0x0070]
[  945.755151] ata8: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  945.756558] ata8.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x80)
[  945.756585] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.1 domain=0x0000 address=0x0000000036320420 flags=0x0070]
[  945.756595] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.1 domain=0x0000 address=0x00000000362fa5b0 flags=0x0070]
[  945.756600] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.1 domain=0x0000 address=0x00000000363203e0 flags=0x0070]
[  945.756604] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.1 domain=0x0000 address=0x0000000036320430 flags=0x0070]
[  945.756608] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.1 domain=0x0000 address=0x00000000362fa5c0 flags=0x0070]
[  945.756612] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.1 domain=0x0000 address=0x00000000362fa740 flags=0x0070]
[  945.756618] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.1 domain=0x0000 address=0x00000000362fa600 flags=0x0070]
[  945.756624] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.1 domain=0x0000 address=0x00000000362fa780 flags=0x0070]
[  945.756627] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.1 domain=0x0000 address=0x00000000362fa640 flags=0x0070]
[  945.756631] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.1 domain=0x0000 address=0x00000000362fa7a0 flags=0x0070]
[  945.756635] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.1 domain=0x0000 address=0x00000000362fa680 flags=0x0070]
[  945.756638] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.1 domain=0x0000 address=0x00000000362fa7b0 flags=0x0070]
[  945.756642] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.1 domain=0x0000 address=0x00000000362fa6c0 flags=0x0070]
[  945.756646] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.1 domain=0x0000 address=0x00000000362fa700 flags=0x0070]
[  950.758359] ata8: hard resetting link
[  950.845372] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.1 domain=0x0000 address=0x0000000036320440 flags=0x0070]
[  950.845381] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.1 domain=0x0000 address=0x0000000036320450 flags=0x0070]
[  951.173633] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.1 domain=0x0000 address=0x0000000036320440 flags=0x0070]
[  951.173642] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.1 domain=0x0000 address=0x0000000036320450 flags=0x0070]
[  951.250667] ata8: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  951.251985] ata8.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x80)
[  951.251993] ata8: limiting SATA link speed to 1.5 Gbps
[  951.252012] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.1 domain=0x0000 address=0x0000000036320420 flags=0x0070]
[  951.252021] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.1 domain=0x0000 address=0x00000000362fa5b0 flags=0x0070]
[  951.252026] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.1 domain=0x0000 address=0x00000000363203e0 flags=0x0070]
[  951.252030] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.1 domain=0x0000 address=0x0000000036320430 flags=0x0070]
[  951.252034] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.1 domain=0x0000 address=0x00000000362fa5c0 flags=0x0070]
[  951.252038] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.1 domain=0x0000 address=0x00000000362fa600 flags=0x0070]
[  951.252042] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.1 domain=0x0000 address=0x00000000362fa640 flags=0x0070]
[  951.252045] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.1 domain=0x0000 address=0x00000000362fa680 flags=0x0070]
[  951.252049] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.1 domain=0x0000 address=0x00000000362fa6c0 flags=0x0070]
[  951.252052] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.1 domain=0x0000 address=0x00000000362fa700 flags=0x0070]
[  951.252056] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.1 domain=0x0000 address=0x00000000362fa740 flags=0x0070]
[  951.252060] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.1 domain=0x0000 address=0x00000000362fa780 flags=0x0070]
[  951.252063] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.1 domain=0x0000 address=0x00000000362fa7a0 flags=0x0070]
[  951.252067] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.1 domain=0x0000 address=0x00000000362fa7b0 flags=0x0070]

```

Ubuntu will not see the drive at all when connected by eSata.

Thanks

---

### Post by Dyson_Shultz on 2014-06-21
I have had a similar problem w/ Nvidia Video Cards with an ECS A990FXM-A v1.1 motherboard and IOMMU settings.  If you are not using virtualization then try adding amd_iommu=off to your boot command line options.  It seems there is a fix in the 3.16 branch of the kernel where iommu=1 iommu=pt worked good for me.

---

### Post by adlin5000 on 2014-06-22
I have to have IOMMU enabled in bios so USB and ethernet work, and use iommu=pt in grub otherwise I get IO_PAGE_FAULT errors constantly, and the error file gets into the Gigs quickly.

---

### Post by Dyson_Shultz on 2014-06-23
I now have "amd_iommu=off iommu=memaper=4" in my grub.conf and now I get 512MB of PCI-DMA instead of SWIOTLB for kernel 3.16-rc2

# dmesg | grep PCI-DMA
[    1.072953] PCI-DMA: Disabling AGP.
[    1.074388] PCI-DMA: aperture base @ 80000000 size 524288 KB
[    1.074389] PCI-DMA: using GART IOMMU.
[    1.074393] PCI-DMA: Reserving 512MB of IOMMU area in the AGP aperture

The test I use is md5sum a video file over nfs and check ifconfig eth0 for frame errors.  With amd_iommu enabled the throuput is lower and I get Ethernet errors.

I get oodles of AMD-Vi page faults on my Nvidia video card too, like every 10 milliseconds but not with the above options on 3.16-rc2.

Error:  kernel: [   55.331381] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0014 address=0x0000000000001000 flags=0x0000]

---

