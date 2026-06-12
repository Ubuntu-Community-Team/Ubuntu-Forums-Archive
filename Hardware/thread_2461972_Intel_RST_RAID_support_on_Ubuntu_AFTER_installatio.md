---
title: "Intel RST RAID support on Ubuntu AFTER installation"
date: 2021-05-11
forum: Hardware
---

### Post by link-dam on 2021-05-11
My goal is to create RAID 0 disk - unfortunately mdadm is not meeting performance expectations, and as far I understand I cannot create AHCI RAID with m.2 NVME disks. Hence, Intel RST is the last option


Google is flooded with guides about how to disable RST to enable ubuntu installation, but what about support AFTER installation? My RST drive is fully visible and operational in Windows, but undetected by Ubuntu Disk Manager. However, it appears in lshw:

```
    *-raid
             description: RAID bus controller
             product: SATA Controller [RAID mode]
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: raid msix pm bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:16 memory:694b0000-694b7fff memory:694c3000-694c30ff ioport:3090(size=8) ioport:3080(size=4) ioport:3060(size=32) memory:69400000-6947ffff
        *-pci:0
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:122
        *-pci:1
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:123 memory:69100000-693fffff

```


Is there any option to enable this disk?

---

### Post by Doug S on 2021-05-11
did you see [this]("https://help.ubuntu.com/rst/")? I don't know if helps with your issue or not.

---

### Post by link-dam on 2021-05-11
Unfortunately yes, it only explains how to Install ubuntu and repair Windows, 0 information how to use RST after installation.

---

### Post by rbmorse on 2021-05-12
IRST requires a kernel driver, but Intel has yet to make the code available under a Linux compatible license. Ball is in their court.

---

### Post by oldfred on 2021-05-12
Why RAID 0 with NVMe?

Typically RAID 0 is not recommended.
It was used with slow HDD, for compiling large applications or uses where data is stored on servers, so loss of install not a big issue when one drive fails.
Depending on motherboard & NVMe drives, you may be limited on bandwidth.

Have you updated UEFI and SSD firmware to latest available?

Where did you see you had to use Intel RAID with NVMe drives?
Most of the info from Intel is for Server motherboards as that is where RAID is more common.

Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[https://ubuntuforums.org/showthread.php?t=2444499](https://ubuntuforums.org/showthread.php?t=2444499)
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)
SSD better than RAID 0
[https://ubuntuforums.org/showthread.php?t=2435221](https://ubuntuforums.org/showthread.php?t=2435221)

---

