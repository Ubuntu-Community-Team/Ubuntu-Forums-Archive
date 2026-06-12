---
title: "SD Card not being detected HP x360 Laptop"
date: 2015-02-21
forum: Hardware
---

### Post by asigachev on 2015-02-21
Hello everyone!

After some updates my laptop stopped to detect SD Card on built-int card-reader

The card reader is being detected by the system:

```
    description: Notebook
    product: HP Pavilion 11 x360 PC (F4J20LA#AC4)
------------
         *-pci:2
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:5000(size=4096) memory:90600000-906fffff
           *-generic UNCLAIMED
                description: Unassigned class
                product: RTS5227 PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress cap_list
                configuration: latency=0
                resources: memory:90600000-90600fff
```

But I don´t see the card (it´s 16GB Transcend):
```
Disk /dev/sda: 465,8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 9970C3AC-279D-4636-A0CA-63320318D520

Device         Start       End   Sectors   Size Type
/dev/sda1       2048    821247    819200   400M Windows recovery environment
/dev/sda2     821248   1353727    532480   260M EFI System
/dev/sda3    1353728   1615871    262144   128M Microsoft reserved
/dev/sda4    1615872 294584621 292968750 139,7G Microsoft basic data
/dev/sda5  943431680 976762879  33331200  15,9G Microsoft basic data
/dev/sda6  294586368 392240664  97654297  46,6G Linux filesystem
/dev/sda7  392241152 587552767 195311616  93,1G Linux filesystem
/dev/sda8  587552768 603176959  15624192   7,5G Linux swap
/dev/sda9  603176960 603762687    585728   286M Linux filesystem
/dev/sda10 603762688 943431679 339668992   162G Linux filesystem

Partition table entries are not in disk order.
Disk /dev/mapper/cryptswap1: 7,5 GiB, 7997489152 bytes, 15620096 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

```

Any ideas on troubleshooting?

---

### Post by weatherman2 on 2015-02-21
Can you try an older kernel? (should find the previous one on the Grub boot menu unless you cleaned out the old kernels.)  If an older kernel works but the new one doesn't, that should send you in one direction.  If you can't get the card to work even in an older kernel (where it used to work), that's something else.

Do you have other cards besides this one SD card?  What format is this card?  exFat cards may not work by default.  I have never gotten my exFat carmera card to work in Ubuntu on my laptop (works fine in Windows 8.1 on same hardware; works fine in Ubuntu in a USB card reader; FAT cards work fine in the internal card reader in Ubuntu but not exFat which unfortunately my camera uses).

You seem to have Windows 8.1 - is the card detected/read there?

---

### Post by the-tech-kid on 2015-02-22
Try a USB card reader.

---

