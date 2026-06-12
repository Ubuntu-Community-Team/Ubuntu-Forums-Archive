---
title: "Asus UX32LN: Waking up from the hibernation mode"
date: 2015-03-06
forum: Hardware
---

### Post by RockTeam on 2015-03-06
[CENTER]**Help needed with Asus UX32LN: a problem with waking up from the hibernation mode – works from the second attempt**
[/CENTER]
  
On the Asus UX32LN with the installed Xubuntu 14.04 with kernel 3.13 I’ve got the following problem. If laptop goes into hibernation mode then when it needs to be waked up again it’s resuming and the battery indicator shows 0%. After that the laptop goes into hibernation again due to xfce4 power management settings. After the second attempt – resuming from the hibernation mode the battery indicator will be get updated to show the correct value in a 30 seconds approximately.
 
This problem will never occur if the laptop is running on the power supply instead of the battery. With the connected power supply it always wakes up correctly on the first try. Do you have any ideas what could be checked to fix this problem?
 
Below you may see the kernel log file where it is seen that at 9:50:15 laptop turns off after the first "failed" attempt to wake up from the sleep mode. And it works fine - after the second attempt.
 
```

Feb 28 09:50:11 asus kernel: [ 9888.514372] PM: Syncing filesystems ... done.
Feb 28 09:50:11 asus kernel: [ 9888.560497] Freezing user space processes ... (elapsed 0.002 seconds) done.
Feb 28 09:50:11 asus kernel: [ 9888.563301] PM: Marking nosave pages: [mem 0x00058000-0x00058fff]
Feb 28 09:50:11 asus kernel: [ 9888.563308] PM: Marking nosave pages: [mem 0x0009e000-0x000fffff]
Feb 28 09:50:11 asus kernel: [ 9888.563315] PM: Marking nosave pages: [mem 0xb95b9000-0xb95b9fff]
Feb 28 09:50:11 asus kernel: [ 9888.563319] PM: Marking nosave pages: [mem 0xb95c1000-0xb95c1fff]
Feb 28 09:50:11 asus kernel: [ 9888.563322] PM: Marking nosave pages: [mem 0xb98d4000-0xb98dafff]
Feb 28 09:50:11 asus kernel: [ 9888.563325] PM: Marking nosave pages: [mem 0xba14c000-0xba3cffff]
Feb 28 09:50:11 asus kernel: [ 9888.563353] PM: Marking nosave pages: [mem 0xc98e3000-0xc9ae8fff]
Feb 28 09:50:11 asus kernel: [ 9888.563378] PM: Marking nosave pages: [mem 0xc9e0f000-0xcaffefff]
Feb 28 09:50:11 asus kernel: [ 9888.563561] PM: Marking nosave pages: [mem 0xcb000000-0xffffffff]
Feb 28 09:50:11 asus kernel: [ 9888.565381] PM: Basic memory bitmaps created
Feb 28 09:50:11 asus kernel: [ 9888.566792] PM: Preallocating image memory... done (allocated 1229565 pages)
Feb 28 09:50:11 asus kernel: [ 9889.934494] PM: Allocated 4918260 kbytes in 1.36 seconds (3616.36 MB/s)
Feb 28 09:50:11 asus kernel: [ 9889.934499] Freezing remaining freezable tasks ... (elapsed 2.127 seconds) done.
Feb 28 09:50:11 asus kernel: [ 9892.063308] Suspending console(s) (use no_console_suspend to debug)
Feb 28 09:50:11 asus kernel: [ 9892.063407] wlan0: deauthenticating from 00:19:7b:a4:f6:15 by local choice (reason=3)
Feb 28 09:50:11 asus kernel: [ 9892.097835] cfg80211: Calling CRDA to update world regulatory domain
Feb 28 09:50:11 asus kernel: [ 9892.098659] mei_me 0000:00:16.0: H_RDY is not cleared 0x801A1A18
Feb 28 09:50:11 asus kernel: [ 9893.395887] PM: freeze of devices complete after 1331.747 msecs
Feb 28 09:50:11 asus kernel: [ 9893.396286] PM: late freeze of devices complete after 0.394 msecs
Feb 28 09:50:11 asus kernel: [ 9893.397345] PM: noirq freeze of devices complete after 1.055 msecs
Feb 28 09:50:11 asus kernel: [ 9893.398326] ACPI: Preparing to enter system sleep state S4
Feb 28 09:50:11 asus kernel: [ 9893.403941] PM: Saving platform NVS memory
Feb 28 09:50:11 asus kernel: [ 9893.432857] Disabling non-boot CPUs ...
Feb 28 09:50:11 asus kernel: [ 9893.536336] smpboot: CPU 1 is now offline
Feb 28 09:50:11 asus kernel: [ 9893.640393] smpboot: CPU 2 is now offline
Feb 28 09:50:11 asus kernel: [ 9893.641169] Broke affinity for irq 60
Feb 28 09:50:11 asus kernel: [ 9893.744457] smpboot: CPU 3 is now offline
Feb 28 09:50:11 asus kernel: [ 9893.745163] PM: Creating hibernation image:
Feb 28 09:50:11 asus kernel: [ 9894.022493] PM: Need to copy 802047 pages
Feb 28 09:50:11 asus kernel: [ 9894.022498] PM: Normal pages needed: 802047 + 1024, available pages: 1265028
Feb 28 09:50:11 asus kernel: [ 9893.747945] PM: Restoring platform NVS memory
Feb 28 09:50:11 asus kernel: [ 9893.752743] Enabling non-boot CPUs ...
Feb 28 09:50:11 asus kernel: [ 9893.752808] x86: Booting SMP configuration:
Feb 28 09:50:11 asus kernel: [ 9893.752810] smpboot: Booting Node 0 Processor 1 APIC 0x2
Feb 28 09:50:11 asus kernel: [ 9893.768666] CPU1 is up
Feb 28 09:50:11 asus kernel: [ 9893.768706] smpboot: Booting Node 0 Processor 2 APIC 0x1
Feb 28 09:50:11 asus kernel: [ 9893.785195] CPU2 is up
Feb 28 09:50:11 asus kernel: [ 9893.785230] smpboot: Booting Node 0 Processor 3 APIC 0x3
Feb 28 09:50:11 asus kernel: [ 9893.801276] CPU3 is up
Feb 28 09:50:11 asus kernel: [ 9893.821194] ACPI: Waking up from system sleep state S4
Feb 28 09:50:11 asus kernel: [ 9893.860836] PM: noirq restore of devices complete after 32.034 msecs
Feb 28 09:50:11 asus kernel: [ 9893.861130] PM: early restore of devices complete after 0.256 msecs
Feb 28 09:50:11 asus kernel: [ 9894.203943] usb usb1: root hub lost power or was reset
Feb 28 09:50:11 asus kernel: [ 9894.203947] usb usb2: root hub lost power or was reset
Feb 28 09:50:11 asus kernel: [ 9894.204197] snd_hda_intel 0000:00:03.0: irq 59 for MSI/MSI-X
Feb 28 09:50:11 asus kernel: [ 9894.204219] xhci_hcd 0000:00:14.0: irq 61 for MSI/MSI-X
Feb 28 09:50:11 asus kernel: [ 9894.204347] mei_me 0000:00:16.0: irq 63 for MSI/MSI-X
Feb 28 09:50:11 asus kernel: [ 9894.204501] ath: phy0: ASPM enabled: 0x42
Feb 28 09:50:11 asus kernel: [ 9894.205618] snd_hda_intel 0000:00:1b.0: irq 64 for MSI/MSI-X
Feb 28 09:50:11 asus kernel: [ 9894.528647] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Feb 28 09:50:11 asus kernel: [ 9894.530485] ata1.00: configured for UDMA/133
Feb 28 09:50:11 asus kernel: [ 9894.536686] usb 1-5: reset high-speed USB device number 3 using xhci_hcd
Feb 28 09:50:11 asus kernel: [ 9894.544699] sd 0:0:0:0: [sda] Starting disk
Feb 28 09:50:11 asus kernel: [ 9894.602613] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88021f792f40
Feb 28 09:50:11 asus kernel: [ 9894.720884] usb 1-4: reset full-speed USB device number 7 using xhci_hcd
Feb 28 09:50:11 asus kernel: [ 9894.737729] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88020928dd80
Feb 28 09:50:11 asus kernel: [ 9894.737733] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88020928de00
Feb 28 09:50:11 asus kernel: [ 9894.737735] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88020928ddc0
Feb 28 09:50:11 asus kernel: [ 9894.737738] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800a617c840
Feb 28 09:50:11 asus kernel: [ 9894.737740] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800a617c800
Feb 28 09:50:11 asus kernel: [ 9896.025622] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
Feb 28 09:50:11 asus kernel: [ 9896.184085] PM: restore of devices complete after 1979.083 msecs
Feb 28 09:50:11 asus kernel: [ 9896.184509] PM: Image restored successfully.
Feb 28 09:50:11 asus kernel: [ 9896.184572] PM: Basic memory bitmaps freed
Feb 28 09:50:11 asus kernel: [ 9896.184576] Restarting tasks ... done.
Feb 28 09:50:11 asus kernel: [ 9896.245044] video LNXVIDEO:00: Restoring backlight state
Feb 28 09:50:11 asus kernel: [ 9896.245058] video LNXVIDEO:01: Restoring backlight state
Feb 28 09:50:11 asus kernel: [ 9896.245069] bbswitch: disabling discrete graphics
Feb 28 09:50:11 asus kernel: [ 9896.245087] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
Feb 28 09:50:11 asus kernel: [ 9896.330996] cfg80211: World regulatory domain updated:
Feb 28 09:50:11 asus kernel: [ 9896.331006] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Feb 28 09:50:11 asus kernel: [ 9896.331014] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 28 09:50:11 asus kernel: [ 9896.331020] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 28 09:50:11 asus kernel: [ 9896.331025] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Feb 28 09:50:11 asus kernel: [ 9896.331031] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 28 09:50:11 asus kernel: [ 9896.331036] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 28 09:50:14 asus kernel: [ 9899.013125] ata1.00: exception Emask 0x10 SAct 0x0 SErr 0x50000 action 0xe frozen
Feb 28 09:50:14 asus kernel: [ 9899.013137] ata1.00: irq_stat 0x00400000, PHY RDY changed
Feb 28 09:50:14 asus kernel: [ 9899.013146] ata1: SError: { PHYRdyChg CommWake }
Feb 28 09:50:14 asus kernel: [ 9899.013155] ata1.00: failed command: IDENTIFY DEVICE
Feb 28 09:50:14 asus kernel: [ 9899.013170] ata1.00: cmd ec/00:01:00:00:00/00:00:00:00:00/40 tag 6 pio 512 in
Feb 28 09:50:14 asus kernel: [ 9899.013170]          res 50/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)
Feb 28 09:50:14 asus kernel: [ 9899.013179] ata1.00: status: { DRDY }
Feb 28 09:50:14 asus kernel: [ 9899.013191] ata1: hard resetting link
Feb 28 09:50:15 asus kernel: [ 9899.735885] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Feb 28 09:50:15 asus kernel: [ 9899.737753] ata1.00: configured for UDMA/133
Feb 28 09:50:15 asus kernel: [ 9899.751916] ata1: EH complete
Feb 28 09:50:15 asus kernel: [ 9899.850154] wlan0: authenticate with 00:19:7b:a4:f6:15
Feb 28 09:50:15 asus kernel: [ 9899.865118] wlan0: send auth to 00:19:7b:a4:f6:15 (try 1/3)
Feb 28 09:50:15 asus kernel: [ 9899.866779] wlan0: authenticated
Feb 28 09:50:15 asus kernel: [ 9899.869222] wlan0: associate with 00:19:7b:a4:f6:15 (try 1/3)
Feb 28 09:50:15 asus kernel: [ 9899.873860] wlan0: RX AssocResp from 00:19:7b:a4:f6:15 (capab=0x431 status=0 aid=2)
Feb 28 09:50:15 asus kernel: [ 9899.873948] wlan0: associated
Feb 28 09:50:15 asus kernel: [ 9900.454480] bbswitch: enabling discrete graphics
Feb 28 09:51:48 asus kernel: [ 9900.897591] PM: Syncing filesystems ... done.
Feb 28 09:51:48 asus kernel: [ 9901.017539] Freezing user space processes ... (elapsed 0.002 seconds) done.
Feb 28 09:51:48 asus kernel: [ 9901.019828] PM: Marking nosave pages: [mem 0x00058000-0x00058fff]
Feb 28 09:51:48 asus kernel: [ 9901.019833] PM: Marking nosave pages: [mem 0x0009e000-0x000fffff]
Feb 28 09:51:48 asus kernel: [ 9901.019840] PM: Marking nosave pages: [mem 0xb95b9000-0xb95b9fff]
Feb 28 09:51:48 asus kernel: [ 9901.019843] PM: Marking nosave pages: [mem 0xb95c1000-0xb95c1fff]
Feb 28 09:51:48 asus kernel: [ 9901.019846] PM: Marking nosave pages: [mem 0xb98d4000-0xb98dafff]
Feb 28 09:51:48 asus kernel: [ 9901.019849] PM: Marking nosave pages: [mem 0xba14c000-0xba3cffff]
Feb 28 09:51:48 asus kernel: [ 9901.019878] PM: Marking nosave pages: [mem 0xc98e3000-0xc9ae8fff]
Feb 28 09:51:48 asus kernel: [ 9901.019902] PM: Marking nosave pages: [mem 0xc9e0f000-0xcaffefff]
Feb 28 09:51:48 asus kernel: [ 9901.020085] PM: Marking nosave pages: [mem 0xcb000000-0xffffffff]
Feb 28 09:51:48 asus kernel: [ 9901.021899] PM: Basic memory bitmaps created
Feb 28 09:51:48 asus kernel: [ 9901.023416] PM: Preallocating image memory... done (allocated 1229550 pages)
Feb 28 09:51:48 asus kernel: [ 9902.399666] PM: Allocated 4918200 kbytes in 1.37 seconds (3589.92 MB/s)
Feb 28 09:51:48 asus kernel: [ 9902.399671] Freezing remaining freezable tasks ... (elapsed 0.795 seconds) done.
Feb 28 09:51:48 asus kernel: [ 9903.196113] Suspending console(s) (use no_console_suspend to debug)
Feb 28 09:51:48 asus kernel: [ 9903.196219] wlan0: deauthenticating from 00:19:7b:a4:f6:15 by local choice (reason=3)
Feb 28 09:51:48 asus kernel: [ 9903.232228] cfg80211: Calling CRDA to update world regulatory domain
Feb 28 09:51:48 asus kernel: [ 9903.232866] mei_me 0000:00:16.0: H_RDY is not cleared 0x801A1A18
Feb 28 09:51:48 asus kernel: [ 9904.560910] PM: freeze of devices complete after 1363.948 msecs
Feb 28 09:51:48 asus kernel: [ 9904.561282] PM: late freeze of devices complete after 0.367 msecs
Feb 28 09:51:48 asus kernel: [ 9904.562336] PM: noirq freeze of devices complete after 1.049 msecs
Feb 28 09:51:48 asus kernel: [ 9904.563360] ACPI: Preparing to enter system sleep state S4
Feb 28 09:51:48 asus kernel: [ 9904.568645] PM: Saving platform NVS memory
Feb 28 09:51:48 asus kernel: [ 9904.597771] Disabling non-boot CPUs ...
Feb 28 09:51:48 asus kernel: [ 9904.600339] smpboot: CPU 1 is now offline
Feb 28 09:51:48 asus kernel: [ 9904.702810] smpboot: CPU 2 is now offline
Feb 28 09:51:48 asus kernel: [ 9904.806869] smpboot: CPU 3 is now offline
Feb 28 09:51:48 asus kernel: [ 9904.807489] PM: Creating hibernation image:
Feb 28 09:51:48 asus kernel: [ 9905.084728] PM: Need to copy 801759 pages
Feb 28 09:51:48 asus kernel: [ 9905.084733] PM: Normal pages needed: 801759 + 1024, available pages: 1265311
Feb 28 09:51:48 asus kernel: [ 9904.810272] PM: Restoring platform NVS memory
Feb 28 09:51:48 asus kernel: [ 9904.815078] Enabling non-boot CPUs ...
Feb 28 09:51:48 asus kernel: [ 9904.815140] x86: Booting SMP configuration:
Feb 28 09:51:48 asus kernel: [ 9904.815143] smpboot: Booting Node 0 Processor 1 APIC 0x2
Feb 28 09:51:48 asus kernel: [ 9904.830991] CPU1 is up
Feb 28 09:51:48 asus kernel: [ 9904.831029] smpboot: Booting Node 0 Processor 2 APIC 0x1
Feb 28 09:51:48 asus kernel: [ 9904.847668] CPU2 is up
Feb 28 09:51:48 asus kernel: [ 9904.847702] smpboot: Booting Node 0 Processor 3 APIC 0x3
Feb 28 09:51:48 asus kernel: [ 9904.863759] CPU3 is up
Feb 28 09:51:48 asus kernel: [ 9904.883908] ACPI: Waking up from system sleep state S4
Feb 28 09:51:48 asus kernel: [ 9904.923268] PM: noirq restore of devices complete after 32.041 msecs
Feb 28 09:51:48 asus kernel: [ 9904.923560] PM: early restore of devices complete after 0.254 msecs
Feb 28 09:51:48 asus kernel: [ 9905.265775] usb usb1: root hub lost power or was reset
Feb 28 09:51:48 asus kernel: [ 9905.265780] usb usb2: root hub lost power or was reset
Feb 28 09:51:48 asus kernel: [ 9905.266045] xhci_hcd 0000:00:14.0: irq 59 for MSI/MSI-X
Feb 28 09:51:48 asus kernel: [ 9905.266061] snd_hda_intel 0000:00:03.0: irq 61 for MSI/MSI-X
Feb 28 09:51:48 asus kernel: [ 9905.266184] mei_me 0000:00:16.0: irq 63 for MSI/MSI-X
Feb 28 09:51:48 asus kernel: [ 9905.266307] ath: phy0: ASPM enabled: 0x42
Feb 28 09:51:48 asus kernel: [ 9905.267627] snd_hda_intel 0000:00:1b.0: irq 64 for MSI/MSI-X
Feb 28 09:51:48 asus kernel: [ 9905.587071] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Feb 28 09:51:48 asus kernel: [ 9905.588942] ata1.00: configured for UDMA/133
Feb 28 09:51:48 asus kernel: [ 9905.595174] usb 1-4: reset full-speed USB device number 7 using xhci_hcd
Feb 28 09:51:48 asus kernel: [ 9905.603193] sd 0:0:0:0: [sda] Starting disk
Feb 28 09:51:48 asus kernel: [ 9905.611901] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88020928dd80
Feb 28 09:51:48 asus kernel: [ 9905.611905] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88020928de00
Feb 28 09:51:48 asus kernel: [ 9905.611908] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88020928ddc0
Feb 28 09:51:48 asus kernel: [ 9905.611910] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800a617c840
Feb 28 09:51:48 asus kernel: [ 9905.611913] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800a617c800
Feb 28 09:51:48 asus kernel: [ 9905.723289] usb 1-5: reset high-speed USB device number 3 using xhci_hcd
Feb 28 09:51:48 asus kernel: [ 9905.789269] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88021f792f40
Feb 28 09:51:48 asus kernel: [ 9907.040016] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
Feb 28 09:51:48 asus kernel: [ 9907.267559] PM: restore of devices complete after 2000.709 msecs
Feb 28 09:51:48 asus kernel: [ 9907.268060] PM: Image restored successfully.
Feb 28 09:51:48 asus kernel: [ 9907.268107] PM: Basic memory bitmaps freed
Feb 28 09:51:48 asus kernel: [ 9907.268110] Restarting tasks ... done.
Feb 28 09:51:48 asus kernel: [ 9907.294165] cfg80211: World regulatory domain updated:
Feb 28 09:51:48 asus kernel: [ 9907.294176] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Feb 28 09:51:48 asus kernel: [ 9907.294183] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 28 09:51:48 asus kernel: [ 9907.294189] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 28 09:51:48 asus kernel: [ 9907.294193] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Feb 28 09:51:48 asus kernel: [ 9907.294198] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 28 09:51:48 asus kernel: [ 9907.294202] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 28 09:51:48 asus kernel: [ 9907.318623] video LNXVIDEO:00: Restoring backlight state
Feb 28 09:51:48 asus kernel: [ 9907.318633] video LNXVIDEO:01: Restoring backlight state
Feb 28 09:51:48 asus kernel: [ 9907.318641] bbswitch: disabling discrete graphics
Feb 28 09:51:48 asus kernel: [ 9907.318653] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
Feb 28 09:51:52 asus kernel: [ 9910.927801] wlan0: authenticate with 00:19:7b:a4:f6:15
Feb 28 09:51:52 asus kernel: [ 9910.944782] wlan0: send auth to 00:19:7b:a4:f6:15 (try 1/3)
Feb 28 09:51:52 asus kernel: [ 9910.946546] wlan0: authenticated
Feb 28 09:51:52 asus kernel: [ 9910.950359] wlan0: associate with 00:19:7b:a4:f6:15 (try 1/3)
Feb 28 09:51:52 asus kernel: [ 9910.957395] wlan0: RX AssocResp from 00:19:7b:a4:f6:15 (capab=0x431 status=0 aid=2)
Feb 28 09:51:52 asus kernel: [ 9910.957488] wlan0: associated

```
 
