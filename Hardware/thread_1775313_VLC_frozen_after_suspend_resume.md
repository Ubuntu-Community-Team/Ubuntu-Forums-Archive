---
title: "VLC frozen after suspend resume"
date: 2011-06-04
forum: Hardware
---

### Post by joes3029 on 2011-06-04
It's not the end of the world, but it's bugging the hell out of me. If I tell VLC to play a file and then suspend the system, on resume VLC may play a frame of the file it was playing (off of the local drive) but will then seem to pause - it'll tell me it's playing, but it's only by pausing it and telling it to play again that it will resume. I've set the logging as high as possible, and I've done tail -f's on /var/log/syslog and the VLC.log to no avail - VLC doesn't show any indication of knowing it's being suspended, and syslog doesn't show anything out of the usual either. In every other respect the systems resumes happily. 

I've set VLC verbosity for logging to 20, and only see this in the log:[INDENT]'main debug: VoutDisplayEvent 'resize' 427x288 window
main debug: auto hidding mouse
xcb_xv debug: display is visible
main warning: late picture skipped (3539399 > -21)
main warning: late picture skipped (3619399 > -21)
main warning: late picture skipped (3579399 > -21)
main warning: late picture skipped (3419399 > -21)
main warning: late picture skipped (3499399 > -21)
main warning: late picture skipped (3459399 > -21)
main warning: late picture skipped (3299399 > -21)
main warning: late picture skipped (3379399 > -21)
main warning: late picture skipped (3339399 > -21)
main warning: late picture skipped (3179399 > -21)
main warning: late picture skipped (3259399 > -21)
main warning: late picture skipped (3219399 > -21)
main warning: late picture skipped (3139399 > -21)
main warning: late picture skipped (3899399 > -21)
main warning: late picture skipped (3939399 > -21)
main warning: late picture skipped (3779399 > -21)
main warning: late picture skipped (3859399 > -21)
main warning: late picture skipped (3819399 > -21)
main warning: late picture skipped (3659399 > -21)
main warning: late picture skipped (3739399 > -21)
main warning: late picture skipped (3699399 > -21)
main warning: late picture skipped (3113933 > -21)
main warning: late picture skipped (3075731 > -21)
main debug: audio output is too slow (5459544), trashing 100000us
main debug: audio output is too slow (5359690), trashing 100000us
main debug: audio output is too slow (5259763), trashing 100000us
main debug: audio output is too slow (5159813), trashing 100000us
main debug: audio output is too slow (5059876), trashing 100000us
main debug: audio output is too slow (4959933), trashing 100000us'
[/INDENT]/var/log/syslog mostly just gives details of network events when the system comes back up (apologies for the wall of text):
[INDENT]Jun  4 20:33:28 insite NetworkManager[455]: <info> (eth0): carrier now OFF (device state 1)
Jun  4 20:33:29 insite anacron[9764]: Anacron 2.3 started on 2011-06-04
Jun  4 20:33:29 insite anacron[9764]: Normal exit (0 jobs run)
Jun  4 20:33:29 insite kernel: [ 4469.036937] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Jun  4 20:33:30 insite kernel: [ 4470.541271] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
Jun  4 20:33:30 insite kernel: [ 4470.541285] PM: Basic memory bitmaps created
Jun  4 20:34:38 insite kernel: [ 4470.541291] PM: Syncing filesystems ... done.
Jun  4 20:34:38 insite kernel: [ 4470.566199] Freezing user space processes ... (elapsed 0.01 seconds) done.
Jun  4 20:34:38 insite kernel: [ 4470.584116] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
Jun  4 20:34:38 insite kernel: [ 4470.600147] PM: Preallocating image memory... done (allocated 187768 pages)
Jun  4 20:34:38 insite kernel: [ 4470.815328] PM: Allocated 751072 kbytes in 0.21 seconds (3576.53 MB/s)
Jun  4 20:34:38 insite kernel: [ 4470.815334] Suspending console(s) (use no_console_suspend to debug)
Jun  4 20:34:38 insite kernel: [ 4470.815769] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Jun  4 20:34:38 insite kernel: [ 4470.816714] parport_pc 00:08: disabled
Jun  4 20:34:38 insite kernel: [ 4470.817135] serial 00:07: disabled
Jun  4 20:34:38 insite kernel: [ 4470.817550] serial 00:06: disabled
Jun  4 20:34:38 insite kernel: [ 4470.817706] e100 0000:02:08.0: PME# enabled
Jun  4 20:34:38 insite kernel: [ 4470.818256] pci 0000:00:1e.0: wake-up capability enabled by ACPI
Jun  4 20:34:38 insite kernel: [ 4470.818313] ata_piix 0000:00:1f.2: PCI INT B disabled
Jun  4 20:34:38 insite kernel: [ 4470.920154] HDA Intel 0000:00:1b.0: PCI INT A disabled
Jun  4 20:34:38 insite kernel: [ 4470.920185] ACPI handle has no context!
Jun  4 20:34:38 insite kernel: [ 4470.936029] PM: freeze of drv:HDA Intel dev:0000:00:1b.0 complete after 118.238 msecs
Jun  4 20:34:38 insite kernel: [ 4470.936053] PM: freeze of drv: dev:pci0000:00 complete after 118.232 msecs
Jun  4 20:34:38 insite kernel: [ 4470.936076] PM: freeze of devices complete after 120.482 msecs
Jun  4 20:34:38 insite kernel: [ 4470.936526] PM: late freeze of devices complete after 0.443 msecs
Jun  4 20:34:38 insite kernel: [ 4470.936563] ACPI: Preparing to enter system sleep state S4
Jun  4 20:34:38 insite kernel: [ 4471.978663] PM: Saving platform NVS memory
Jun  4 20:34:38 insite kernel: [ 4471.980513] Disabling non-boot CPUs ...
Jun  4 20:34:38 insite kernel: [ 4471.989667] CPU 1 is now offline
Jun  4 20:34:38 insite kernel: [ 4472.156026] CPU 2 is now offline
Jun  4 20:34:38 insite kernel: [ 4472.188076] Broke affinity for irq 1
Jun  4 20:34:38 insite kernel: [ 4472.292019] CPU 3 is now offline
Jun  4 20:34:38 insite kernel: [ 4472.292530] Extended CMOS year: 2000
Jun  4 20:34:38 insite kernel: [ 4472.292611] PM: Creating hibernation image:
Jun  4 20:34:38 insite kernel: [ 4472.296007] PM: Need to copy 186822 pages
Jun  4 20:34:38 insite kernel: [ 4472.296007] PM: Normal pages needed: 50514 + 1024, available pages: 198338
Jun  4 20:34:38 insite kernel: [ 4472.296007] PM: Restoring platform NVS memory
Jun  4 20:34:38 insite kernel: [ 4472.296007] Extended CMOS year: 2000
Jun  4 20:34:38 insite kernel: [ 4472.296007] Enabling non-boot CPUs ...
Jun  4 20:34:38 insite kernel: [ 4472.296007] Booting Node 0 Processor 1 APIC 0x2
Jun  4 20:34:38 insite kernel: [ 4471.989657] Initializing CPU#1
Jun  4 20:34:38 insite kernel: [ 4472.400701] CPU1 is up
Jun  4 20:34:38 insite kernel: [ 4472.400878] Booting Node 0 Processor 2 APIC 0x1
Jun  4 20:34:38 insite kernel: [ 4472.404020] Switched to NOHz mode on CPU #1
Jun  4 20:34:38 insite kernel: [ 4472.053311] Initializing CPU#2
Jun  4 20:34:38 insite kernel: [ 4472.508929] CPU2 is up
Jun  4 20:34:38 insite kernel: [ 4472.509120] Booting Node 0 Processor 3 APIC 0x3
Jun  4 20:34:38 insite kernel: [ 4472.512017] Switched to NOHz mode on CPU #2
Jun  4 20:34:38 insite kernel: [ 4472.189158] Initializing CPU#3
Jun  4 20:34:38 insite kernel: [ 4472.624023] Switched to NOHz mode on CPU #3
Jun  4 20:34:38 insite kernel: [ 4472.629146] CPU3 is up
Jun  4 20:34:38 insite kernel: [ 4472.630563] ACPI: Waking up from system sleep state S4
Jun  4 20:34:38 insite kernel: [ 4472.631052] i915 0000:00:02.0: restoring config space at offset 0x1 (was 0x900007, writing 0x900407)
Jun  4 20:34:38 insite kernel: [ 4472.631111] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
Jun  4 20:34:38 insite kernel: [ 4472.631362] ata_piix 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00003, writing 0x2b00007)
Jun  4 20:34:38 insite kernel: [ 4472.644039] e100 0000:02:08.0: BAR 0: set to [mem 0xfebff000-0xfebfffff] (PCI address [0xfebff000-0xfebfffff])
Jun  4 20:34:38 insite kernel: [ 4472.644049] e100 0000:02:08.0: BAR 1: set to [io  0xec00-0xec3f] (PCI address [0xec00-0xec3f])
Jun  4 20:34:38 insite kernel: [ 4472.644063] e100 0000:02:08.0: restoring config space at offset 0xf (was 0x38080100, writing 0x3808010b)
Jun  4 20:34:38 insite kernel: [ 4472.644083] e100 0000:02:08.0: restoring config space at offset 0x3 (was 0x0, writing 0x4008)
Jun  4 20:34:38 insite kernel: [ 4472.644092] e100 0000:02:08.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900017)
Jun  4 20:34:38 insite kernel: [ 4472.644227] PM: early restore of devices complete after 13.232 msecs
Jun  4 20:34:38 insite kernel: [ 4472.748611] i915 0000:00:02.0: setting latency timer to 64
Jun  4 20:34:38 insite kernel: [ 4472.748837] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun  4 20:34:38 insite kernel: [ 4472.748848] HDA Intel 0000:00:1b.0: setting latency timer to 64
Jun  4 20:34:38 insite kernel: [ 4472.748882] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Jun  4 20:34:38 insite kernel: [ 4472.748917] HDA Intel 0000:00:1b.0: irq 42 for MSI/MSI-X
Jun  4 20:34:38 insite kernel: [ 4472.748927] usb usb2: root hub lost power or was reset
Jun  4 20:34:38 insite kernel: [ 4472.748947] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Jun  4 20:34:38 insite kernel: [ 4472.748986] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Jun  4 20:34:38 insite kernel: [ 4472.748994] usb usb3: root hub lost power or was reset
Jun  4 20:34:38 insite kernel: [ 4472.749013] uhci_hcd 0000:00:1d.3: setting latency timer to 64
Jun  4 20:34:38 insite kernel: [ 4472.749032] usb usb4: root hub lost power or was reset
Jun  4 20:34:38 insite kernel: [ 4472.749056] usb usb5: root hub lost power or was reset
Jun  4 20:34:38 insite kernel: [ 4472.749060] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Jun  4 20:34:38 insite kernel: [ 4472.749081] pci 0000:00:1e.0: setting latency timer to 64
Jun  4 20:34:38 insite kernel: [ 4472.749096] usb usb1: root hub lost power or was reset
Jun  4 20:34:38 insite kernel: [ 4472.749136] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jun  4 20:34:38 insite kernel: [ 4472.749148] ata_piix 0000:00:1f.2: setting latency timer to 64
Jun  4 20:34:38 insite kernel: [ 4472.749208] pci 0000:00:1e.0: wake-up capability disabled by ACPI
Jun  4 20:34:38 insite kernel: [ 4472.749221] e100 0000:02:08.0: PME# disabled
Jun  4 20:34:38 insite kernel: [ 4472.752995] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Jun  4 20:34:38 insite kernel: [ 4472.753338] sd 0:0:0:0: [sda] Starting disk
Jun  4 20:34:38 insite kernel: [ 4472.753550] serial 00:06: activated
Jun  4 20:34:38 insite kernel: [ 4472.759964] serial 00:07: activated
Jun  4 20:34:38 insite kernel: [ 4472.762405] parport_pc 00:08: activated
Jun  4 20:34:38 insite kernel: [ 4472.840092] No ACPI video bus found
Jun  4 20:34:38 insite kernel: [ 4472.872063] PM: restore of drv:usb dev:usb4 complete after 118.834 msecs
Jun  4 20:34:38 insite kernel: [ 4472.872085] PM: restore of drv:hub dev:4-0:1.0 complete after 118.843 msecs
Jun  4 20:34:38 insite kernel: [ 4472.872095] PM: restore of drv: dev:ep_00 complete after 118.829 msecs
Jun  4 20:34:38 insite kernel: [ 4472.872104] PM: restore of drv:usb dev:usb5 complete after 118.830 msecs
Jun  4 20:34:38 insite kernel: [ 4472.872111] PM: restore of drv: dev:ep_81 complete after 118.855 msecs
Jun  4 20:34:38 insite kernel: [ 4472.872186] PM: restore of drv:hub dev:5-0:1.0 complete after 118.896 msecs
Jun  4 20:34:38 insite kernel: [ 4472.872194] PM: restore of drv: dev:ep_00 complete after 118.883 msecs
Jun  4 20:34:38 insite kernel: [ 4472.872208] PM: restore of drv: dev:ep_81 complete after 118.911 msecs
Jun  4 20:34:38 insite kernel: [ 4472.924151] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
Jun  4 20:34:38 insite kernel: [ 4472.924159] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
Jun  4 20:34:38 insite kernel: [ 4472.924241] ata1.00: ACPI cmd c6/00:10:00:00:00:a0 (SET MULTIPLE MODE) succeeded
Jun  4 20:34:38 insite kernel: [ 4472.924249] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
Jun  4 20:34:38 insite kernel: [ 4472.940228] ata1.00: configured for UDMA/133
Jun  4 20:34:38 insite kernel: [ 4472.940435] PM: restore of drv:sd dev:0:0:0:0 complete after 187.104 msecs
Jun  4 20:34:38 insite kernel: [ 4472.940454] PM: restore of drv:scsi_device dev:0:0:0:0 complete after 187.121 msecs
Jun  4 20:34:38 insite kernel: [ 4472.940464] PM: restore of drv:scsi_disk dev:0:0:0:0 complete after 177.685 msecs
Jun  4 20:34:38 insite kernel: [ 4472.976029] PM: restore of drv:usb dev:usb3 complete after 222.862 msecs
Jun  4 20:34:38 insite kernel: [ 4472.976037] PM: restore of drv:usb dev:usb2 complete after 222.956 msecs
Jun  4 20:34:38 insite kernel: [ 4472.976054] PM: restore of drv:hub dev:3-0:1.0 complete after 222.878 msecs
Jun  4 20:34:38 insite kernel: [ 4472.976064] PM: restore of drv:hub dev:2-0:1.0 complete after 222.943 msecs
Jun  4 20:34:38 insite kernel: [ 4472.976097] PM: restore of drv: dev:ep_81 complete after 222.912 msecs
Jun  4 20:34:38 insite kernel: [ 4472.976104] PM: restore of drv: dev:ep_00 complete after 222.909 msecs
Jun  4 20:34:38 insite kernel: [ 4472.976113] PM: restore of drv: dev:ep_00 complete after 222.958 msecs
Jun  4 20:34:38 insite kernel: [ 4472.976137] PM: restore of drv: dev:ep_81 complete after 222.995 msecs
Jun  4 20:34:38 insite kernel: [ 4473.004049] PM: restore of drv:usb dev:usb1 complete after 254.709 msecs
Jun  4 20:34:38 insite kernel: [ 4473.004076] PM: restore of drv:hub dev:1-0:1.0 complete after 251.055 msecs
Jun  4 20:34:38 insite kernel: [ 4473.004096] PM: restore of drv: dev:ep_81 complete after 251.065 msecs
Jun  4 20:34:38 insite kernel: [ 4473.004103] PM: restore of drv: dev:ep_00 complete after 251.057 msecs
Jun  4 20:34:38 insite kernel: [ 4473.264030] usb 3-1: reset low speed USB device using uhci_hcd and address 2
Jun  4 20:34:38 insite kernel: [ 4473.571199] PM: restore of drv:usb dev:3-1 complete after 817.762 msecs
Jun  4 20:34:38 insite kernel: [ 4473.571220] PM: restore of drv:usbhid dev:3-1:1.0 complete after 817.774 msecs
Jun  4 20:34:38 insite kernel: [ 4473.571228] PM: restore of drv: dev:ep_00 complete after 817.764 msecs
Jun  4 20:34:38 insite kernel: [ 4473.571241] PM: restore of drv: dev:ep_81 complete after 817.786 msecs
Jun  4 20:34:38 insite kernel: [ 4473.812024] usb 2-1: reset low speed USB device using uhci_hcd and address 2
Jun  4 20:34:38 insite kernel: [ 4474.119108] PM: restore of drv:usb dev:2-1 complete after 1365.766 msecs
Jun  4 20:34:38 insite kernel: [ 4474.119129] PM: restore of drv:usbhid dev:2-1:1.0 complete after 1365.732 msecs
Jun  4 20:34:38 insite kernel: [ 4474.119151] PM: restore of drv: dev:ep_81 complete after 1365.747 msecs
Jun  4 20:34:38 insite kernel: [ 4474.119163] PM: restore of drv: dev:ep_00 complete after 1365.744 msecs
Jun  4 20:34:38 insite kernel: [ 4474.119170] PM: restore of drv:generic-usb dev:0003:15D9:0A41.0001 complete after 1178.679 msecs
Jun  4 20:34:38 insite kernel: [ 4474.119267] PM: restore of devices complete after 1370.718 msecs
Jun  4 20:34:38 insite kernel: [ 4474.119548] PM: Image restored successfully.
Jun  4 20:34:38 insite kernel: [ 4474.119552] Restarting tasks ... done.
Jun  4 20:34:38 insite kernel: [ 4474.121915] PM: Basic memory bitmaps freed
Jun  4 20:34:38 insite acpid: client 851[0:0] has disconnected
Jun  4 20:34:38 insite acpid: client connected from 851[0:0]
Jun  4 20:34:38 insite acpid: 1 client rule loaded
Jun  4 20:34:38 insite kernel: [ 4474.139842] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
Jun  4 20:34:38 insite kernel: [ 4474.139861] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
Jun  4 20:34:38 insite anacron[10042]: Anacron 2.3 started on 2011-06-04
Jun  4 20:34:38 insite anacron[10042]: Normal exit (0 jobs run)
Jun  4 20:34:38 insite NetworkManager[455]: <info> wake requested (sleeping: yes  enabled: yes)
Jun  4 20:34:38 insite NetworkManager[455]: <info> waking up and re-enabling...
Jun  4 20:34:38 insite NetworkManager[455]: <info> (eth0): now managed
Jun  4 20:34:38 insite NetworkManager[455]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Jun  4 20:34:38 insite NetworkManager[455]: <info> (eth0): bringing up device.
Jun  4 20:34:38 insite NetworkManager[455]: <info> (eth0): preparing device.
Jun  4 20:34:38 insite NetworkManager[455]: <info> (eth0): deactivating device (reason: 2).
Jun  4 20:34:38 insite kernel: [ 4474.286927] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun  4 20:34:39 insite anacron[10183]: Anacron 2.3 started on 2011-06-04
Jun  4 20:34:39 insite anacron[10183]: Normal exit (0 jobs run)
Jun  4 20:34:39 insite kernel: [ 4475.057122] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Jun  4 20:34:41 insite NetworkManager[455]: <info> (eth0): carrier now ON (device state 2)
Jun  4 20:34:41 insite NetworkManager[455]: <info> (eth0): device state change: 2 -> 3 (reason 40)
Jun  4 20:34:41 insite kernel: [ 4476.984167] e100 0000:02:08.0: eth0: NIC Link is Up 100 Mbps Full Duplex
Jun  4 20:34:41 insite kernel: [ 4476.984654] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jun  4 20:34:41 insite NetworkManager[455]: <info> Activation (eth0) starting connection 'Auto eth0'
Jun  4 20:34:41 insite NetworkManager[455]: <info> (eth0): device state change: 3 -> 4 (reason 0)
Jun  4 20:34:41 insite NetworkManager[455]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  4 20:34:41 insite NetworkManager[455]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jun  4 20:34:41 insite NetworkManager[455]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jun  4 20:34:41 insite NetworkManager[455]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jun  4 20:34:41 insite NetworkManager[455]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jun  4 20:34:41 insite NetworkManager[455]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Jun  4 20:34:41 insite NetworkManager[455]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jun  4 20:34:41 insite NetworkManager[455]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun  4 20:34:41 insite NetworkManager[455]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jun  4 20:34:41 insite NetworkManager[455]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jun  4 20:34:41 insite NetworkManager[455]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Jun  4 20:34:41 insite NetworkManager[455]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun  4 20:34:41 insite NetworkManager[455]: <info> dhclient started with pid 10206
Jun  4 20:34:41 insite NetworkManager[455]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jun  4 20:34:41 insite dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Jun  4 20:34:41 insite dhclient: Copyright 2004-2010 Internet Systems Consortium.
Jun  4 20:34:41 insite dhclient: All rights reserved.
Jun  4 20:34:41 insite dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jun  4 20:34:41 insite dhclient: 
Jun  4 20:34:41 insite NetworkManager[455]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jun  4 20:34:41 insite dhclient: Listening on LPF/eth0/00:30:18:af:33:ef
Jun  4 20:34:41 insite dhclient: Sending on   LPF/eth0/00:30:18:af:33:ef
Jun  4 20:34:41 insite dhclient: Sending on   Socket/fallback
Jun  4 20:34:41 insite dhclient: DHCPREQUEST of 10.0.0.101 on eth0 to 255.255.255.255 port 67
Jun  4 20:34:42 insite dhclient: DHCPACK of 10.0.0.101 from 10.0.0.2
Jun  4 20:34:42 insite dhclient: bound to 10.0.0.101 -- renewal in 38750 seconds.
Jun  4 20:34:42 insite NetworkManager[455]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Jun  4 20:34:42 insite NetworkManager[455]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jun  4 20:34:42 insite NetworkManager[455]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Jun  4 20:34:42 insite NetworkManager[455]: <info>   address 10.0.0.101
Jun  4 20:34:42 insite NetworkManager[455]: <info>   prefix 24 (255.255.255.0)
Jun  4 20:34:42 insite NetworkManager[455]: <info>   gateway 10.0.0.2
Jun  4 20:34:42 insite NetworkManager[455]: <info>   nameserver '10.0.0.2'
Jun  4 20:34:42 insite NetworkManager[455]: <info>   domain name 'domain.name'
Jun  4 20:34:42 insite NetworkManager[455]: <info> Scheduling stage 5
Jun  4 20:34:42 insite NetworkManager[455]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jun  4 20:34:42 insite NetworkManager[455]: <info> Done scheduling stage 5
Jun  4 20:34:42 insite NetworkManager[455]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Jun  4 20:34:42 insite NetworkManager[455]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Jun  4 20:34:42 insite avahi-daemon[456]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.0.0.101.
Jun  4 20:34:42 insite avahi-daemon[456]: New relevant interface eth0.IPv4 for mDNS.
Jun  4 20:34:42 insite avahi-daemon[456]: Registering new address record for 10.0.0.101 on eth0.IPv4.
Jun  4 20:34:42 insite avahi-daemon[456]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::230:18ff:feaf:33ef.
Jun  4 20:34:42 insite avahi-daemon[456]: New relevant interface eth0.IPv6 for mDNS.
Jun  4 20:34:42 insite avahi-daemon[456]: Registering new address record for fe80::230:18ff:feaf:33ef on eth0.*.
Jun  4 20:34:43 insite NetworkManager[455]: <info> (eth0): device state change: 7 -> 8 (reason 0)
Jun  4 20:34:43 insite NetworkManager[455]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Jun  4 20:34:43 insite NetworkManager[455]: <info> Activation (eth0) successful, device activated.
Jun  4 20:34:43 insite NetworkManager[455]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Jun  4 20:34:51 insite kernel: [ 4487.264019] eth0: no IPv6 routers present
[/INDENT]Ultimately, I think I'm (somehow) looking in the wrong place - this wasn't an issue for 10.04, it's only started with 11.04. For presentations this is important for me, but it's annoying me more because I'm sure if I could only get a better idea why this was happening I could try and find a way to fix it!

---

