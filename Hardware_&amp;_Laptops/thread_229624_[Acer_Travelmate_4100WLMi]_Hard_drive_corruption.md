---
title: "[Acer Travelmate 4100WLMi] Hard drive corruption"
date: 2006-08-04
forum: Hardware &amp; Laptops
---

### Post by dangerjunkie2002 on 2006-08-04
Hi,

I have an Acer Travelmate 4100WLMi (1.5GHz Pen-M, 80201 (ICH6) chipset, i915GM graphics, 1.25GB, 80GB, ProWireless 2200BG) It previously ran Breezy with no great dramas. Since doing a clean install of Dapper on my spare HD (dual boot XPH) I have had the hard drive corrupted twice in a week. The symptom is that the machine will not boot (black screen with cursor instead of the usual GRUB starting message) but the drives (ext3) seem intact when mounted with a rescue disc. My guess is that the MBR is getting corrupted.

I did a full test with the DFT test program (the drive is a Travelstar) and it gives the drive a clean bill of health. I've reinstalled and am just downloading 400mb of updates over satellite (yawn)

I'm not sure whether it is GRUB or the MBR that got wasted. I am assuming it is the MBR as /boot appeared to be intact. The first time it went I was writing a DVD with nautilus and the second I was configuring Wine to use the DVD drive (do I see a pattern forming here?) The HD is hda and the DVD is hdb. It's a laptop so I can't change the wiring. I'm starting to wonder if I have a kernel or a driver fault.

The IDE says it is "80201FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller". There is one funny at boot time. Before logging starts there are about half a dozen complaint lines which say something like "cannot allocate resource region 9 of bridge xxxxxxxxxx" There are also occasional "ipw2200: firmware error detected. restarting" messages but I got those in Breezy and it didn't do this.


Here are all the lines from messages I am curious about:

Aug 4 18:14:36 localhost kernel: No module symbols loaded - kernel modules not enabled.
[SNIP]
Aug 4 18:14:36 localhost kernel: [4294670.072000] ACPI: Looking for DSDT ... not found!
[SNIP]
Aug 4 18:14:36 localhost kernel: [4294670.239000] pnp: PnP ACPI init
Aug 4 18:14:36 localhost kernel: [4294670.239000] pnp: PnPACPI: unknown resource type 7
Aug 4 18:14:36 localhost kernel: [4294670.239000] pnp: PnPACPI: METHOD_NAME__CRS failure for PNP0c02
Aug 4 18:14:36 localhost kernel: [4294670.239000] pnp: PnPACPI: unknown resource type 7
Aug 4 18:14:36 localhost kernel: [4294670.239000] pnp: PnPACPI: METHOD_NAME__CRS failure for PNP0200
Aug 4 18:14:36 localhost kernel: [4294670.239000] pnp: PnPACPI: unknown resource type 7
Aug 4 18:14:36 localhost kernel: [4294670.239000] pnp: PnPACPI: METHOD_NAME__CRS failure for PNP0c04
Aug 4 18:14:36 localhost kernel: [4294670.239000] pnp: PnPACPI: unknown resource type 7
Aug 4 18:14:36 localhost kernel: [4294670.239000] pnp: PnPACPI: METHOD_NAME__CRS failure for PNP0c02
Aug 4 18:14:36 localhost kernel: [4294670.239000] pnp: PnPACPI: unknown resource type 7
Aug 4 18:14:36 localhost kernel: [4294670.239000] pnp: PnPACPI: METHOD_NAME__CRS failure for PNP0b00
Aug 4 18:14:36 localhost kernel: [4294670.240000] pnp: PnPACPI: unknown resource type 7
Aug 4 18:14:36 localhost kernel: [4294670.240000] pnp: PnPACPI: METHOD_NAME__CRS failure for NSC6001
Aug 4 18:14:36 localhost kernel: [4294670.241000] pnp: PnPACPI: unknown resource type 7
Aug 4 18:14:36 localhost kernel: [4294670.241000] pnp: PnPACPI: METHOD_NAME__CRS failure for PNP0303
Aug 4 18:14:36 localhost kernel: [4294670.241000] pnp: PnPACPI: unknown resource type 7
Aug 4 18:14:36 localhost kernel: [4294670.241000] pnp: PnPACPI: METHOD_NAME__CRS failure for SYN1003
Aug 4 18:14:36 localhost kernel: [4294670.241000] pnp: PnP ACPI: found 1 devices
Aug 4 18:14:36 localhost kernel: [4294670.241000] PnPBIOS: Disabled by ACPI PNP
Aug 4 18:14:36 localhost kernel: [4294670.241000] PCI: Using ACPI for IRQ routing
Aug 4 18:14:36 localhost kernel: [4294670.241000] PCI: If a device doesn't work, try "pci=routeirq". If it helps, post a report
[SNIP]
Aug 4 18:14:36 localhost kernel: [4294670.690000] **** SET: Misaligned resource pointer: df878e02 Type 07 Len 0
[SNIP]
Aug 4 18:14:36 localhost kernel: [4294674.227000] **** SET: Misaligned resource pointer: df89b302 Type 07 Len 0
[SNIP]
Aug 4 18:14:36 localhost kernel: [4294674.329000] **** SET: Misaligned resource pointer: dfab9ec2 Type 07 Len 0
[SNIP]
Aug 4 18:14:36 localhost kernel: [4294690.553000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
Aug 4 18:14:36 localhost kernel: [4294691.190000] cdrom: open failed.
[SNIP]
Aug 4 18:14:46 localhost kernel: [4294705.503000] hdb: drive_cmd: status=0x01 {Error }
Aug 4 18:14:46 localhost kernel: [4294705.503000] hdb: drive_cmd: error=0x04 {AbortedCommand }
Aug 4 18:14:46 localhost kernel: [4294705.503000] ide: failed opcode was: 0xec
Aug 4 18:14:46 localhost kernel: [4294705.928000] hdb: drive_cmd: status=0x01 {Error }
Aug 4 18:14:46 localhost kernel: [4294705.928000] hdb: drive_cmd: error=0x04 {AbortedCommand }
Aug 4 18:14:46 localhost kernel: [4294705.928000] ide: failed opcode was: 0xec
[SNIP]

Since hdb is the DVD+-RW I wonder if this is indicative of some deep problem.

Any help will be very much appreciated.

Thanks,
Paul

---

