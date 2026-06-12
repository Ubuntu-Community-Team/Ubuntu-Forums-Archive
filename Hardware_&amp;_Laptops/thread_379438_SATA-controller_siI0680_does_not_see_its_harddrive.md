---
title: "SATA-controller siI0680 does not see its harddrives"
date: 2007-03-08
forum: Hardware &amp; Laptops
---

### Post by gruadp on 2007-03-08
Ubuntu 6.06


I just bought a SATA-card with a sil0680-chip, which offers some RAID-mode too. 
The card has two sata-plugs and on each there is a 300GB-disk. In the Bios both cards are detected and I set them as "passthrouh" in the cards bios, cause I dont need any Raid but just want to use the card as controller.

The Linux-Kernel seems to know about the card, cause when I boot

[17179582.332000] SiI680: IDE controller at PCI slot 0000:00:0f.0
[17179582.332000] **** SET: Misaligned resource pointer: d7de84e2 Type 07 Len 0
[17179582.332000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[17179582.332000] PCI: setting IRQ 11 as level-triggered
[17179582.332000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179582.332000] SiI680: chipset revision 2
[17179582.332000] SiI680: BASE CLOCK == 133
[17179582.332000] SiI680: 100% native mode on irq 11
[17179582.332000] ide2: MMIO-DMA , BIOS settings: hde:pio, hdf:pio
[17179582.332000] ide3: MMIO-DMA , BIOS settings: hdg:pio, hdh:pio
[17179582.332000] Probing IDE interface ide2...
[17179582.900000] Probing IDE interface ide3...

But none of the two disks is recognized.
in /proc/ide I just find my find my "normal" IDE-Disks that are connected to the onboard-channels ide0 and ide1. No trace of the new ide2 and ide3.

I would have expected the new disks to appear as scsi-devides, but there is also no sign of them in  /proc/scsi.

# lspci
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02)
0000:00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:09.0 0106: Initio Corporation: Unknown device 1622 (rev 02)
0000:00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:0f.0 RAID bus controller: Silicon Image, Inc. PCI0680 Ultra ATA-133 Host Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage XL AGP 2X (rev 27)


The cards appears two times. One time as raid controller and one time as  "Unknown device 1622".

I found the  modul sata_sil and loaded it but nothing happens. Only the additional modul libata is loaded.

any idea?
thnx
peter

---