```

$ uname -a

Linux asus 3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```
 
```

#grub config

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force drm.vblankoffdelay=1 i915.semaphores=1 nmi_watchdog=0 ipv6.disable=1 acpi_osi="

GRUB_CMDLINE_LINUX="resume=UUID=a21ddf35-d03d-4f62-a3cd-3ed1396e012f"
```

---

### Post by RockTeam on 2015-03-06
I have tried with the kernel 3.16 but in this case I’ve got another problem - my hardware (CPU at least) is not determining correctly by the OS.
 
Commit Log for Mon Mar  2 22:16:47 2015

Installed the following packages:
linux-generic-lts-utopic (3.16.0.31.24)
linux-headers-3.16.0-31 (3.16.0-31.41~14.04.1)
linux-headers-3.16.0-31-generic (3.16.0-31.41~14.04.1)
linux-headers-generic-lts-utopic (3.16.0.31.24)
linux-image-3.16.0-31-generic (3.16.0-31.41~14.04.1)
linux-image-extra-3.16.0-31-generic (3.16.0-31.41~14.04.1)
linux-image-generic-lts-utopic (3.16.0.31.24)
linux-signed-generic-lts-utopic (3.16.0.31.24)
linux-signed-image-3.16.0-31-generic (3.16.0-31.41~14.04.1)
linux-signed-image-generic-lts-utopic (3.16.0.31.24)

