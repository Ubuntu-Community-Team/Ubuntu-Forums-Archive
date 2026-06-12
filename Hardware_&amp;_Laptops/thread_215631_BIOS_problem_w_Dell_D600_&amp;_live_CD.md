---
title: "BIOS problem w/ Dell D600 &amp; live CD"
date: 2006-07-14
forum: Hardware &amp; Laptops
---

### Post by busgeek on 2006-07-14
I've tried Ubuntu 6.06 on my desktop and I'm happy enough to try it on my laptop too - a Dell Latitude D600.  

But even the Live CD won't work on the laptop...

I adjusted the BIOS to enable boot from CD. (The BIOS said to be careful with the boot-order since it could change the drive letters (huh!?))  I think it started with an order of Floppy/HDD/USB/DVD
So I changed it to Floppy/DVD/HDD/USB (seems like a reasonable order, yes?)  But the Live CD just gets a little beyond the 'Restricted Drivers' section and then throws out a few error messages and stops dead.

Any thoughts?

(I know some of the errors were with the bcm43xx drivers; but surely that shouldn't stop it dead!?)  ](*,)     
I think this D600 has the Intel 1350 MiniPCI card (not the 2100)

I'll post the exact errors up later - I don't have them to hand.


Thanks in advance...

Howard

---

### Post by busgeek on 2006-07-14
Ah, yes, some of the other errors were I/O errors reading /hdc 
(if that helps...)

---

### Post by Hellkeepa on 2006-07-16
HELLo!

Sounds like you got a damaged disk there, or a dodgey CD-ROM reader, since /hdc would be your CD-ROM. Try with another disk, burned at a lower speed. Or if you got it from ShipIt, get a new one.

Happy codin'!

---

### Post by busgeek on 2006-07-17
Ok.  I have got a bit further...  I've managed to get into Ubuntu on the Live CD - but not without problems.  

Here's the dmesg output...  (from where the errors start)

[4294678.917000] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
[4294678.917000] hdc: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
[4294678.917000] ide: failed opcode was: unknown
[4294678.917000] end_request: I/O error, dev hdc, sector 1429192
[4294678.917000] Buffer I/O error on device hdc, logical block 357298
[4294679.980000] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
[4294679.980000] hdc: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
[4294679.980000] ide: failed opcode was: unknown
[4294679.980000] end_request: I/O error, dev hdc, sector 1429192
[4294679.980000] Buffer I/O error on device hdc, logical block 357298
[4294681.044000] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
[4294681.044000] hdc: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
[4294681.044000] ide: failed opcode was: unknown
[4294681.044000] end_request: I/O error, dev hdc, sector 1429192
[4294681.044000] Buffer I/O error on device hdc, logical block 357298
[4294682.107000] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
[4294682.107000] hdc: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
[4294682.107000] ide: failed opcode was: unknown
[4294682.107000] end_request: I/O error, dev hdc, sector 1429192
[4294682.107000] Buffer I/O error on device hdc, logical block 357298
[4294683.171000] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
[4294683.171000] hdc: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
[4294683.171000] ide: failed opcode was: unknown
[4294683.171000] end_request: I/O error, dev hdc, sector 1429192
[4294683.171000] Buffer I/O error on device hdc, logical block 357298
[4294684.234000] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
[4294684.234000] hdc: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
[4294684.234000] ide: failed opcode was: unknown
[4294684.234000] end_request: I/O error, dev hdc, sector 1429192
[4294684.234000] Buffer I/O error on device hdc, logical block 357298
[4294685.455000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294685.455000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[4294685.455000] ide: failed opcode was: unknown
[4294685.455000] end_request: I/O error, dev hdc, sector 1429184
[4294685.455000] Buffer I/O error on device hdc, logical block 357296
[4294686.518000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294686.518000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[4294686.518000] ide: failed opcode was: unknown
[4294686.518000] end_request: I/O error, dev hdc, sector 1429188
[4294686.518000] Buffer I/O error on device hdc, logical block 357297
[4294687.582000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294687.582000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[4294687.582000] ide: failed opcode was: unknown
[4294687.582000] end_request: I/O error, dev hdc, sector 1429184
[4294687.582000] Buffer I/O error on device hdc, logical block 357296
[4294688.645000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294688.645000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[4294688.645000] ide: failed opcode was: unknown
[4294688.645000] end_request: I/O error, dev hdc, sector 1429188
[4294688.645000] Buffer I/O error on device hdc, logical block 357297
[4294689.439000] ISO 9660 Extensions: Microsoft Joliet Level 3
[4294689.533000] ISO 9660 Extensions: RRIP_1991A
[4294689.586000] loop: loaded (max 8 devices)
[4294689.596000] Registering unionfs 1.1.2
[4294689.707000] squashfs: version 3.0prerelease (2006/1/24) Phillip Lougher
[4294828.910000] tg3.c:v3.47 (Dec 28, 2005)
[4294828.910000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4294828.941000] eth0: Tigon3 [partno(BCM95702A20) rev 1002 PHY(5703)] (PCI:33MHz:32-bit) 10/100/1000BaseT Ethernet 00:0d:56:76:1f:74
[4294828.941000] eth0: RXcsums[1] LinkChgREG[1] MIirq[1] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
[4294828.941000] eth0: dma_rwctrl[763f0000]
[4294859.097000] Real Time Clock Driver v1.12
[4294859.290000] input: PC Speaker as /class/input/input1
[4294859.672000] NET: Registered protocol family 17
[4294860.022000] input: DualPoint Stick as /class/input/input2
[4294860.045000] input: AlpsPS/2 ALPS DualPoint TouchPad as /class/input/input3
[4294860.295000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294861.224000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[4294861.224000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[4294861.469000] Linux agpgart interface v0.101 (c) Dave Jones
[4294862.035000] intel8x0_measure_ac97_clock: measured 50422 usecs
[4294862.035000] intel8x0: clocking to 48000
[4294863.383000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294863.400000] ts: Compaq touchscreen protocol output
**[4294863.776000] hw_random: cannot enable RNG, aborting**
[4294863.780000] agpgart: Detected an Intel 855PM Chipset.
[4294863.787000] agpgart: AGP aperture is 128M @ 0xe0000000
[4294866.838000] ieee80211_crypt: registered algorithm 'NULL'
[4294867.013000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[4294867.013000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4294867.851000] bcm43xx driver
[4294867.852000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[4294867.862000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294867.862000] Yenta: CardBus bridge found at 0000:02:01.0 [1028:011d]
[4294867.862000] Yenta O2: res at 0x94/0xD4: 00/ea
[4294867.862000] Yenta O2: enabling read prefetch/write burst
[4294868.050000] Yenta: ISA IRQ mask 0x0438, PCI irq 11
[4294868.050000] Socket status: 30000006
[4294868.050000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[4294868.050000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
[4294868.050000] cs: IO port probe 0xd000-0xefff: clean.
[4294868.051000] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
[4294868.051000] pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x23ffffff
[4294868.057000] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[4294868.062000] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[4294868.064000] ACPI: PCI Interrupt 0000:02:01.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294868.064000] Yenta: CardBus bridge found at 0000:02:01.1 [1028:011d]
[4294868.186000] Yenta: ISA IRQ mask 0x0438, PCI irq 11
[4294868.186000] Socket status: 30000410
[4294868.186000] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[4294868.186000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
[4294868.186000] cs: IO port probe 0xd000-0xefff: clean.
[4294868.187000] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
[4294868.187000] pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x23ffffff
[4294868.848000] pccard: PCMCIA card inserted into slot 1
[4294868.848000] cs: memory probe 0xf6000000-0xfbffffff: excluding 0xf6000000-0xfa1fffff 0xfae00000-0xfb3fffff
[4294868.852000] pcmcia: registering new device pcmcia1.0
[4294869.070000] cs: IO port probe 0x100-0x3af: clean.
[4294869.071000] cs: IO port probe 0x3e0-0x4ff: clean.
[4294869.072000] cs: IO port probe 0x820-0x8ff: clean.
[4294869.072000] cs: IO port probe 0xc00-0xcf7: clean.
[4294869.072000] cs: IO port probe 0xa00-0xaff: clean.
[4294869.074000] cs: IO port probe 0x100-0x3af: clean.
[4294869.075000] cs: IO port probe 0x3e0-0x4ff: clean.
[4294869.076000] cs: IO port probe 0x820-0x8ff: clean.
[4294869.076000] cs: IO port probe 0xc00-0xcf7: clean.
[4294869.076000] cs: IO port probe 0xa00-0xaff: clean.
[4294869.851000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294869.851000] md: bitmap version 4.39
[4294870.654000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]

---

### Post by busgeek on 2006-07-17
This was with another newly-burnt CD.  I did find 1 bad checksum on the first one....

Um. Aaaah - I haven't actually verified this one yet.  (I'll do that tonight - just to check that it's ok...)

---

### Post by busgeek on 2006-07-18
Yup.  The new CD checked out fine.  So what can I do with the dmesg errors outlined above???

---

