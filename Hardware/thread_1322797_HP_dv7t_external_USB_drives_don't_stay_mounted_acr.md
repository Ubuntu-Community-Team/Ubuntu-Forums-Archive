---
title: "HP dv7t: external USB drives don't stay mounted across suspend/resume"
date: 2009-11-11
forum: Hardware
---

### Post by pointym5 on 2009-11-11
I've got an HP dv7t that's been running a 32-bit Ubuntu build since 8.10.  I generally keep a 500GB external (USB2.0) drive mounted at all times.  I almost always suspend the laptop at night and resume in the morning.

Since I've had it, the dv7t has been mostly OK with suspend/resume. I understand that the dv5t laptops of its similar generation have BIOS problems that keep suspend/resume from working, but this one has been OK.  OK, that is, until I installed 9.10.  Now, while in a couple of ways (sound, mostly, though sound has its own new problems) resuming from sleep has gotten a little better, with the external USB drive it's gotten worse. Basically, the USB drive never works after resume. The drive has to be power-cycled for the system to even notice it again - that is, unplugging and replugging it has no effect, and there's nothing in /var/log/messages to indicate when I do that that the system has detected it as a mass storage device.

According to the mount table, the disk remains mounted (which isn't surprising), but any attempt to access it gets an "I/O error".  I don't see errors in the log upon failed accesses, and I'm not sure how to interpret what's there in general from the process of resuming after sleep.

Note that I'm talking about suspend to RAM, not "hibernate" (which is slower than shutdown/reboot on this laptop and therefore pretty useless).

---

### Post by Joe Ker1086 on 2009-11-11
Try this. Create a folder in media


```
mkdir /media/usb_drive
```

Add this line in /etc/fstab file :


```
/media/disk   /media/usb_drive  vfat   noatime  0 0
```

WHERE IT SAYS DISK ENTER THE LOCATION OF YOUR DRIVE ie /media/sda1

---

### Post by pointym5 on 2009-11-11
Thank you for your reply. I've already got that all set up. I have no problem mounting the drive. In fact I've got udev rules to recognize it.  There's no problem mounting the drive.

The problem is this:

[list=1][*]System is up. Drive is mounted. Life is good.[*]I suspend the system from the xfce menu (I'm running Ubuntu, but on top of that I've installed and am running xfce - it's been that way for months and was fine in 9.04)[*]A few hours later I resume the system by touching a key, and it (mostly) comes back to life[/list]

At this point, any attempt to access the drive via its mount point gets an I/O error. If I switch the drive off and then turn it back on, the system recognizes it (and my udev rules work fine). I can then mount the drive again via my /etc/fstab entry.

---

### Post by Joe Ker1086 on 2009-11-11
sorry then, i thought that would permanantly mount it....maybe its a bug with 9.10 running xfce...thats all i got tho :(

---

### Post by pointym5 on 2009-11-11
Here's what's in /var/log/messages, for what it's worth. I don't know why it starts off with messages that look like they'd be about suspending the system; 7:23 AM was when I resumed it.
```

Nov 11 07:23:54 patience kernel: [529873.301429] PM: Syncing filesystems ... done.
Nov 11 07:23:54 patience kernel: [529873.306499] Freezing user space processes ... (elapsed 0.00 seconds) done.
Nov 11 07:23:54 patience kernel: [529873.307366] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Nov 11 07:23:54 patience kernel: [529873.307457] Suspending console(s) (use no_console_suspend to debug)
Nov 11 07:23:54 patience kernel: [529873.440055] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Nov 11 07:23:54 patience kernel: [529873.554159] sd 0:0:0:0: [sda] Stopping disk
Nov 11 07:23:54 patience kernel: [529874.553329] jmb38x_ms 0000:06:00.3: PME# disabled
Nov 11 07:23:54 patience kernel: [529874.553338] jmb38x_ms 0000:06:00.3: PCI INT A disabled
Nov 11 07:23:54 patience kernel: [529874.568222] sdhci-pci 0000:06:00.1: PME# disabled
Nov 11 07:23:54 patience kernel: [529874.568229] sdhci-pci 0000:06:00.1: PCI INT A disabled
Nov 11 07:23:54 patience kernel: [529874.752117] ehci_hcd 0000:00:1d.7: PCI INT A disabled
Nov 11 07:23:54 patience kernel: [529874.752131] uhci_hcd 0000:00:1d.3: PCI INT D disabled
Nov 11 07:23:54 patience kernel: [529874.752141] uhci_hcd 0000:00:1d.2: PCI INT C disabled
Nov 11 07:23:54 patience kernel: [529874.752151] uhci_hcd 0000:00:1d.1: PCI INT B disabled
Nov 11 07:23:54 patience kernel: [529874.752160] uhci_hcd 0000:00:1d.0: PCI INT A disabled
Nov 11 07:23:54 patience kernel: [529874.856397] HDA Intel 0000:00:1b.0: PCI INT B disabled
Nov 11 07:23:54 patience kernel: [529874.872220] HDA Intel 0000:00:1b.0: power state changed by ACPI to D3
Nov 11 07:23:54 patience kernel: [529874.872230] ehci_hcd 0000:00:1a.7: PCI INT C disabled
Nov 11 07:23:54 patience kernel: [529874.872237] uhci_hcd 0000:00:1a.1: PCI INT B disabled
Nov 11 07:23:54 patience kernel: [529874.872245] uhci_hcd 0000:00:1a.0: PCI INT A disabled
Nov 11 07:23:54 patience kernel: [529874.872888] PM: suspend devices took 1.568 seconds
Nov 11 07:23:54 patience kernel: [529874.873347] r8169 0000:05:00.0: PME# enabled
Nov 11 07:23:54 patience kernel: [529874.894910] r8169 0000:05:00.0: wake-up capability enabled by ACPI
Nov 11 07:23:54 patience kernel: [529874.908253] ehci_hcd 0000:00:1d.7: PME# disabled
Nov 11 07:23:54 patience kernel: [529874.924512] ehci_hcd 0000:00:1a.7: PME# disabled
Nov 11 07:23:54 patience kernel: [529874.940386] ACPI: Preparing to enter system sleep state S3
Nov 11 07:23:54 patience kernel: [529874.940676] Disabling non-boot CPUs ...
Nov 11 07:23:54 patience kernel: [529875.044013] CPU 1 is now offline
Nov 11 07:23:54 patience kernel: [529875.044016] SMP alternatives: switching to UP code
Nov 11 07:23:54 patience kernel: [529875.051660] CPU1 is down
Nov 11 07:23:54 patience kernel: [529875.051667] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Nov 11 07:23:54 patience kernel: [529875.051667] Enabling non-boot CPUs ...
Nov 11 07:23:54 patience kernel: [529875.051667] SMP alternatives: switching to SMP code
Nov 11 07:23:54 patience kernel: [529875.059108] Booting processor 1 APIC 0x1 ip 0x6000
Nov 11 07:23:54 patience kernel: [529875.051321] Initializing CPU#1
Nov 11 07:23:54 patience kernel: [529875.051321] Calibrating delay using timer specific routine.. 4392.61 BogoMIPS (lpj=8785228)
Nov 11 07:23:54 patience kernel: [529875.051321] CPU: L1 I cache: 32K, L1 D cache: 32K
Nov 11 07:23:54 patience kernel: [529875.051321] CPU: L2 cache: 2048K
Nov 11 07:23:54 patience kernel: [529875.051321] CPU: Physical Processor ID: 0
Nov 11 07:23:54 patience kernel: [529875.051321] CPU: Processor Core ID: 1
Nov 11 07:23:54 patience kernel: [529875.051321] mce: CPU supports 6 MCE banks
Nov 11 07:23:54 patience kernel: [529875.051321] CPU1: Thermal monitoring enabled (TM1)
Nov 11 07:23:54 patience kernel: [529875.051321] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
Nov 11 07:23:54 patience kernel: [529875.154825] CPU1: Intel(R) Core(TM)2 Duo CPU     T6600  @ 2.20GHz stepping 0a
Nov 11 07:23:54 patience kernel: [529875.168516] CPU1 is up
Nov 11 07:23:54 patience kernel: [529875.168519] ACPI: Waking up from system sleep state S3
Nov 11 07:23:54 patience kernel: [529875.217727] ehci_hcd 0000:00:1a.7: PME# disabled
Nov 11 07:23:54 patience kernel: [529875.218428] ehci_hcd 0000:00:1d.7: PME# disabled
Nov 11 07:23:54 patience kernel: [529875.275109] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 11 07:23:54 patience kernel: [529875.275139] usb usb3: root hub lost power or was reset
Nov 11 07:23:54 patience kernel: [529875.275160] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Nov 11 07:23:54 patience kernel: [529875.275189] usb usb4: root hub lost power or was reset
Nov 11 07:23:54 patience kernel: [529875.275209] ehci_hcd 0000:00:1a.7: PME# disabled
Nov 11 07:23:54 patience kernel: [529875.275213] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov 11 07:23:54 patience kernel: [529875.275230] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 22 (level, low) -> IRQ 22
Nov 11 07:23:54 patience kernel: [529875.275264] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Nov 11 07:23:54 patience kernel: [529875.275294] usb usb5: root hub lost power or was reset
Nov 11 07:23:54 patience kernel: [529875.275323] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
Nov 11 07:23:54 patience kernel: [529875.275352] usb usb6: root hub lost power or was reset
Nov 11 07:23:54 patience kernel: [529875.275370] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov 11 07:23:54 patience kernel: [529875.275400] usb usb7: root hub lost power or was reset
Nov 11 07:23:54 patience kernel: [529875.275418] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Nov 11 07:23:54 patience kernel: [529875.275447] usb usb8: root hub lost power or was reset
Nov 11 07:23:54 patience kernel: [529875.275466] ehci_hcd 0000:00:1d.7: PME# disabled
Nov 11 07:23:54 patience kernel: [529875.275470] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Nov 11 07:23:54 patience kernel: [529876.127261] r8169 0000:05:00.0: wake-up capability disabled by ACPI
Nov 11 07:23:54 patience kernel: [529876.127277] r8169 0000:05:00.0: PME# disabled
Nov 11 07:23:54 patience kernel: [529876.143380] r8169: eth0: link up
Nov 11 07:23:54 patience kernel: [529876.185137] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[da000000-da0007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Nov 11 07:23:54 patience kernel: [529876.192249] sdhci-pci 0000:06:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 11 07:23:54 patience kernel: [529876.192284] pci 0000:06:00.2: PME# disabled
Nov 11 07:23:54 patience kernel: [529876.192290] jmb38x_ms 0000:06:00.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 11 07:23:54 patience kernel: [529876.192313] pci 0000:06:00.4: PME# disabled
Nov 11 07:23:54 patience kernel: [529876.236623] ata2: SATA link down (SStatus 4 SControl 300)
Nov 11 07:23:54 patience kernel: [529876.236650] ata6: SATA link down (SStatus 0 SControl 300)
Nov 11 07:23:54 patience kernel: [529876.731023] sd 0:0:0:0: [sda] Starting disk
Nov 11 07:23:54 patience kernel: [529876.804097] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov 11 07:23:54 patience kernel: [529876.808896] ata5.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
Nov 11 07:23:54 patience kernel: [529876.809352] ata5.00: ACPI cmd ef/10:01:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
Nov 11 07:23:54 patience kernel: [529876.809813] ata5.00: ACPI cmd ef/10:02:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
Nov 11 07:23:54 patience kernel: [529876.809819] ata5.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
Nov 11 07:23:54 patience kernel: [529876.810279] ata5.00: ACPI cmd ef/10:04:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
Nov 11 07:23:54 patience kernel: [529876.810741] ata5.00: ACPI cmd ef/10:05:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
Nov 11 07:23:54 patience kernel: [529876.816072] ata5.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
Nov 11 07:23:54 patience kernel: [529876.816529] ata5.00: ACPI cmd ef/10:01:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
Nov 11 07:23:54 patience kernel: [529876.816989] ata5.00: ACPI cmd ef/10:02:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
Nov 11 07:23:54 patience kernel: [529876.816994] ata5.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
Nov 11 07:23:54 patience kernel: [529876.817455] ata5.00: ACPI cmd ef/10:04:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
Nov 11 07:23:54 patience kernel: [529876.817917] ata5.00: ACPI cmd ef/10:05:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
Nov 11 07:23:54 patience kernel: [529876.817961] ata5.00: configured for UDMA/100
Nov 11 07:23:54 patience kernel: [529878.124061] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 11 07:23:54 patience kernel: [529878.125714] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
Nov 11 07:23:54 patience kernel: [529878.130419] ata1.00: ACPI cmd ef/10:01:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
Nov 11 07:23:54 patience kernel: [529878.130761] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
Nov 11 07:23:54 patience kernel: [529878.131068] ata1.00: ACPI cmd ef/10:04:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
Nov 11 07:23:54 patience kernel: [529878.131416] ata1.00: ACPI cmd ef/10:05:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
Nov 11 07:23:54 patience kernel: [529878.134598] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
Nov 11 07:23:54 patience kernel: [529878.134958] ata1.00: ACPI cmd ef/10:01:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
Nov 11 07:23:54 patience kernel: [529878.134963] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
Nov 11 07:23:54 patience kernel: [529878.135323] ata1.00: ACPI cmd ef/10:04:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
Nov 11 07:23:54 patience kernel: [529878.135670] ata1.00: ACPI cmd ef/10:05:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
Nov 11 07:23:54 patience kernel: [529878.135714] ata1.00: configured for UDMA/100
Nov 11 07:23:54 patience kernel: [529878.272057] usb 2-5: reset high speed USB device using ehci_hcd and address 4
Nov 11 07:23:54 patience kernel: [529878.540050] usb 2-7: reset high speed USB device using ehci_hcd and address 5
Nov 11 07:23:54 patience kernel: [529878.992049] usb 5-2: reset full speed USB device using uhci_hcd and address 2
Nov 11 07:23:54 patience kernel: [529879.176520] Registered led device: iwl-phy0::radio
Nov 11 07:23:54 patience kernel: [529879.176549] Registered led device: iwl-phy0::assoc
Nov 11 07:23:54 patience kernel: [529879.176575] Registered led device: iwl-phy0::RX
Nov 11 07:23:54 patience kernel: [529879.176602] Registered led device: iwl-phy0::TX
Nov 11 07:23:54 patience kernel: [529879.260350] usb 2-7.1: reset full speed USB device using ehci_hcd and address 20
Nov 11 07:23:54 patience kernel: [529879.424344] usb 2-7.4: reset full speed USB device using ehci_hcd and address 24
Nov 11 07:23:54 patience kernel: [529879.520716] snd-usb-audio 2-7.4:1.0: no reset_resume for driver snd-usb-audio?
Nov 11 07:23:54 patience kernel: [529879.520720] snd-usb-audio 2-7.4:1.1: no reset_resume for driver snd-usb-audio?
Nov 11 07:23:54 patience kernel: [529879.520724] snd-usb-audio 2-7.4:1.2: no reset_resume for driver snd-usb-audio?
Nov 11 07:23:54 patience kernel: [529879.563132] PM: resume devices took 4.344 seconds
Nov 11 07:23:54 patience kernel: [529879.563170] Restarting tasks ... done.
Nov 11 07:23:54 patience kernel: [529879.563751] usb 2-3: USB disconnect, address 29
Nov 11 07:23:57 patience kernel: [529882.804600] Registered led device: iwl-phy0::radio
Nov 11 07:23:57 patience kernel: [529882.804621] Registered led device: iwl-phy0::assoc
Nov 11 07:23:57 patience kernel: [529882.804639] Registered led device: iwl-phy0::RX
Nov 11 07:23:57 patience kernel: [529882.804655] Registered led device: iwl-phy0::TX
Nov 11 07:23:57 patience kernel: [529882.840301] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov 11 07:23:57 patience kernel: [529883.304243] r8169: eth0: link up

```

---