After that we can see a the following outputs shown below:
 
```

$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_cur_freq
2127937
2000375
2262609
2127226

```
 
```

$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_available_governors
performance powersave
performance powersave
performance powersave
performance powersave

```

The correct values should be the same as when kernel 3.13 is running:
```

$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_cur_freq
754000
754000
754000
754000

```
 
```

$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_available_governors
conservative ondemand userspace powersave performance
conservative ondemand userspace powersave performance
conservative ondemand userspace powersave performance
conservative ondemand userspace powersave performance 

```

It is very similar that after the exit from sleep the battery controller is not reported the battery charge level immediately and the indicator in the tray show 0%. When the OS is resuming at the second time the battery charge level keeps at the same level 0% but in the same time the system is no longer goes to sleep because the event for hibernation at 1% (battery charge - manually configuration) has passed.

---

### Post by RockTeam on 2015-03-09
Attaching the dmesg log file for the same event when resuming from the hibernation mode. Do we have an experts here?

---

### Post by RockTeam on 2015-05-08
Does nobody knows what to do with this issue for further investigation?

---

### Post by os2 on 2015-09-02
Can you show what PM-utils scripts you have running?
Just copy and paste in [code].

---

### Post by RockTeam on 2015-09-03
Below are my pm-utils scripts and comments how it was going.

```

Wed Sep  2 22:50:42 MSK 2015: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:
/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status hibernate hibernate:
/usr/lib/pm-utils/sleep.d/000record-status hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux asus 3.13.0-62-generic #102-Ubuntu SMP Tue Aug 11 14:29:36 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
md4                    12595  0 
ctr                    13049  2 
ccm                    17773  2 
bbswitch               13943  0 
rfcomm                 69160  12 
bnep                   19624  2 
binfmt_misc            17468  1 
nls_iso8859_1          12713  1 
nls_utf8               12557  2 
cifs                  462779  4 
fscache                63988  1 cifs
arc4                   12608  2 
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630728  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
snd_hda_codec_hdmi     46368  1 
snd_hda_codec_conexant    57486  1 
ipt_REJECT             12541  1 
xt_LOG                 17717  5 
xt_multiport           12798  2 
xt_limit               12711  7 
xt_tcpudp              12884  9 
xt_addrtype            12635  4 
nf_conntrack_ipv4      15012  8 
nf_defrag_ipv4         12758  1 nf_conntrack_ipv4
xt_conntrack           12760  8 
ip6_tables             27025  0 
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12770  0 
nf_nat                 21841  1 nf_nat_ftp
nf_conntrack_ftp       18638  1 nf_nat_ftp
nf_conntrack           97202  7 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4
iptable_filter         12810  1 
ip_tables              27239  1 iptable_filter
x_tables               34059  10 ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,xt_multiport,iptable_filter,ipt_REJECT,ip6_tables,xt_addrtype
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
mxm_wmi                13021  0 
snd_hda_intel          56531  5 
snd_hda_codec         193017  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
parport_pc             32701  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
ppdev                  17671  0 
snd                    69322  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
lpc_ich                21080  0 
shpchp                 37032  0 
ath3k                  17414  0 
btusb                  32412  0 
bluetooth             391136  23 bnep,ath3k,btusb,rfcomm
i915                  788212  5 
mei_me                 18627  0 
mei                    82276  1 mei_me
drm_kms_helper         55071  1 i915
drm                   303102  4 i915,drm_kms_helper
i2c_algo_bit           13413  1 i915
soundcore              12680  1 snd
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             143187  0 
kvm                   455843  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  4 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
joydev                 17381  0 
serio_raw              13462  0 
wmi                    19177  2 mxm_wmi,asus_wmi
mac_hid                13205  0 
video                  19476  2 i915,asus_wmi
psmouse               106692  0 
ahci                   34091  3 
libahci                32716  1 ahci
             total       used       free     shared    buffers     cached
Mem:       8057472    2482060    5575412     124212     135232    1586688
-/+ buffers/cache:     760140    7297332
Swap:      8860668          0    8860668
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.

Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx hibernate hibernate:
/usr/lib/pm-utils/sleep.d/50unload_alx hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Selected interface 'wlan0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:
/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.

Wed Sep  2 22:50:43 MSK 2015: performing hibernate
Thu Sep  3 21:10:25 MSK 2015: Awake.
Thu Sep  3 21:10:25 MSK 2015: Running hooks for thaw
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:
/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level    = 128

/dev/sda:
 setting standby to 36 (3 minutes)
/usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate:
Selected interface 'wlan0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx thaw hibernate:
/usr/lib/pm-utils/sleep.d/50unload_alx thaw hibernate: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.

Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:
/etc/pm/sleep.d/10_grub-common thaw hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status thaw hibernate:
/usr/lib/pm-utils/sleep.d/000record-status thaw hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:
/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.

Thu Sep  3 21:10:25 MSK 2015: Finished.
Initial commandline parameters: 
Thu Sep  3 21:10:29 MSK 2015: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:
/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status hibernate hibernate:
/usr/lib/pm-utils/sleep.d/000record-status hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux asus 3.13.0-62-generic #102-Ubuntu SMP Tue Aug 11 14:29:36 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
md4                    12595  0 
ctr                    13049  2 
ccm                    17773  2 
bbswitch               13943  0 
rfcomm                 69160  12 
bnep                   19624  2 
binfmt_misc            17468  1 
nls_iso8859_1          12713  1 
nls_utf8               12557  2 
cifs                  462779  4 
fscache                63988  1 cifs
arc4                   12608  2 
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630728  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
snd_hda_codec_hdmi     46368  1 
snd_hda_codec_conexant    57486  1 
ipt_REJECT             12541  1 
xt_LOG                 17717  5 
xt_multiport           12798  2 
xt_limit               12711  7 
xt_tcpudp              12884  9 
xt_addrtype            12635  4 
nf_conntrack_ipv4      15012  8 
nf_defrag_ipv4         12758  1 nf_conntrack_ipv4
xt_conntrack           12760  8 
ip6_tables             27025  0 
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12770  0 
nf_nat                 21841  1 nf_nat_ftp
nf_conntrack_ftp       18638  1 nf_nat_ftp
nf_conntrack           97202  7 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4
iptable_filter         12810  1 
ip_tables              27239  1 iptable_filter
x_tables               34059  10 ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,xt_multiport,iptable_filter,ipt_REJECT,ip6_tables,xt_addrtype
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
mxm_wmi                13021  0 
snd_hda_intel          56531  5 
snd_hda_codec         193017  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
parport_pc             32701  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
ppdev                  17671  0 
snd                    69322  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
lpc_ich                21080  0 
shpchp                 37032  0 
ath3k                  17414  0 
btusb                  32412  0 
bluetooth             391136  23 bnep,ath3k,btusb,rfcomm
i915                  788212  5 
mei_me                 18627  0 
mei                    82276  1 mei_me
drm_kms_helper         55071  1 i915
drm                   303102  4 i915,drm_kms_helper
i2c_algo_bit           13413  1 i915
soundcore              12680  1 snd
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             143187  0 
kvm                   455843  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  4 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
joydev                 17381  0 
serio_raw              13462  0 
wmi                    19177  2 mxm_wmi,asus_wmi
mac_hid                13205  0 
video                  19476  2 i915,asus_wmi
psmouse               106692  0 
ahci                   34091  3 
libahci                32716  1 ahci
             total       used       free     shared    buffers     cached
Mem:       8057472    2440348    5617124      84896     135256    1547408
-/+ buffers/cache:     757684    7299788
Swap:      8860668          0    8860668
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.

Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx hibernate hibernate:
/usr/lib/pm-utils/sleep.d/50unload_alx hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Selected interface 'wlan0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:
/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.

Thu Sep  3 21:10:30 MSK 2015: performing hibernate
Thu Sep  3 21:11:39 MSK 2015: Awake.
Thu Sep  3 21:11:39 MSK 2015: Running hooks for thaw
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:
/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level    = 128

/dev/sda:
 setting standby to 36 (3 minutes)
/usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate:
Selected interface 'wlan0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx thaw hibernate:
/usr/lib/pm-utils/sleep.d/50unload_alx thaw hibernate: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.

Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:
/etc/pm/sleep.d/10_grub-common thaw hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status thaw hibernate:
/usr/lib/pm-utils/sleep.d/000record-status thaw hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:
/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.

Thu Sep  3 21:11:39 MSK 2015: Finished.

```

Wed Sep 2 22:50:42 MSK 2015: Running hooks for hibernate. [COLOR=#ff0000]=> Hibernate PC.[/COLOR]
Thu Sep 3 21:10:25 MSK 2015: Awake. [COLOR=#ff0000]=> Turning on PC.[/COLOR]
Thu Sep 3 21:10:25 MSK 2015: Finished. [COLOR=#ff0000]=> It seems that the battery is not detected and I can see yesterday's time when the hibernate was performed. In a 4 seconds the OS was get freezed and went into hibernate again by itself.[/COLOR]
Thu Sep 3 21:10:29 MSK 2015: Running hooks for hibernate.
Thu Sep 3 21:11:39 MSK 2015: Awake.[COLOR=#ff0000] => Turning on PC second time[/COLOR]
Thu Sep 3 21:11:39 MSK 2015: Finished. [COLOR=#ff0000]=> PC is wake up and the battery indicator was updated in a 20-30 seconds approximately.[/COLOR]

Please let me know if you have an idea what need to be checked next? Thank you in advance.

---

### Post by os2 on 2015-09-04
Could you also post /var/log/syslog and /var/log/messages shortly before and after you suspend to disk.

As there aren't any flaws readily apparent I just want to eliminate any userspace possibilities before we go further.

---

### Post by RockTeam on 2015-09-05
I haven't messages in the log directory. But the rest of outputs were collected including the battery status after the first wake up.

pm-suspend summary (no significant changes since the last output with all details).
```

Fri Sep  4 22:57:04 MSK 2015: performing hibernate
Sat Sep  5 09:52:52 MSK 2015: Awake.
Sat Sep  5 09:52:52 MSK 2015: Running hooks for thaw
Sat Sep  5 09:52:52 MSK 2015: Finished.
Sat Sep  5 10:45:40 MSK 2015: Running hooks for hibernate.
Sat Sep  5 10:45:40 MSK 2015: performing hibernate
Sat Sep  5 11:00:57 MSK 2015: Awake.
Sat Sep  5 11:00:57 MSK 2015: Running hooks for thaw
Sat Sep  5 11:00:57 MSK 2015: Finished.
Sat Sep  5 11:01:11 MSK 2015: Running hooks for hibernate.
Sat Sep  5 11:01:11 MSK 2015: performing hibernate
Sat Sep  5 11:04:07 MSK 2015: Awake.
Sat Sep  5 11:04:07 MSK 2015: Running hooks for thaw
Sat Sep  5 11:04:07 MSK 2015: Finished.

```

An output for /var/log/syslog
```

Sep  5 09:52:52 asus kernel: [  203.540132] PM: Syncing filesystems ... done.
Sep  5 09:52:52 asus kernel: [  203.587107] Freezing user space processes ... (elapsed 0.001 seconds) done.
Sep  5 09:52:52 asus kernel: [  203.588607] PM: Marking nosave pages: [mem 0x00058000-0x00058fff]
Sep  5 09:52:52 asus kernel: [  203.588609] PM: Marking nosave pages: [mem 0x0009e000-0x000fffff]
Sep  5 09:52:52 asus kernel: [  203.588612] PM: Marking nosave pages: [mem 0xb95c3000-0xb95c3fff]
Sep  5 09:52:52 asus kernel: [  203.588613] PM: Marking nosave pages: [mem 0xb95cb000-0xb95cbfff]
Sep  5 09:52:52 asus kernel: [  203.588614] PM: Marking nosave pages: [mem 0xb98d4000-0xb98dafff]
Sep  5 09:52:52 asus kernel: [  203.588616] PM: Marking nosave pages: [mem 0xba14c000-0xba3cffff]
Sep  5 09:52:52 asus kernel: [  203.588627] PM: Marking nosave pages: [mem 0xc98e3000-0xc9ae8fff]
Sep  5 09:52:52 asus kernel: [  203.588637] PM: Marking nosave pages: [mem 0xc9e0f000-0xcaffefff]
Sep  5 09:52:52 asus kernel: [  203.588710] PM: Marking nosave pages: [mem 0xcb000000-0xffffffff]
Sep  5 09:52:52 asus kernel: [  203.589430] PM: Basic memory bitmaps created
Sep  5 09:52:52 asus kernel: [  203.589979] PM: Preallocating image memory... done (allocated 510429 pages)
Sep  5 09:52:52 asus kernel: [  203.769041] PM: Allocated 2041716 kbytes in 0.17 seconds (12010.09 MB/s)
Sep  5 09:52:52 asus kernel: [  203.769043] Freezing remaining freezable tasks ... (elapsed 3.452 seconds) done.
Sep  5 09:52:52 asus kernel: [  207.223500] Suspending console(s) (use no_console_suspend to debug)
Sep  5 09:52:52 asus kernel: [  207.223533] wlan0: deauthenticating from 00:19:7b:a4:f6:15 by local choice (reason=3)
Sep  5 09:52:52 asus kernel: [  207.255466] cfg80211: Calling CRDA to update world regulatory domain
Sep  5 09:52:52 asus kernel: [  208.575216] PM: freeze of devices complete after 1350.882 msecs
Sep  5 09:52:52 asus kernel: [  208.575381] PM: late freeze of devices complete after 0.162 msecs
Sep  5 09:52:52 asus kernel: [  208.575980] PM: noirq freeze of devices complete after 0.598 msecs
Sep  5 09:52:52 asus kernel: [  208.576297] ACPI: Preparing to enter system sleep state S4
Sep  5 09:52:52 asus kernel: [  208.598879] PM: Saving platform NVS memory
Sep  5 09:52:52 asus kernel: [  208.607528] Disabling non-boot CPUs ...
Sep  5 09:52:52 asus kernel: [  208.608739] kvm: disabling virtualization on CPU1
Sep  5 09:52:52 asus kernel: [  208.710177] smpboot: CPU 1 is now offline
Sep  5 09:52:52 asus kernel: [  208.711628] kvm: disabling virtualization on CPU2
Sep  5 09:52:52 asus kernel: [  208.814245] smpboot: CPU 2 is now offline
Sep  5 09:52:52 asus kernel: [  208.814677] Broke affinity for irq 59
Sep  5 09:52:52 asus kernel: [  208.814678] Broke affinity for irq 60
Sep  5 09:52:52 asus kernel: [  208.815680] kvm: disabling virtualization on CPU3
Sep  5 09:52:52 asus kernel: [  208.918309] smpboot: CPU 3 is now offline
Sep  5 09:52:52 asus kernel: [  208.918723] PM: Creating hibernation image:
Sep  5 09:52:52 asus kernel: [  209.001462] PM: Need to copy 509135 pages
Sep  5 09:52:52 asus kernel: [  209.001464] PM: Normal pages needed: 509135 + 1024, available pages: 1557929
Sep  5 09:52:52 asus kernel: [  208.919629] PM: Restoring platform NVS memory
Sep  5 09:52:52 asus kernel: [  208.921703] Enabling non-boot CPUs ...
Sep  5 09:52:52 asus kernel: [  208.921732] x86: Booting SMP configuration:
Sep  5 09:52:52 asus kernel: [  208.921733] smpboot: Booting Node 0 Processor 1 APIC 0x2
Sep  5 09:52:52 asus kernel: [  208.933588] kvm: enabling virtualization on CPU1
Sep  5 09:52:52 asus kernel: [  208.935875] CPU1 is up
Sep  5 09:52:52 asus kernel: [  208.935888] smpboot: Booting Node 0 Processor 2 APIC 0x1
Sep  5 09:52:52 asus kernel: [  208.947851] kvm: enabling virtualization on CPU2
Sep  5 09:52:52 asus kernel: [  208.950200] CPU2 is up
Sep  5 09:52:52 asus kernel: [  208.950216] smpboot: Booting Node 0 Processor 3 APIC 0x3
Sep  5 09:52:52 asus kernel: [  208.962180] kvm: enabling virtualization on CPU3
Sep  5 09:52:52 asus kernel: [  208.964474] CPU3 is up
Sep  5 09:52:52 asus kernel: [  208.970513] ACPI: Waking up from system sleep state S4
Sep  5 09:52:52 asus kernel: [  209.009814] PM: noirq restore of devices complete after 32.055 msecs
Sep  5 09:52:52 asus kernel: [  209.009946] PM: early restore of devices complete after 0.111 msecs
Sep  5 09:52:52 asus kernel: [  209.080113] usb usb1: root hub lost power or was reset
Sep  5 09:52:52 asus kernel: [  209.080114] usb usb2: root hub lost power or was reset
Sep  5 09:52:52 asus kernel: [  209.080230] snd_hda_intel 0000:00:03.0: irq 59 for MSI/MSI-X
Sep  5 09:52:52 asus kernel: [  209.080265] xhci_hcd 0000:00:14.0: irq 61 for MSI/MSI-X
Sep  5 09:52:52 asus kernel: [  209.080321] mei_me 0000:00:16.0: irq 63 for MSI/MSI-X
Sep  5 09:52:52 asus kernel: [  209.082327] ath: phy0: ASPM enabled: 0x42
Sep  5 09:52:52 asus kernel: [  209.082423] snd_hda_intel 0000:00:1b.0: irq 64 for MSI/MSI-X
Sep  5 09:52:52 asus kernel: [  209.405720] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Sep  5 09:52:52 asus kernel: [  209.407358] ata1.00: configured for UDMA/133
Sep  5 09:52:52 asus kernel: [  209.413744] usb 1-5: reset high-speed USB device number 3 using xhci_hcd
Sep  5 09:52:52 asus kernel: [  209.421758] sd 0:0:0:0: [sda] Starting disk
Sep  5 09:52:52 asus kernel: [  209.479626] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88021f6e59c0
Sep  5 09:52:52 asus kernel: [  209.597892] usb 1-4: reset full-speed USB device number 2 using xhci_hcd
Sep  5 09:52:52 asus kernel: [  209.614231] usb 1-4: device firmware changed
Sep  5 09:52:52 asus kernel: [  210.950699] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
Sep  5 09:52:52 asus kernel: [  211.020714] PM: restore of devices complete after 1939.475 msecs
Sep  5 09:52:52 asus kernel: [  211.020937] PM: Image restored successfully.
Sep  5 09:52:52 asus kernel: [  211.020960] PM: Basic memory bitmaps freed
Sep  5 09:52:52 asus kernel: [  211.021025] usb 1-4: USB disconnect, device number 2
Sep  5 09:52:52 asus kernel: [  211.021458] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88021f7b6540
Sep  5 09:52:52 asus kernel: [  211.021461] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88021f7b65c0
Sep  5 09:52:52 asus kernel: [  211.021463] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88021f7b6580
Sep  5 09:52:52 asus kernel: [  211.021465] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88021f538ac0
Sep  5 09:52:52 asus kernel: [  211.021467] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88021f538a80
Sep  5 09:52:52 asus rtkit-daemon[2683]: The canary thread is apparently starving. Taking action.
Sep  5 09:52:52 asus rtkit-daemon[2683]: Demoting known real-time threads.
Sep  5 09:52:52 asus rtkit-daemon[2683]: Successfully demoted thread 2895 of process 2677 (n/a).
Sep  5 09:52:52 asus rtkit-daemon[2683]: Successfully demoted thread 2878 of process 2677 (n/a).
Sep  5 09:52:52 asus rtkit-daemon[2683]: Successfully demoted thread 2818 of process 2677 (n/a).
Sep  5 09:52:52 asus rtkit-daemon[2683]: Successfully demoted thread 2677 of process 2677 (n/a).
Sep  5 09:52:52 asus rtkit-daemon[2683]: Demoted 4 threads.
Sep  5 09:52:52 asus NetworkManager[961]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Sep  5 09:52:52 asus NetworkManager[961]: <info> (wlan0): roamed from BSSID 00:19:7b:a4:f6:15 (WiFinet) to (none) ((none))
Sep  5 09:52:52 asus wpa_supplicant[1107]: wlan0: CTRL-EVENT-DISCONNECTED bssid=00:19:7b:a4:f6:15 reason=3 locally_generated=1
Sep  5 09:52:52 asus NetworkManager[961]: <warn> Connection disconnected (reason -3)
Sep  5 09:52:52 asus bluetoothd[906]: Adapter /org/bluez/906/hci0 has been disabled
Sep  5 09:52:52 asus bluetoothd[906]: Unregister path: /org/bluez/906/hci0
Sep  5 09:52:52 asus bluetoothd[906]: hci0: Set IO Capability (0x0018) failed: Invalid Index (0x11)
Sep  5 09:52:52 asus kernel: [  211.026865] cfg80211: World regulatory domain updated:
Sep  5 09:52:52 asus kernel: [  211.026869] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Sep  5 09:52:52 asus kernel: [  211.026871] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep  5 09:52:52 asus kernel: [  211.026873] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep  5 09:52:52 asus kernel: [  211.026875] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep  5 09:52:52 asus kernel: [  211.026876] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep  5 09:52:52 asus kernel: [  211.026877] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep  5 09:52:52 asus kernel: [  211.020961] Restarting tasks ... done.
Sep  5 09:52:52 asus NetworkManager[961]: <info> (wlan0): supplicant interface state: completed -> disconnected
Sep  5 09:52:52 asus kernel: [  211.049791] video LNXVIDEO:00: Restoring backlight state
Sep  5 09:52:52 asus kernel: [  211.049796] video LNXVIDEO:01: Restoring backlight state
Sep  5 09:52:52 asus kernel: [  211.049801] bbswitch: disabling discrete graphics
Sep  5 09:52:52 asus kernel: [  211.049807] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
Sep  5 09:52:52 asus wpa_supplicant[1107]: wlan0: CTRL-EVENT-SCAN-STARTED 
Sep  5 09:52:52 asus NetworkManager[961]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Sep  5 09:52:52 asus anacron[12539]: Anacron 2.3 started on 2015-09-05
Sep  5 09:52:52 asus kernel: [  211.186767] usb 1-4: new full-speed USB device number 4 using xhci_hcd
Sep  5 09:52:52 asus anacron[12539]: Will run job `cron.daily' in 5 min.
Sep  5 09:52:52 asus anacron[12539]: Jobs will be executed sequentially
Sep  5 09:52:52 asus kernel: [  211.204576] usb 1-4: string descriptor 0 read error: -22
Sep  5 09:52:52 asus kernel: [  211.204582] usb 1-4: New USB device found, idVendor=13d3, idProduct=3393
Sep  5 09:52:52 asus kernel: [  211.204584] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Sep  5 09:52:52 asus kernel: [  211.327135] init: anacron main process (12539) killed by TERM signal
Sep  5 09:52:52 asus kernel: [  211.362570] usb 1-4: USB disconnect, device number 4
Sep  5 09:52:53 asus kernel: [  211.635122] usb 1-4: new full-speed USB device number 5 using xhci_hcd
Sep  5 09:52:53 asus kernel: [  211.653081] usb 1-4: string descriptor 0 read error: -22
Sep  5 09:52:53 asus kernel: [  211.653096] usb 1-4: New USB device found, idVendor=13d3, idProduct=3393
Sep  5 09:52:53 asus kernel: [  211.653101] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Sep  5 09:52:53 asus bluetoothd[906]: input-headset driver probe failed for device 78:CA:04:6B:89:AB
Sep  5 09:52:53 asus bluetoothd[906]: Unknown command complete for opcode 19
Sep  5 09:52:53 asus bluetoothd[906]: hci0: Set Discoverable (0x0006) failed: Not Powered (0x0f)
Sep  5 09:52:53 asus bluetoothd[906]: Adapter /org/bluez/906/hci0 has been enabled
Sep  5 09:52:56 asus kernel: [  214.675671] wlan0: authenticate with 00:19:7b:a4:f6:15
Sep  5 09:52:56 asus wpa_supplicant[1107]: wlan0: SME: Trying to authenticate with 00:19:7b:a4:f6:15 (SSID='WiFinet' freq=2432 MHz)
Sep  5 09:52:56 asus NetworkManager[961]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Sep  5 09:52:56 asus wpa_supplicant[1107]: wlan0: Trying to associate with 00:19:7b:a4:f6:15 (SSID='WiFinet' freq=2432 MHz)
Sep  5 09:52:56 asus kernel: [  214.691060] wlan0: send auth to 00:19:7b:a4:f6:15 (try 1/3)
Sep  5 09:52:56 asus kernel: [  214.692708] wlan0: authenticated
Sep  5 09:52:56 asus kernel: [  214.692942] wlan0: associate with 00:19:7b:a4:f6:15 (try 1/3)
Sep  5 09:52:56 asus wpa_supplicant[1107]: wlan0: Associated with 00:19:7b:a4:f6:15
Sep  5 09:52:56 asus NetworkManager[961]: <info> (wlan0): supplicant interface state: authenticating -> associated
Sep  5 09:52:56 asus wpa_supplicant[1107]: wlan0: WPA: Key negotiation completed with 00:19:7b:a4:f6:15 [PTK=CCMP GTK=CCMP]
Sep  5 09:52:56 asus wpa_supplicant[1107]: wlan0: CTRL-EVENT-CONNECTED - Connection to 00:19:7b:a4:f6:15 completed [id=0 id_str=]
Sep  5 09:52:56 asus kernel: [  214.697290] wlan0: RX AssocResp from 00:19:7b:a4:f6:15 (capab=0x431 status=0 aid=4)
Sep  5 09:52:56 asus kernel: [  214.697331] wlan0: associated
Sep  5 09:52:56 asus NetworkManager[961]: <info> (wlan0): supplicant interface state: associated -> completed
Sep  5 09:52:56 asus NetworkManager[961]: <info> (wlan0): roamed from BSSID (none) ((none)) to 00:19:7b:a4:f6:15 (WiFinet)
Sep  5 10:05:59 asus dbus[845]: [system] Activating service name='org.blueman.Mechanism' (using servicehelper)
Sep  5 10:05:59 asus blueman-mechanism: Starting blueman-mechanism 
Sep  5 10:05:59 asus dbus[845]: [system] Successfully activated service 'org.blueman.Mechanism'
Sep  5 10:05:59 asus blueman-mechanism: loading RfKill 
Sep  5 10:05:59 asus blueman-mechanism: loading Config 
Sep  5 10:05:59 asus blueman-mechanism: loading Network 
Sep  5 10:05:59 asus blueman-mechanism: loading Ppp 
Sep  5 10:05:59 asus kernel: [  998.393442] usb 1-4: USB disconnect, device number 5
Sep  5 10:05:59 asus bluetoothd[906]: Adapter /org/bluez/906/hci0 has been disabled
Sep  5 10:05:59 asus bluetoothd[906]: Unregister path: /org/bluez/906/hci0
Sep  5 10:05:59 asus bluetoothd[906]: hci0: Set IO Capability (0x0018) failed: Invalid Index (0x11)
Sep  5 10:06:29 asus blueman-mechanism: Exiting 
Sep  5 10:07:10 asus wpa_supplicant[1107]: wlan0: WPA: Group rekeying completed with 00:19:7b:a4:f6:15 [GTK=CCMP]
Sep  5 10:17:01 asus CRON[17275]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep  5 10:45:40 asus anacron[5535]: Anacron 2.3 started on 2015-09-05
Sep  5 10:45:40 asus anacron[5535]: Will run job `cron.daily' in 5 min.
Sep  5 10:45:40 asus anacron[5535]: Jobs will be executed sequentially
Sep  5 10:45:40 asus kernel: [ 3380.811688] init: anacron main process (5535) killed by TERM signal
Sep  5 10:45:40 asus kernel: [ 3381.002502] bbswitch: enabling discrete graphics
Sep  5 11:00:57 asus kernel: [ 3381.441777] PM: Syncing filesystems ... done.
Sep  5 11:00:57 asus kernel: [ 3381.566044] Freezing user space processes ... (elapsed 0.001 seconds) done.
Sep  5 11:00:57 asus kernel: [ 3381.567604] PM: Marking nosave pages: [mem 0x00058000-0x00058fff]
Sep  5 11:00:57 asus kernel: [ 3381.567606] PM: Marking nosave pages: [mem 0x0009e000-0x000fffff]
Sep  5 11:00:57 asus kernel: [ 3381.567609] PM: Marking nosave pages: [mem 0xb95c3000-0xb95c3fff]
Sep  5 11:00:57 asus kernel: [ 3381.567611] PM: Marking nosave pages: [mem 0xb95cb000-0xb95cbfff]
Sep  5 11:00:57 asus kernel: [ 3381.567612] PM: Marking nosave pages: [mem 0xb98d4000-0xb98dafff]
Sep  5 11:00:57 asus kernel: [ 3381.567613] PM: Marking nosave pages: [mem 0xba14c000-0xba3cffff]
Sep  5 11:00:57 asus kernel: [ 3381.567626] PM: Marking nosave pages: [mem 0xc98e3000-0xc9ae8fff]
Sep  5 11:00:57 asus kernel: [ 3381.567636] PM: Marking nosave pages: [mem 0xc9e0f000-0xcaffefff]
Sep  5 11:00:57 asus kernel: [ 3381.567718] PM: Marking nosave pages: [mem 0xcb000000-0xffffffff]
Sep  5 11:00:57 asus kernel: [ 3381.568477] PM: Basic memory bitmaps created
Sep  5 11:00:57 asus kernel: [ 3381.568950] PM: Preallocating image memory... done (allocated 615863 pages)
Sep  5 11:00:57 asus kernel: [ 3381.762661] PM: Allocated 2463452 kbytes in 0.19 seconds (12965.53 MB/s)
Sep  5 11:00:57 asus kernel: [ 3381.762662] Freezing remaining freezable tasks ... (elapsed 4.417 seconds) done.
Sep  5 11:00:57 asus kernel: [ 3386.197205] Suspending console(s) (use no_console_suspend to debug)
Sep  5 11:00:57 asus kernel: [ 3386.197241] wlan0: deauthenticating from 00:19:7b:a4:f6:15 by local choice (reason=3)
Sep  5 11:00:57 asus kernel: [ 3386.235745] cfg80211: Calling CRDA to update world regulatory domain
Sep  5 11:00:57 asus kernel: [ 3386.253067] PM: freeze of devices complete after 55.820 msecs
Sep  5 11:00:57 asus kernel: [ 3386.253184] PM: late freeze of devices complete after 0.115 msecs
Sep  5 11:00:57 asus kernel: [ 3386.253820] PM: noirq freeze of devices complete after 0.634 msecs
Sep  5 11:00:57 asus kernel: [ 3386.254193] ACPI: Preparing to enter system sleep state S4
Sep  5 11:00:57 asus kernel: [ 3386.258124] PM: Saving platform NVS memory
Sep  5 11:00:57 asus kernel: [ 3386.267223] Disabling non-boot CPUs ...
Sep  5 11:00:57 asus kernel: [ 3386.268416] kvm: disabling virtualization on CPU1
Sep  5 11:00:57 asus kernel: [ 3386.369074] smpboot: CPU 1 is now offline
Sep  5 11:00:57 asus kernel: [ 3386.370473] kvm: disabling virtualization on CPU2
Sep  5 11:00:57 asus kernel: [ 3386.473136] smpboot: CPU 2 is now offline
Sep  5 11:00:57 asus kernel: [ 3386.473496] Broke affinity for irq 60
Sep  5 11:00:57 asus kernel: [ 3386.474502] kvm: disabling virtualization on CPU3
Sep  5 11:00:57 asus kernel: [ 3386.577198] smpboot: CPU 3 is now offline
Sep  5 11:00:57 asus kernel: [ 3386.577582] PM: Creating hibernation image:
Sep  5 11:00:57 asus kernel: [ 3386.657661] PM: Need to copy 614772 pages
Sep  5 11:00:57 asus kernel: [ 3386.657663] PM: Normal pages needed: 614772 + 1024, available pages: 1452298
Sep  5 11:00:57 asus kernel: [ 3386.578452] PM: Restoring platform NVS memory
Sep  5 11:00:57 asus kernel: [ 3386.580544] Enabling non-boot CPUs ...
Sep  5 11:00:57 asus kernel: [ 3386.580572] x86: Booting SMP configuration:
Sep  5 11:00:57 asus kernel: [ 3386.580573] smpboot: Booting Node 0 Processor 1 APIC 0x2
Sep  5 11:00:57 asus kernel: [ 3386.592428] kvm: enabling virtualization on CPU1
Sep  5 11:00:57 asus kernel: [ 3386.594706] CPU1 is up
Sep  5 11:00:57 asus kernel: [ 3386.594720] smpboot: Booting Node 0 Processor 2 APIC 0x1
Sep  5 11:00:57 asus kernel: [ 3386.606665] kvm: enabling virtualization on CPU2
Sep  5 11:00:57 asus kernel: [ 3386.608983] CPU2 is up
Sep  5 11:00:57 asus kernel: [ 3386.608996] smpboot: Booting Node 0 Processor 3 APIC 0x3
Sep  5 11:00:57 asus kernel: [ 3386.620946] kvm: enabling virtualization on CPU3
Sep  5 11:00:57 asus kernel: [ 3386.623242] CPU3 is up
Sep  5 11:00:57 asus kernel: [ 3386.629335] ACPI: Waking up from system sleep state S4
Sep  5 11:00:57 asus kernel: [ 3386.668700] PM: noirq restore of devices complete after 32.026 msecs
Sep  5 11:00:57 asus kernel: [ 3386.668832] PM: early restore of devices complete after 0.111 msecs
Sep  5 11:00:57 asus kernel: [ 3386.749045] snd_hda_intel 0000:00:03.0: irq 59 for MSI/MSI-X
Sep  5 11:00:57 asus kernel: [ 3386.751044] usb usb1: root hub lost power or was reset
Sep  5 11:00:57 asus kernel: [ 3386.751045] usb usb2: root hub lost power or was reset
Sep  5 11:00:57 asus kernel: [ 3386.751053] mei_me 0000:00:16.0: irq 63 for MSI/MSI-X
Sep  5 11:00:57 asus kernel: [ 3386.751133] ath: phy0: ASPM enabled: 0x42
Sep  5 11:00:57 asus kernel: [ 3386.751178] xhci_hcd 0000:00:14.0: irq 61 for MSI/MSI-X
Sep  5 11:00:57 asus kernel: [ 3386.751232] snd_hda_intel 0000:00:1b.0: irq 64 for MSI/MSI-X
Sep  5 11:00:57 asus kernel: [ 3387.068607] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Sep  5 11:00:57 asus kernel: [ 3387.068638] usb 1-5: reset high-speed USB device number 3 using xhci_hcd
Sep  5 11:00:57 asus kernel: [ 3387.070325] ata1.00: configured for UDMA/133
Sep  5 11:00:57 asus kernel: [ 3387.084662] sd 0:0:0:0: [sda] Starting disk
Sep  5 11:00:57 asus kernel: [ 3387.134581] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88021f6e59c0
Sep  5 11:00:57 asus kernel: [ 3387.877140] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
Sep  5 11:00:57 asus kernel: [ 3388.671915] PM: restore of devices complete after 1921.842 msecs
Sep  5 11:00:57 asus kernel: [ 3388.672100] PM: Image restored successfully.
Sep  5 11:00:57 asus kernel: [ 3388.672119] PM: Basic memory bitmaps freed
Sep  5 11:00:57 asus NetworkManager[961]: <info> (wlan0): roamed from BSSID 00:19:7b:a4:f6:15 (WiFinet) to (none) ((none))
Sep  5 11:00:57 asus wpa_supplicant[1107]: wlan0: CTRL-EVENT-DISCONNECTED bssid=00:19:7b:a4:f6:15 reason=3 locally_generated=1
Sep  5 11:00:57 asus NetworkManager[961]: <warn> Connection disconnected (reason -3)
Sep  5 11:00:57 asus kernel: [ 3388.672121] Restarting tasks ... done.
Sep  5 11:00:57 asus kernel: [ 3388.679065] cfg80211: World regulatory domain updated:
Sep  5 11:00:57 asus kernel: [ 3388.679069] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Sep  5 11:00:57 asus kernel: [ 3388.679070] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep  5 11:00:57 asus kernel: [ 3388.679072] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep  5 11:00:57 asus kernel: [ 3388.679074] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep  5 11:00:57 asus kernel: [ 3388.679076] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep  5 11:00:57 asus kernel: [ 3388.679077] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep  5 11:00:57 asus NetworkManager[961]: <info> (wlan0): supplicant interface state: completed -> disconnected
Sep  5 11:00:57 asus kernel: [ 3388.695560] video LNXVIDEO:00: Restoring backlight state
Sep  5 11:00:57 asus kernel: [ 3388.695564] video LNXVIDEO:01: Restoring backlight state
Sep  5 11:00:57 asus kernel: [ 3388.695568] bbswitch: disabling discrete graphics
Sep  5 11:00:57 asus kernel: [ 3388.695572] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
Sep  5 11:00:57 asus wpa_supplicant[1107]: wlan0: CTRL-EVENT-SCAN-STARTED 
Sep  5 11:00:57 asus NetworkManager[961]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Sep  5 11:00:57 asus kernel: [ 3388.841672] usb 1-4: new full-speed USB device number 6 using xhci_hcd
Sep  5 11:00:57 asus kernel: [ 3388.859187] usb 1-4: string descriptor 0 read error: -22
Sep  5 11:00:57 asus kernel: [ 3388.859193] usb 1-4: New USB device found, idVendor=13d3, idProduct=3393
Sep  5 11:00:57 asus kernel: [ 3388.859195] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Sep  5 11:00:57 asus anacron[6740]: Anacron 2.3 started on 2015-09-05
Sep  5 11:00:57 asus anacron[6740]: Will run job `cron.daily' in 5 min.
Sep  5 11:00:57 asus anacron[6740]: Jobs will be executed sequentially
Sep  5 11:00:57 asus kernel: [ 3388.895445] usb 1-4: USB disconnect, device number 6
Sep  5 11:00:57 asus kernel: [ 3388.975216] init: anacron main process (6740) killed by TERM signal
Sep  5 11:00:57 asus kernel: [ 3389.165919] usb 1-4: new full-speed USB device number 7 using xhci_hcd
Sep  5 11:00:57 asus kernel: [ 3389.183737] usb 1-4: string descriptor 0 read error: -22
Sep  5 11:00:57 asus kernel: [ 3389.183744] usb 1-4: New USB device found, idVendor=13d3, idProduct=3393
Sep  5 11:00:57 asus kernel: [ 3389.183747] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Sep  5 11:00:57 asus bluetoothd[906]: input-headset driver probe failed for device 78:CA:04:6B:89:AB
Sep  5 11:00:57 asus bluetoothd[906]: Unknown command complete for opcode 19
Sep  5 11:00:57 asus bluetoothd[906]: hci0: Set Discoverable (0x0006) failed: Not Powered (0x0f)
Sep  5 11:00:57 asus bluetoothd[906]: hci0: Set Powered (0x0005) failed: <unknown status> (0x12)
Sep  5 11:01:01 asus wpa_supplicant[1107]: wlan0: SME: Trying to authenticate with 00:19:7b:a4:f6:15 (SSID='WiFinet' freq=2432 MHz)
Sep  5 11:01:01 asus kernel: [ 3392.320600] wlan0: authenticate with 00:19:7b:a4:f6:15
Sep  5 11:01:01 asus NetworkManager[961]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Sep  5 11:01:01 asus kernel: [ 3392.338183] wlan0: send auth to 00:19:7b:a4:f6:15 (try 1/3)
Sep  5 11:01:01 asus wpa_supplicant[1107]: wlan0: Trying to associate with 00:19:7b:a4:f6:15 (SSID='WiFinet' freq=2432 MHz)
Sep  5 11:01:01 asus kernel: [ 3392.339915] wlan0: authenticated
Sep  5 11:01:01 asus kernel: [ 3392.343791] wlan0: associate with 00:19:7b:a4:f6:15 (try 1/3)
Sep  5 11:01:01 asus NetworkManager[961]: <info> (wlan0): supplicant interface state: authenticating -> associating
Sep  5 11:01:01 asus wpa_supplicant[1107]: wlan0: Associated with 00:19:7b:a4:f6:15
Sep  5 11:01:01 asus wpa_supplicant[1107]: wlan0: WPA: Key negotiation completed with 00:19:7b:a4:f6:15 [PTK=CCMP GTK=CCMP]
Sep  5 11:01:01 asus wpa_supplicant[1107]: wlan0: CTRL-EVENT-CONNECTED - Connection to 00:19:7b:a4:f6:15 completed [id=0 id_str=]
Sep  5 11:01:01 asus kernel: [ 3392.348196] wlan0: RX AssocResp from 00:19:7b:a4:f6:15 (capab=0x431 status=0 aid=3)
Sep  5 11:01:01 asus kernel: [ 3392.348233] wlan0: associated
Sep  5 11:01:01 asus NetworkManager[961]: <info> (wlan0): supplicant interface state: associating -> completed
Sep  5 11:01:01 asus NetworkManager[961]: <info> (wlan0): roamed from BSSID (none) ((none)) to 00:19:7b:a4:f6:15 (WiFinet)
Sep  5 11:01:09 asus anacron[6929]: Anacron 2.3 started on 2015-09-05
Sep  5 11:01:09 asus anacron[6929]: Will run job `cron.daily' in 5 min.
Sep  5 11:01:09 asus anacron[6929]: Jobs will be executed sequentially
Sep  5 11:01:11 asus kernel: [ 3402.796056] init: anacron main process (6929) killed by TERM signal
Sep  5 11:01:11 asus kernel: [ 3403.035270] bbswitch: enabling discrete graphics
Sep  5 11:04:07 asus kernel: [ 3403.474260] PM: Syncing filesystems ... done.
Sep  5 11:04:07 asus kernel: [ 3403.609967] Freezing user space processes ... (elapsed 0.001 seconds) done.
Sep  5 11:04:07 asus kernel: [ 3403.611486] PM: Marking nosave pages: [mem 0x00058000-0x00058fff]
Sep  5 11:04:07 asus kernel: [ 3403.611488] PM: Marking nosave pages: [mem 0x0009e000-0x000fffff]
Sep  5 11:04:07 asus kernel: [ 3403.611491] PM: Marking nosave pages: [mem 0xb95c3000-0xb95c3fff]
Sep  5 11:04:07 asus kernel: [ 3403.611492] PM: Marking nosave pages: [mem 0xb95cb000-0xb95cbfff]
Sep  5 11:04:07 asus kernel: [ 3403.611494] PM: Marking nosave pages: [mem 0xb98d4000-0xb98dafff]
Sep  5 11:04:07 asus kernel: [ 3403.611495] PM: Marking nosave pages: [mem 0xba14c000-0xba3cffff]
Sep  5 11:04:07 asus kernel: [ 3403.611506] PM: Marking nosave pages: [mem 0xc98e3000-0xc9ae8fff]
Sep  5 11:04:07 asus kernel: [ 3403.611516] PM: Marking nosave pages: [mem 0xc9e0f000-0xcaffefff]
Sep  5 11:04:07 asus kernel: [ 3403.611589] PM: Marking nosave pages: [mem 0xcb000000-0xffffffff]
Sep  5 11:04:07 asus kernel: [ 3403.612308] PM: Basic memory bitmaps created
Sep  5 11:04:07 asus kernel: [ 3403.612882] PM: Preallocating image memory... done (allocated 627648 pages)
Sep  5 11:04:07 asus kernel: [ 3403.800440] PM: Allocated 2510592 kbytes in 0.18 seconds (13947.73 MB/s)
Sep  5 11:04:07 asus kernel: [ 3403.800442] Freezing remaining freezable tasks ... (elapsed 5.886 seconds) done.
Sep  5 11:04:07 asus kernel: [ 3409.690875] Suspending console(s) (use no_console_suspend to debug)
Sep  5 11:04:07 asus kernel: [ 3409.690929] wlan0: deauthenticating from 00:19:7b:a4:f6:15 by local choice (reason=3)
Sep  5 11:04:07 asus kernel: [ 3409.724526] cfg80211: Calling CRDA to update world regulatory domain
Sep  5 11:04:07 asus kernel: [ 3410.956315] PM: freeze of devices complete after 1264.658 msecs
Sep  5 11:04:07 asus kernel: [ 3410.956444] PM: late freeze of devices complete after 0.127 msecs
Sep  5 11:04:07 asus kernel: [ 3410.957024] PM: noirq freeze of devices complete after 0.579 msecs
Sep  5 11:04:07 asus kernel: [ 3410.957305] ACPI: Preparing to enter system sleep state S4
Sep  5 11:04:07 asus kernel: [ 3410.960784] PM: Saving platform NVS memory
Sep  5 11:04:07 asus kernel: [ 3410.969584] Disabling non-boot CPUs ...
Sep  5 11:04:07 asus kernel: [ 3410.970779] kvm: disabling virtualization on CPU1
Sep  5 11:04:07 asus kernel: [ 3411.071261] smpboot: CPU 1 is now offline
Sep  5 11:04:07 asus kernel: [ 3411.072680] kvm: disabling virtualization on CPU2
Sep  5 11:04:07 asus kernel: [ 3411.175323] smpboot: CPU 2 is now offline
Sep  5 11:04:07 asus kernel: [ 3411.176677] kvm: disabling virtualization on CPU3
Sep  5 11:04:07 asus kernel: [ 3411.279388] smpboot: CPU 3 is now offline
Sep  5 11:04:07 asus kernel: [ 3411.279757] PM: Creating hibernation image:
Sep  5 11:04:07 asus kernel: [ 3411.358941] PM: Need to copy 626716 pages
Sep  5 11:04:07 asus kernel: [ 3411.358942] PM: Normal pages needed: 626716 + 1024, available pages: 1440360
Sep  5 11:04:07 asus kernel: [ 3411.280664] PM: Restoring platform NVS memory
Sep  5 11:04:07 asus kernel: [ 3411.282747] Enabling non-boot CPUs ...
Sep  5 11:04:07 asus kernel: [ 3411.282776] x86: Booting SMP configuration:
Sep  5 11:04:07 asus kernel: [ 3411.282777] smpboot: Booting Node 0 Processor 1 APIC 0x2
Sep  5 11:04:07 asus kernel: [ 3411.294632] kvm: enabling virtualization on CPU1
Sep  5 11:04:07 asus kernel: [ 3411.296909] CPU1 is up
Sep  5 11:04:07 asus kernel: [ 3411.296921] smpboot: Booting Node 0 Processor 2 APIC 0x1
Sep  5 11:04:07 asus kernel: [ 3411.308767] kvm: enabling virtualization on CPU2
Sep  5 11:04:07 asus kernel: [ 3411.311090] CPU2 is up
Sep  5 11:04:07 asus kernel: [ 3411.311102] smpboot: Booting Node 0 Processor 3 APIC 0x3
Sep  5 11:04:07 asus kernel: [ 3411.323052] kvm: enabling virtualization on CPU3
Sep  5 11:04:07 asus kernel: [ 3411.325348] CPU3 is up
Sep  5 11:04:07 asus kernel: [ 3411.331428] ACPI: Waking up from system sleep state S4
Sep  5 11:04:07 asus kernel: [ 3411.370912] PM: noirq restore of devices complete after 32.027 msecs
Sep  5 11:04:07 asus kernel: [ 3411.371044] PM: early restore of devices complete after 0.112 msecs
Sep  5 11:04:07 asus kernel: [ 3411.452402] snd_hda_intel 0000:00:03.0: irq 59 for MSI/MSI-X
Sep  5 11:04:07 asus kernel: [ 3411.452451] usb usb1: root hub lost power or was reset
Sep  5 11:04:07 asus kernel: [ 3411.452452] usb usb2: root hub lost power or was reset
Sep  5 11:04:07 asus kernel: [ 3411.453237] xhci_hcd 0000:00:14.0: irq 61 for MSI/MSI-X
Sep  5 11:04:07 asus kernel: [ 3411.453289] mei_me 0000:00:16.0: irq 63 for MSI/MSI-X
Sep  5 11:04:07 asus kernel: [ 3411.453339] ath: phy0: ASPM enabled: 0x42
Sep  5 11:04:07 asus kernel: [ 3411.453380] snd_hda_intel 0000:00:1b.0: irq 64 for MSI/MSI-X
Sep  5 11:04:07 asus kernel: [ 3411.770817] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Sep  5 11:04:07 asus kernel: [ 3411.772457] ata1.00: configured for UDMA/133
Sep  5 11:04:07 asus kernel: [ 3411.782835] usb 1-5: reset high-speed USB device number 3 using xhci_hcd
Sep  5 11:04:07 asus kernel: [ 3411.786845] sd 0:0:0:0: [sda] Starting disk
Sep  5 11:04:07 asus kernel: [ 3411.848734] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88021f6e59c0
Sep  5 11:04:07 asus kernel: [ 3411.966990] usb 1-4: reset full-speed USB device number 7 using xhci_hcd
Sep  5 11:04:07 asus kernel: [ 3411.983327] usb 1-4: device firmware changed
Sep  5 11:04:07 asus kernel: [ 3412.919559] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
Sep  5 11:04:07 asus kernel: [ 3413.429807] PM: restore of devices complete after 1976.358 msecs
Sep  5 11:04:07 asus kernel: [ 3413.430021] PM: Image restored successfully.
Sep  5 11:04:07 asus kernel: [ 3413.430044] PM: Basic memory bitmaps freed
Sep  5 11:04:07 asus kernel: [ 3413.430112] usb 1-4: USB disconnect, device number 7
Sep  5 11:04:07 asus rtkit-daemon[2683]: The canary thread is apparently starving. Taking action.
Sep  5 11:04:07 asus rtkit-daemon[2683]: Demoting known real-time threads.
Sep  5 11:04:07 asus rtkit-daemon[2683]: Successfully demoted thread 2895 of process 2677 (n/a).
Sep  5 11:04:07 asus rtkit-daemon[2683]: Successfully demoted thread 2878 of process 2677 (n/a).
Sep  5 11:04:07 asus rtkit-daemon[2683]: Successfully demoted thread 2818 of process 2677 (n/a).
Sep  5 11:04:07 asus rtkit-daemon[2683]: Successfully demoted thread 2677 of process 2677 (n/a).
Sep  5 11:04:07 asus rtkit-daemon[2683]: Demoted 4 threads.
Sep  5 11:04:07 asus kernel: [ 3413.433520] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801f7d5e840
Sep  5 11:04:07 asus kernel: [ 3413.433524] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801f7d5e8c0
Sep  5 11:04:07 asus kernel: [ 3413.433526] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801f7d5e880
Sep  5 11:04:07 asus kernel: [ 3413.433528] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801f7f2afc0
Sep  5 11:04:07 asus kernel: [ 3413.433529] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801f7f2af80
Sep  5 11:04:07 asus bluetoothd[906]: Unregister path: /org/bluez/906/hci0
Sep  5 11:04:07 asus wpa_supplicant[1107]: wlan0: CTRL-EVENT-DISCONNECTED bssid=00:19:7b:a4:f6:15 reason=3 locally_generated=1
Sep  5 11:04:07 asus bluetoothd[906]: hci0: Set IO Capability (0x0018) failed: Invalid Index (0x11)
Sep  5 11:04:07 asus kernel: [ 3413.439709] cfg80211: World regulatory domain updated:
Sep  5 11:04:07 asus kernel: [ 3413.439713] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Sep  5 11:04:07 asus kernel: [ 3413.439715] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep  5 11:04:07 asus kernel: [ 3413.439716] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep  5 11:04:07 asus kernel: [ 3413.439718] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep  5 11:04:07 asus kernel: [ 3413.439720] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep  5 11:04:07 asus kernel: [ 3413.439721] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep  5 11:04:07 asus NetworkManager[961]: <info> (wlan0): roamed from BSSID 00:19:7b:a4:f6:15 (WiFinet) to (none) ((none))
Sep  5 11:04:07 asus NetworkManager[961]: <warn> Connection disconnected (reason -3)
Sep  5 11:04:07 asus NetworkManager[961]: <info> (wlan0): supplicant interface state: completed -> disconnected
Sep  5 11:04:07 asus kernel: [ 3413.430045] Restarting tasks ... done.
Sep  5 11:04:07 asus kernel: [ 3413.470410] video LNXVIDEO:00: Restoring backlight state
Sep  5 11:04:07 asus kernel: [ 3413.470415] video LNXVIDEO:01: Restoring backlight state
Sep  5 11:04:07 asus kernel: [ 3413.470420] bbswitch: disabling discrete graphics
Sep  5 11:04:07 asus kernel: [ 3413.470425] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
Sep  5 11:04:07 asus wpa_supplicant[1107]: wlan0: CTRL-EVENT-SCAN-STARTED 
Sep  5 11:04:07 asus NetworkManager[961]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Sep  5 11:04:07 asus anacron[8252]: Anacron 2.3 started on 2015-09-05
Sep  5 11:04:07 asus anacron[8252]: Will run job `cron.daily' in 5 min.
Sep  5 11:04:07 asus anacron[8252]: Jobs will be executed sequentially
Sep  5 11:04:07 asus kernel: [ 3413.599888] usb 1-4: new full-speed USB device number 8 using xhci_hcd
Sep  5 11:04:07 asus kernel: [ 3413.617217] usb 1-4: string descriptor 0 read error: -22
Sep  5 11:04:07 asus kernel: [ 3413.617223] usb 1-4: New USB device found, idVendor=13d3, idProduct=3393
Sep  5 11:04:07 asus kernel: [ 3413.617225] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Sep  5 11:04:07 asus kernel: [ 3413.654360] usb 1-4: USB disconnect, device number 8
Sep  5 11:04:07 asus kernel: [ 3413.704186] init: anacron main process (8252) killed by TERM signal
Sep  5 11:04:07 asus kernel: [ 3413.928207] usb 1-4: new full-speed USB device number 9 using xhci_hcd
Sep  5 11:04:07 asus kernel: [ 3413.946097] usb 1-4: string descriptor 0 read error: -22
Sep  5 11:04:07 asus kernel: [ 3413.946112] usb 1-4: New USB device found, idVendor=13d3, idProduct=3393
Sep  5 11:04:07 asus kernel: [ 3413.946117] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Sep  5 11:04:08 asus bluetoothd[906]: input-headset driver probe failed for device 78:CA:04:6B:89:AB
Sep  5 11:04:08 asus bluetoothd[906]: Unknown command complete for opcode 19
Sep  5 11:04:08 asus bluetoothd[906]: hci0: Set Discoverable (0x0006) failed: Not Powered (0x0f)
Sep  5 11:04:08 asus bluetoothd[906]: hci0: Set Powered (0x0005) failed: <unknown status> (0x12)
Sep  5 11:04:11 asus wpa_supplicant[1107]: wlan0: SME: Trying to authenticate with 00:19:7b:a4:f6:15 (SSID='WiFinet' freq=2432 MHz)
Sep  5 11:04:11 asus kernel: [ 3417.088876] wlan0: authenticate with 00:19:7b:a4:f6:15
Sep  5 11:04:11 asus NetworkManager[961]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Sep  5 11:04:11 asus wpa_supplicant[1107]: wlan0: Trying to associate with 00:19:7b:a4:f6:15 (SSID='WiFinet' freq=2432 MHz)
Sep  5 11:04:11 asus kernel: [ 3417.104309] wlan0: send auth to 00:19:7b:a4:f6:15 (try 1/3)
Sep  5 11:04:11 asus kernel: [ 3417.105949] wlan0: authenticated
Sep  5 11:04:11 asus NetworkManager[961]: <info> (wlan0): supplicant interface state: authenticating -> associating
Sep  5 11:04:11 asus kernel: [ 3417.110029] wlan0: associate with 00:19:7b:a4:f6:15 (try 1/3)
Sep  5 11:04:11 asus wpa_supplicant[1107]: wlan0: Associated with 00:19:7b:a4:f6:15
Sep  5 11:04:11 asus wpa_supplicant[1107]: wlan0: WPA: Key negotiation completed with 00:19:7b:a4:f6:15 [PTK=CCMP GTK=CCMP]
Sep  5 11:04:11 asus wpa_supplicant[1107]: wlan0: CTRL-EVENT-CONNECTED - Connection to 00:19:7b:a4:f6:15 completed [id=0 id_str=]
Sep  5 11:04:11 asus kernel: [ 3417.114376] wlan0: RX AssocResp from 00:19:7b:a4:f6:15 (capab=0x431 status=0 aid=3)
Sep  5 11:04:11 asus kernel: [ 3417.114413] wlan0: associated
Sep  5 11:04:11 asus NetworkManager[961]: <info> (wlan0): supplicant interface state: associating -> completed
Sep  5 11:04:11 asus NetworkManager[961]: <info> (wlan0): roamed from BSSID (none) ((none)) to 00:19:7b:a4:f6:15 (WiFinet)
Sep  5 11:07:10 asus wpa_supplicant[1107]: wlan0: WPA: Group rekeying completed with 00:19:7b:a4:f6:15 [GTK=CCMP]
Sep  5 11:12:50 asus dbus[845]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Sep  5 11:12:51 asus kernel: [ 3937.360102] systemd-hostnamed[1907]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
Sep  5 11:12:51 asus dbus[845]: [system] Successfully activated service 'org.freedesktop.hostname1'
Sep  5 11:17:01 asus CRON[13935]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

```

The battery status after the first wake up (it was taken during the 4 seconds time frame between the first wake up event and suspend to disk) and after the second.
```

~$ upower -i /org/freedesktop/UPower/devices/battery_BAT0
  native-path:          BAT0
  vendor:               ASUSTeK
  model:                UX3-44
  power supply:         yes
  updated:              &#1057;&#1073;. 05 &#1089;&#1077;&#1085;&#1090;. 2015 11:01:09 (178 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    [COLOR=#ff0000]state:               empty[/COLOR]
    energy:              0 Wh
    energy-empty:        0 Wh
    energy-full:         45,477 Wh
    energy-full-design:  50,103 Wh
    energy-rate:         0 W
    percentage:          0%
    capacity:            90,767%
    technology:          lithium-ion

~$ upower -i /org/freedesktop/UPower/devices/battery_BAT0
  native-path:          BAT0
  vendor:               ASUSTeK
  model:                UX3-44
  power supply:         yes
  updated:              &#1057;&#1073;. 05 &#1089;&#1077;&#1085;&#1090;. 2015 11:08:25 (10 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               discharging
    energy:              41,451 Wh
    energy-empty:        0 Wh
    energy-full:         45,477 Wh
    energy-full-design:  50,103 Wh
    energy-rate:         5,066 W
    voltage:             11,31 V
    time to empty:       8,2 hours
    percentage:          90%
    capacity:            90,767%
    technology:          lithium-ion
  History (rate):
    1441440505    5,066    discharging
    1441440475    5,496    discharging
    1441440445    5,179    discharging
    1441440415    11,038    discharging

```

---

### Post by RockTeam on 2015-10-28
So what is it more obviously looks like a configuration issue or a software bug?

---

