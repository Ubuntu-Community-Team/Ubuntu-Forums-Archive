---
title: "Inspiron 6400 resuming with lid closed"
date: 2009-05-04
forum: Hardware
---

### Post by clconway on 2009-05-04
Since upgrading to Jaunty, my laptop has acquired the annoying habit of resuming from suspend with the lid closed, leading it to overheat and drain the battery. I had similar problems on Hardy and previous releases, but this never happened on Intrepid.

It doesn't happen every time and has a fairly high correlation with the laptop being in my backpack...  Obviously, I can't observe what happening to my laptop when it's inside my bag, but I've tried and failed to trigger a resume by fiddling with all of the externally visible buttons, including the lid latch.

I'm fairly certain that the status light "throbber" has come on in most of the cases when this has happened, indicating that the laptop has not simply failed to suspend. 

The system passes the [suspend/resume stress test]("https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting") with 100%.

I've reported this as [a bug in Launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/368704"), without much success as far as debugging goes. Some /var/log/messages dumps are attached to the bug.

I'm looking for advice on how to isolate this problem. If it's being caused by some malfunctioning hardware, how would I detect that? How can I isolate the signal that's causing the system to resume from suspend? Or, if the problem is a failure to suspend, how can I isolate the component that is aborting that process? Is it possible for the system to fail to suspend, but still enable the "throbber" status light?

---

### Post by clconway on 2009-05-05
This happened again this morning. Here are the logs. The lid was closed from around 10:30 to around 12:20.

```
May  5 10:07:52 wagstaff -- MARK --
May  5 10:19:51 wagstaff kernel: [207219.692094] usb 1-1: new high speed USB device using ehci_hcd and address 14
May  5 10:19:51 wagstaff kernel: [207219.826126] usb 1-1: configuration #1 chosen from 2 choices
May  5 10:19:51 wagstaff kernel: [207219.833424] scsi7 : SCSI emulation for USB Mass Storage devices
May  5 10:19:56 wagstaff kernel: [207224.838741] scsi 7:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
May  5 10:19:56 wagstaff kernel: [207224.866743] sd 7:0:0:0: [sdb] 1946049 4096-byte hardware sectors: (7.97 GB/7.42 GiB)
May  5 10:19:56 wagstaff kernel: [207224.867437] sd 7:0:0:0: [sdb] Write Protect is off
May  5 10:19:56 wagstaff kernel: [207224.869944] sd 7:0:0:0: [sdb] 1946049 4096-byte hardware sectors: (7.97 GB/7.42 GiB)
May  5 10:19:56 wagstaff kernel: [207224.870571] sd 7:0:0:0: [sdb] Write Protect is off
May  5 10:19:56 wagstaff kernel: [207224.870590]  sdb: sdb1
May  5 10:19:56 wagstaff kernel: [207224.873605] sd 7:0:0:0: [sdb] Attached SCSI removable disk
May  5 10:19:56 wagstaff kernel: [207224.873735] sd 7:0:0:0: Attached scsi generic sg2 type 0
May  5 10:30:28 wagstaff kernel: [207856.713447] usb 1-1: USB disconnect, address 14
May  5 10:30:51 wagstaff kernel: [207879.245242] b44: eth0: powering down PHY
May  5 11:12:28 wagstaff kernel: [207882.030619] PM: Syncing filesystems ... done.
May  5 11:12:28 wagstaff kernel: [207882.043417] Freezing user space processes ... (elapsed 0.00 seconds) done.
May  5 11:12:28 wagstaff kernel: [207882.045225] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
May  5 11:12:28 wagstaff kernel: [207882.045307] Suspending console(s) (use no_console_suspend to debug)
May  5 11:12:28 wagstaff kernel: [207882.540279] sd 0:0:0:0: [sda] Synchronizing SCSI cache
May  5 11:12:28 wagstaff kernel: [207882.540704] sd 0:0:0:0: [sda] Stopping disk
May  5 11:12:28 wagstaff kernel: [207882.862732] ricoh-mmc: Suspending.
May  5 11:12:28 wagstaff kernel: [207882.862741] ricoh-mmc: Controller is now re-enabled.
May  5 11:12:28 wagstaff kernel: [207882.862803] sdhci-pci 0000:03:01.1: PCI INT B disabled
May  5 11:12:28 wagstaff kernel: [207882.896097] b44 0000:03:00.0: PCI INT A disabled
May  5 11:12:28 wagstaff kernel: [207882.928075] NVRM: RmPowerManagement: 4
May  5 11:12:28 wagstaff kernel: [207884.363096] ata_piix 0000:00:1f.2: PCI INT B disabled
May  5 11:12:28 wagstaff kernel: [207884.376201] ehci_hcd 0000:00:1d.7: PCI INT A disabled
May  5 11:12:28 wagstaff kernel: [207884.392099] uhci_hcd 0000:00:1d.3: PCI INT D disabled
May  5 11:12:28 wagstaff kernel: [207884.392133] uhci_hcd 0000:00:1d.2: PCI INT C disabled
May  5 11:12:28 wagstaff kernel: [207884.392167] uhci_hcd 0000:00:1d.1: PCI INT B disabled
May  5 11:12:28 wagstaff kernel: [207884.392201] uhci_hcd 0000:00:1d.0: PCI INT A disabled
May  5 11:12:28 wagstaff kernel: [207884.408216] HDA Intel 0000:00:1b.0: PCI INT A disabled
May  5 11:12:28 wagstaff kernel: [207884.424165] PM: suspend devices took 2.380 seconds
May  5 11:12:28 wagstaff kernel: [207884.427911] ACPI: Preparing to enter system sleep state S3
May  5 11:12:28 wagstaff kernel: [207884.428258] Disabling non-boot CPUs ...
May  5 11:12:28 wagstaff kernel: [207884.528027] CPU 1 is now offline
May  5 11:12:28 wagstaff kernel: [207884.528031] SMP alternatives: switching to UP code
May  5 11:12:28 wagstaff kernel: [207884.685096] CPU1 is down
May  5 11:12:28 wagstaff kernel: [207884.685096] Enabling non-boot CPUs ...
May  5 11:12:28 wagstaff kernel: [207884.685096] SMP alternatives: switching to SMP code
May  5 11:12:28 wagstaff kernel: [207884.841808] Booting processor 1 APIC 0x1 ip 0x6000
May  5 11:12:28 wagstaff kernel: [207884.684517] Initializing CPU#1
May  5 11:12:28 wagstaff kernel: [207884.684517] Calibrating delay using timer specific routine.. 3990.16 BogoMIPS (lpj=7980338)
May  5 11:12:28 wagstaff kernel: [207884.684517] CPU: L1 I cache: 32K, L1 D cache: 32K
May  5 11:12:28 wagstaff kernel: [207884.684517] CPU: L2 cache: 2048K
May  5 11:12:28 wagstaff kernel: [207884.684517] CPU: Physical Processor ID: 0
May  5 11:12:28 wagstaff kernel: [207884.684517] CPU: Processor Core ID: 1
May  5 11:12:28 wagstaff kernel: [207884.932456] CPU1: Genuine Intel(R) CPU           T2500  @ 2.00GHz stepping 08
May  5 11:12:28 wagstaff kernel: [207884.936036] CPU1 is up
May  5 11:12:28 wagstaff kernel: [207884.936039] ACPI: Waking up from system sleep state S3
May  5 11:12:28 wagstaff kernel: [207885.020198] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
May  5 11:12:28 wagstaff kernel: [207885.020525] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
May  5 11:12:28 wagstaff kernel: [207885.020597] usb usb2: root hub lost power or was reset
May  5 11:12:28 wagstaff kernel: [207885.020621] uhci_hcd 0000:00:1d.1: enabling device (0000 -> 0001)
May  5 11:12:28 wagstaff kernel: [207885.020628] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
May  5 11:12:28 wagstaff kernel: [207885.020713] usb usb3: root hub lost power or was reset
May  5 11:12:28 wagstaff kernel: [207885.020735] uhci_hcd 0000:00:1d.2: enabling device (0000 -> 0001)
May  5 11:12:28 wagstaff kernel: [207885.020741] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
May  5 11:12:28 wagstaff kernel: [207885.020825] usb usb4: root hub lost power or was reset
May  5 11:12:28 wagstaff kernel: [207885.020846] uhci_hcd 0000:00:1d.3: enabling device (0000 -> 0001)
May  5 11:12:28 wagstaff kernel: [207885.020853] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
May  5 11:12:28 wagstaff kernel: [207885.020937] usb usb5: root hub lost power or was reset
May  5 11:12:28 wagstaff kernel: [207885.036098] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
May  5 11:12:28 wagstaff kernel: [207885.052150] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
May  5 11:12:28 wagstaff kernel: [207885.052427] NVRM: RmPowerManagement: 5
May  5 11:12:28 wagstaff kernel: [207885.052567] ata2.00: _GTF evaluation failed (AE 0x1001)
May  5 11:12:28 wagstaff kernel: [207885.636105] iwl3945 0000:0b:00.0: enabling device (0000 -> 0002)
May  5 11:12:28 wagstaff kernel: [207885.652096] b44 0000:03:00.0: enabling device (0000 -> 0002)
May  5 11:12:28 wagstaff kernel: [207885.652106] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
May  5 11:12:28 wagstaff kernel: [207885.740785] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[ecbfd800-ecbfdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
May  5 11:12:28 wagstaff kernel: [207885.760172] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
May  5 11:12:28 wagstaff kernel: [207885.761198] ricoh-mmc: Resuming.
May  5 11:12:28 wagstaff kernel: [207885.761210] ricoh-mmc: Controller is now disabled.
May  5 11:12:28 wagstaff kernel: [207885.761491] sd 0:0:0:0: [sda] Starting disk
May  5 11:12:28 wagstaff kernel: [207885.796526] ata2.00: configured for UDMA/33
May  5 11:12:28 wagstaff kernel: [207887.796401] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
May  5 11:12:28 wagstaff kernel: [207887.808853] ata1.00: configured for UDMA/133
May  5 11:12:28 wagstaff kernel: [207887.861370] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
May  5 11:12:28 wagstaff kernel: [207887.861408] sd 0:0:0:0: [sda] Write Protect is off
May  5 11:12:28 wagstaff kernel: [207887.861464] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  5 11:12:28 wagstaff kernel: [207888.500391] PM: resume devices took 3.560 seconds
May  5 11:12:28 wagstaff kernel: [207888.500465] Restarting tasks ... done.
May  5 11:12:28 wagstaff kernel: [207888.674597] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
May  5 11:12:36 wagstaff kernel: [207895.762595] ADDRCONF(NETDEV_UP): eth0: link is not ready
May  5 11:12:36 wagstaff kernel: [207897.279339] Registered led device: iwl-phy0:radio
May  5 11:12:36 wagstaff kernel: [207897.279419] Registered led device: iwl-phy0:assoc
May  5 11:12:36 wagstaff kernel: [207897.279453] Registered led device: iwl-phy0:RX
May  5 11:12:36 wagstaff kernel: [207897.279486] Registered led device: iwl-phy0:TX
May  5 11:12:37 wagstaff kernel: [207897.331563] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  5 11:29:20 wagstaff -- MARK --
May  5 11:49:20 wagstaff -- MARK --
May  5 12:09:20 wagstaff -- MARK --
May  5 12:23:24 wagstaff kernel: [212144.989199] b44: eth0: Link is up at 100 Mbps, full duplex.

```

---

### Post by clconway on 2009-05-05
Note also, the laptop gave every seeming of being suspended at 10:30. There are no "MARK" messages between 10:30 and 11:12.

---

### Post by clconway on 2009-05-05
Here's the syslog and kern.log for 10:30 to 11:12.

Note the first message at 11:12 in syslog is "acpid: client 3219[0:0] has disconnected".

syslog:
```
May  5 10:30:01 wagstaff /USR/SBIN/CRON[8164]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
May  5 10:30:28 wagstaff kernel: [207856.713447] usb 1-1: USB disconnect, address 14
May  5 10:30:50 wagstaff anacron[8433]: Anacron 2.3 started on 2009-05-05
May  5 10:30:50 wagstaff anacron[8433]: Normal exit (0 jobs run)
May  5 10:30:51 wagstaff NetworkManager: <info>  Sleeping... 
May  5 10:30:51 wagstaff NetworkManager: <info>  (eth0): now unmanaged 
May  5 10:30:51 wagstaff NetworkManager: <info>  (eth0): device state change: 2 -> 1 
May  5 10:30:51 wagstaff NetworkManager: <info>  (eth0): cleaning up... 
May  5 10:30:51 wagstaff NetworkManager: <info>  (eth0): taking down device. 
May  5 10:30:51 wagstaff kernel: [207879.245242] b44: eth0: powering down PHY
May  5 10:30:51 wagstaff NetworkManager: <info>  (wlan0): now unmanaged 
May  5 10:30:51 wagstaff NetworkManager: <info>  (wlan0): device state change: 8 -> 1 
May  5 10:30:51 wagstaff NetworkManager: <info>  (wlan0): deactivating device (reason: 37). 
May  5 10:30:51 wagstaff NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 29658 
May  5 10:30:51 wagstaff kernel: [207879.621945] wlan0: disassociating by local choice (reason=3)
May  5 10:30:51 wagstaff NetworkManager: <info>  (wlan0): removing resolv.conf from /sbin/resolvconf 
May  5 10:30:52 wagstaff NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess  
May  5 10:30:52 wagstaff NetworkManager: <info>  (wlan0): cleaning up... 
May  5 10:30:52 wagstaff NetworkManager: <info>  (wlan0): taking down device. 
May  5 10:30:53 wagstaff avahi-daemon[3277]: Withdrawing address record for 10.0.1.2 on wlan0.
May  5 10:30:53 wagstaff avahi-daemon[3277]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.0.1.2.
May  5 10:30:53 wagstaff avahi-daemon[3277]: Interface wlan0.IPv4 no longer relevant for mDNS.
May  5 10:30:53 wagstaff avahi-daemon[3277]: Withdrawing address record for fe80::218:deff:fe11:ebe4 on wlan0.
May  5 11:12:28 wagstaff acpid: client 3219[0:0] has disconnected 
May  5 11:12:28 wagstaff acpid: client 3219[0:0] has disconnected 
May  5 11:12:28 wagstaff kernel: [207882.030619] PM: Syncing filesystems ... done.
May  5 11:12:28 wagstaff kernel: [207882.043412] PM: Preparing system for mem sleep
May  5 11:12:28 wagstaff kernel: [207882.043417] Freezing user space processes ... (elapsed 0.00 seconds) done.
May  5 11:12:28 wagstaff kernel: [207882.045225] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
May  5 11:12:28 wagstaff kernel: [207882.045293] PM: Entering mem sleep
May  5 11:12:28 wagstaff kernel: [207882.045307] Suspending console(s) (use no_console_suspend to debug)
May  5 11:12:28 wagstaff kernel: [207882.540279] sd 0:0:0:0: [sda] Synchronizing SCSI cache
May  5 11:12:28 wagstaff kernel: [207882.540704] sd 0:0:0:0: [sda] Stopping disk
May  5 11:12:28 wagstaff kernel: [207882.862732] ricoh-mmc: Suspending.
May  5 11:12:28 wagstaff kernel: [207882.862741] ricoh-mmc: Controller is now re-enabled.
May  5 11:12:28 wagstaff kernel: [207882.862796] ACPI handle has no context!
May  5 11:12:28 wagstaff kernel: [207882.862803] sdhci-pci 0000:03:01.1: PCI INT B disabled
May  5 11:12:28 wagstaff kernel: [207882.862809] ACPI handle has no context!
May  5 11:12:28 wagstaff kernel: [207882.896097] b44 0000:03:00.0: PCI INT A disabled
May  5 11:12:28 wagstaff kernel: [207882.896103] ACPI handle has no context!
May  5 11:12:28 wagstaff kernel: [207882.928075] NVRM: RmPowerManagement: 4
May  5 11:12:28 wagstaff kernel: [207884.363096] ata_piix 0000:00:1f.2: PCI INT B disabled
May  5 11:12:28 wagstaff kernel: [207884.376201] ehci_hcd 0000:00:1d.7: PCI INT A disabled
May  5 11:12:28 wagstaff kernel: [207884.392099] uhci_hcd 0000:00:1d.3: PCI INT D disabled
May  5 11:12:28 wagstaff kernel: [207884.392133] uhci_hcd 0000:00:1d.2: PCI INT C disabled
May  5 11:12:28 wagstaff kernel: [207884.392167] uhci_hcd 0000:00:1d.1: PCI INT B disabled
May  5 11:12:28 wagstaff kernel: [207884.392201] uhci_hcd 0000:00:1d.0: PCI INT A disabled
May  5 11:12:28 wagstaff kernel: [207884.408216] HDA Intel 0000:00:1b.0: PCI INT A disabled
May  5 11:12:28 wagstaff kernel: [207884.424165] PM: suspend devices took 2.380 seconds
May  5 11:12:28 wagstaff kernel: [207884.427911] ACPI: Preparing to enter system sleep state S3
May  5 11:12:28 wagstaff kernel: [207884.428258] Disabling non-boot CPUs ...
May  5 11:12:28 wagstaff kernel: [207884.528027] CPU 1 is now offline
May  5 11:12:28 wagstaff kernel: [207884.528031] SMP alternatives: switching to UP code
May  5 11:12:28 wagstaff kernel: [207884.684669] CPU0 attaching NULL sched-domain.
May  5 11:12:28 wagstaff kernel: [207884.684673] CPU1 attaching NULL sched-domain.
May  5 11:12:28 wagstaff kernel: [207884.684928] CPU0 attaching NULL sched-domain.
May  5 11:12:28 wagstaff kernel: [207884.685096] CPU1 is down
May  5 11:12:28 wagstaff kernel: [207884.685096] Back to C!
May  5 11:12:28 wagstaff kernel: [207884.685096] Enabling non-boot CPUs ...
May  5 11:12:28 wagstaff kernel: [207884.685096] SMP alternatives: switching to SMP code
May  5 11:12:28 wagstaff kernel: [207884.841808] Booting processor 1 APIC 0x1 ip 0x6000
May  5 11:12:28 wagstaff kernel: [207884.684517] Initializing CPU#1
May  5 11:12:28 wagstaff kernel: [207884.684517] Calibrating delay using timer specific routine.. 3990.16 BogoMIPS (lpj=7980338)
May  5 11:12:28 wagstaff kernel: [207884.684517] CPU: L1 I cache: 32K, L1 D cache: 32K
May  5 11:12:28 wagstaff kernel: [207884.684517] CPU: L2 cache: 2048K
May  5 11:12:28 wagstaff kernel: [207884.684517] CPU: Physical Processor ID: 0
May  5 11:12:28 wagstaff kernel: [207884.684517] CPU: Processor Core ID: 1
May  5 11:12:28 wagstaff kernel: [207884.932456] CPU1: Genuine Intel(R) CPU           T2500  @ 2.00GHz stepping 08
May  5 11:12:28 wagstaff kernel: [207884.932527] CPU0 attaching NULL sched-domain.
May  5 11:12:28 wagstaff kernel: [207884.933163] CPU0 attaching sched-domain:
May  5 11:12:28 wagstaff kernel: [207884.933166]  domain 0: span 0-1 level MC
May  5 11:12:28 wagstaff kernel: [207884.933168]   groups: 0 1
May  5 11:12:28 wagstaff kernel: [207884.933173] CPU1 attaching sched-domain:
May  5 11:12:28 wagstaff kernel: [207884.933175]  domain 0: span 0-1 level MC
May  5 11:12:28 wagstaff kernel: [207884.933176]   groups: 1 0
May  5 11:12:28 wagstaff kernel: [207884.936024] Switched to high resolution mode on CPU 1
May  5 11:12:28 wagstaff kernel: [207884.936036] CPU1 is up
May  5 11:12:28 wagstaff kernel: [207884.936039] ACPI: Waking up from system sleep state S3
May  5 11:12:28 wagstaff kernel: [207885.004272] pcieport-driver 0000:00:01.0: restoring config space at offset 0xf (was 0x100, writing 0x1a0100)
May  5 11:12:28 wagstaff kernel: [207885.004279] pcieport-driver 0000:00:01.0: restoring config space at offset 0xa (was 0xf, writing 0x0)
May  5 11:12:28 wagstaff kernel: [207885.004523] pcieport-driver 0000:00:01.0: restoring config space at offset 0x9 (was 0x1fff1, writing 0xdff1d001)
May  5 11:12:28 wagstaff kernel: [207885.004528] pcieport-driver 0000:00:01.0: restoring config space at offset 0x8 (was 0xfff0, writing 0xefe0ed00)
May  5 11:12:28 wagstaff kernel: [207885.004532] pcieport-driver 0000:00:01.0: restoring config space at offset 0x7 (was 0xf0, writing 0x200000f0)
May  5 11:12:28 wagstaff kernel: [207885.004536] pcieport-driver 0000:00:01.0: restoring config space at offset 0x6 (was 0x0, writing 0x10100)
May  5 11:12:28 wagstaff kernel: [207885.004542] pcieport-driver 0000:00:01.0: restoring config space at offset 0x3 (was 0x10000, writing 0x10010)
May  5 11:12:28 wagstaff kernel: [207885.004546] pcieport-driver 0000:00:01.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
May  5 11:12:28 wagstaff kernel: [207885.004567] pcieport-driver 0000:00:01.0: setting latency timer to 64
May  5 11:12:28 wagstaff kernel: [207885.020120] HDA Intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
May  5 11:12:28 wagstaff kernel: [207885.020147] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0xffa7c004, writing 0xefffc004)
May  5 11:12:28 wagstaff kernel: [207885.020156] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
May  5 11:12:28 wagstaff kernel: [207885.020167] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100102)
May  5 11:12:28 wagstaff kernel: [207885.020198] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
May  5 11:12:28 wagstaff kernel: [207885.020208] HDA Intel 0000:00:1b.0: setting latency timer to 64
May  5 11:12:28 wagstaff kernel: [207885.020247] pcieport-driver 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x20100)
May  5 11:12:28 wagstaff kernel: [207885.020265] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
May  5 11:12:28 wagstaff kernel: [207885.020274] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0xecf0ecf0)
May  5 11:12:28 wagstaff kernel: [207885.020283] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x7 (was 0x20000000, writing 0x200000f0)
May  5 11:12:28 wagstaff kernel: [207885.020292] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x6 (was 0x0, writing 0xb0b00)
May  5 11:12:28 wagstaff kernel: [207885.020305] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
May  5 11:12:28 wagstaff kernel: [207885.020316] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
May  5 11:12:28 wagstaff kernel: [207885.020368] pcieport-driver 0000:00:1c.0: setting latency timer to 64
May  5 11:12:28 wagstaff kernel: [207885.020392] pcieport-driver 0000:00:1c.3: restoring config space at offset 0xf (was 0x400, writing 0x20400)
May  5 11:12:28 wagstaff kernel: [207885.020410] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x9 (was 0x10001, writing 0xe011e001)
May  5 11:12:28 wagstaff kernel: [207885.020419] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x8 (was 0x0, writing 0xece0ecc0)
May  5 11:12:28 wagstaff kernel: [207885.020428] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x7 (was 0x0, writing 0xe0e0)
May  5 11:12:28 wagstaff kernel: [207885.020436] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x6 (was 0x0, writing 0xd0c00)
May  5 11:12:28 wagstaff kernel: [207885.020449] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
May  5 11:12:28 wagstaff kernel: [207885.020460] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
May  5 11:12:28 wagstaff kernel: [207885.020511] pcieport-driver 0000:00:1c.3: setting latency timer to 64
May  5 11:12:28 wagstaff kernel: [207885.020525] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
May  5 11:12:28 wagstaff kernel: [207885.020533] uhci_hcd 0000:00:1d.0: setting latency timer to 64
May  5 11:12:28 wagstaff kernel: [207885.020597] usb usb2: root hub lost power or was reset
May  5 11:12:28 wagstaff kernel: [207885.020621] uhci_hcd 0000:00:1d.1: enabling device (0000 -> 0001)
May  5 11:12:28 wagstaff kernel: [207885.020628] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
May  5 11:12:28 wagstaff kernel: [207885.020637] uhci_hcd 0000:00:1d.1: setting latency timer to 64
May  5 11:12:28 wagstaff kernel: [207885.020647] uhci_hcd 0000:00:1d.1: restoring config space at offset 0xf (was 0x200, writing 0x20b)
May  5 11:12:28 wagstaff kernel: [207885.020667] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x8 (was 0x1, writing 0xbf61)
May  5 11:12:28 wagstaff kernel: [207885.020713] usb usb3: root hub lost power or was reset
May  5 11:12:28 wagstaff kernel: [207885.020735] uhci_hcd 0000:00:1d.2: enabling device (0000 -> 0001)
May  5 11:12:28 wagstaff kernel: [207885.020741] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
May  5 11:12:28 wagstaff kernel: [207885.020750] uhci_hcd 0000:00:1d.2: setting latency timer to 64
May  5 11:12:28 wagstaff kernel: [207885.020760] uhci_hcd 0000:00:1d.2: restoring config space at offset 0xf (was 0x300, writing 0x309)
May  5 11:12:28 wagstaff kernel: [207885.020779] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x8 (was 0x1, writing 0xbf41)
May  5 11:12:28 wagstaff kernel: [207885.020825] usb usb4: root hub lost power or was reset
May  5 11:12:28 wagstaff kernel: [207885.020846] uhci_hcd 0000:00:1d.3: enabling device (0000 -> 0001)
May  5 11:12:28 wagstaff kernel: [207885.020853] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
May  5 11:12:28 wagstaff kernel: [207885.020862] uhci_hcd 0000:00:1d.3: setting latency timer to 64
May  5 11:12:28 wagstaff kernel: [207885.020872] uhci_hcd 0000:00:1d.3: restoring config space at offset 0xf (was 0x400, writing 0x407)
May  5 11:12:28 wagstaff kernel: [207885.020891] uhci_hcd 0000:00:1d.3: restoring config space at offset 0x8 (was 0x1, writing 0xbf21)
May  5 11:12:28 wagstaff kernel: [207885.020937] usb usb5: root hub lost power or was reset
May  5 11:12:28 wagstaff kernel: [207885.036098] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
May  5 11:12:28 wagstaff kernel: [207885.036106] ehci_hcd 0000:00:1d.7: setting latency timer to 64
May  5 11:12:28 wagstaff kernel: [207885.036189] pci 0000:00:1e.0: restoring config space at offset 0x9 (was 0x100f1, writing 0x1fff1)
May  5 11:12:28 wagstaff kernel: [207885.036197] pci 0000:00:1e.0: restoring config space at offset 0x8 (was 0xb0, writing 0xecb0ecb0)
May  5 11:12:28 wagstaff kernel: [207885.036206] pci 0000:00:1e.0: restoring config space at offset 0x7 (was 0x2280e0f0, writing 0x228000f0)
May  5 11:12:28 wagstaff kernel: [207885.036224] pci 0000:00:1e.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100107)
May  5 11:12:28 wagstaff kernel: [207885.036246] pci 0000:00:1e.0: setting latency timer to 64
May  5 11:12:28 wagstaff kernel: [207885.036296] pci 0000:00:1f.0: restoring config space at offset 0x1 (was 0x2100007, writing 0x2100107)
May  5 11:12:28 wagstaff kernel: [207885.052104] ata_piix 0000:00:1f.2: restoring config space at offset 0xf (was 0x200, writing 0x205)
May  5 11:12:28 wagstaff kernel: [207885.052150] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
May  5 11:12:28 wagstaff kernel: [207885.052157] ata_piix 0000:00:1f.2: setting latency timer to 64
May  5 11:12:28 wagstaff kernel: [207885.052186] pci 0000:00:1f.3: restoring config space at offset 0xf (was 0x200, writing 0x205)
May  5 11:12:28 wagstaff kernel: [207885.052227] pci 0000:00:1f.3: restoring config space at offset 0x1 (was 0x2800001, writing 0x2800101)
May  5 11:12:28 wagstaff kernel: [207885.052427] NVRM: RmPowerManagement: 5
May  5 11:12:28 wagstaff kernel: [207885.052567] ata2.00: _GTF evaluation failed (AE 0x1001)
May  5 11:12:28 wagstaff kernel: [207885.636105] iwl3945 0000:0b:00.0: enabling device (0000 -> 0002)
May  5 11:12:28 wagstaff kernel: [207885.636188] iwl3945 0000:0b:00.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
May  5 11:12:28 wagstaff kernel: [207885.636262] iwl3945 0000:0b:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xecfff000)
May  5 11:12:28 wagstaff kernel: [207885.636278] iwl3945 0000:0b:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
May  5 11:12:28 wagstaff kernel: [207885.636301] iwl3945 0000:0b:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100506)
May  5 11:12:28 wagstaff kernel: [207885.652096] b44 0000:03:00.0: enabling device (0000 -> 0002)
May  5 11:12:28 wagstaff kernel: [207885.652106] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
May  5 11:12:28 wagstaff kernel: [207885.652120] b44 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
May  5 11:12:28 wagstaff kernel: [207885.652147] b44 0000:03:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xecbfe000)
May  5 11:12:28 wagstaff kernel: [207885.652156] b44 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x4000)
May  5 11:12:28 wagstaff kernel: [207885.652166] b44 0000:03:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100106)
May  5 11:12:28 wagstaff kernel: [207885.688103] ohci1394 0000:03:01.0: restoring config space at offset 0xf (was 0x4020100, writing 0x4020103)
May  5 11:12:28 wagstaff kernel: [207885.688131] ohci1394 0000:03:01.0: restoring config space at offset 0x4 (was 0x0, writing 0xecbfd800)
May  5 11:12:28 wagstaff kernel: [207885.688140] ohci1394 0000:03:01.0: restoring config space at offset 0x3 (was 0x800000, writing 0x804000)
May  5 11:12:28 wagstaff kernel: [207885.688152] ohci1394 0000:03:01.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
May  5 11:12:28 wagstaff kernel: [207885.740785] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[ecbfd800-ecbfdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
May  5 11:12:28 wagstaff kernel: [207885.760103] sdhci-pci 0000:03:01.1: restoring config space at offset 0xf (was 0x200, writing 0x209)
May  5 11:12:28 wagstaff kernel: [207885.760131] sdhci-pci 0000:03:01.1: restoring config space at offset 0x4 (was 0x0, writing 0xecbfd400)
May  5 11:12:28 wagstaff kernel: [207885.760140] sdhci-pci 0000:03:01.1: restoring config space at offset 0x3 (was 0x800000, writing 0x804000)
May  5 11:12:28 wagstaff kernel: [207885.760151] sdhci-pci 0000:03:01.1: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
May  5 11:12:28 wagstaff kernel: [207885.760172] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
May  5 11:12:28 wagstaff kernel: [207885.761198] ricoh-mmc: Resuming.
May  5 11:12:28 wagstaff kernel: [207885.761210] ricoh-mmc: Controller is now disabled.
May  5 11:12:28 wagstaff kernel: [207885.761225] pci 0000:03:01.3: restoring config space at offset 0xf (was 0x200, writing 0x209)
May  5 11:12:28 wagstaff kernel: [207885.761253] pci 0000:03:01.3: restoring config space at offset 0x4 (was 0x0, writing 0xecbfd700)
May  5 11:12:28 wagstaff kernel: [207885.761265] pci 0000:03:01.3: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100102)
May  5 11:12:28 wagstaff kernel: [207885.761491] sd 0:0:0:0: [sda] Starting disk
May  5 11:12:28 wagstaff kernel: [207885.796526] ata2.00: configured for UDMA/33
May  5 11:12:28 wagstaff kernel: [207887.796401] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
May  5 11:12:28 wagstaff kernel: [207887.808853] ata1.00: configured for UDMA/133
May  5 11:12:28 wagstaff kernel: [207887.861370] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
May  5 11:12:28 wagstaff kernel: [207887.861408] sd 0:0:0:0: [sda] Write Protect is off
May  5 11:12:28 wagstaff kernel: [207887.861412] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
May  5 11:12:28 wagstaff kernel: [207887.861464] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  5 11:12:28 wagstaff kernel: [207888.500391] PM: resume devices took 3.560 seconds
May  5 11:12:28 wagstaff kernel: [207888.500462] PM: Finishing wakeup.
May  5 11:12:28 wagstaff kernel: [207888.500465] Restarting tasks ... done.
May  5 11:12:28 wagstaff kernel: [207888.674597] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
May  5 11:12:35 wagstaff acpid: client connected from 3219[0:0] 
May  5 11:12:36 wagstaff NetworkManager: <info>  Waking up... 
May  5 11:12:36 wagstaff NetworkManager: <info>  (eth0): now managed 
May  5 11:12:36 wagstaff NetworkManager: <info>  (eth0): device state change: 1 -> 2 
May  5 11:12:36 wagstaff NetworkManager: <info>  (eth0): bringing up device. 
May  5 11:12:36 wagstaff NetworkManager: <info>  (eth0): preparing device. 
May  5 11:12:36 wagstaff NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
May  5 11:12:36 wagstaff NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
May  5 11:12:36 wagstaff NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
May  5 11:12:36 wagstaff kernel: [207895.762595] ADDRCONF(NETDEV_UP): eth0: link is not ready
May  5 11:12:36 wagstaff NetworkManager: <info>  (wlan0): now managed 
May  5 11:12:36 wagstaff NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
May  5 11:12:36 wagstaff acpid: client connected from 3219[0:0] 
May  5 11:12:36 wagstaff NetworkManager: <info>  (wlan0): bringing up device. 
May  5 11:12:36 wagstaff kernel: [207897.279339] Registered led device: iwl-phy0:radio
May  5 11:12:36 wagstaff kernel: [207897.279419] Registered led device: iwl-phy0:assoc
May  5 11:12:36 wagstaff kernel: [207897.279453] Registered led device: iwl-phy0:RX
May  5 11:12:36 wagstaff kernel: [207897.279486] Registered led device: iwl-phy0:TX
May  5 11:12:37 wagstaff NetworkManager: <info>  (wlan0): preparing device. 
May  5 11:12:37 wagstaff NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
May  5 11:12:37 wagstaff kernel: [207897.331563] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  5 11:12:37 wagstaff kernel: [207897.339940] wlan0: direct probe to AP 00:13:7f:f1:77:f0 try 1
May  5 11:12:37 wagstaff NetworkManager: <info>  (wlan0): device state change: 2 -> 3 
May  5 11:12:37 wagstaff kernel: [207897.536070] wlan0: direct probe to AP 00:13:7f:f1:77:f0 try 2
May  5 11:12:37 wagstaff NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready 
May  5 11:12:37 wagstaff kernel: [207897.736063] wlan0: direct probe to AP 00:13:7f:f1:77:f0 try 3
May  5 11:12:37 wagstaff kernel: [207897.936061] wlan0: direct probe to AP 00:13:7f:f1:77:f0 timed out

```

kern.log:
```
May  5 10:30:28 wagstaff kernel: [207856.713447] usb 1-1: USB disconnect, address 14
May  5 10:30:51 wagstaff kernel: [207879.245242] b44: eth0: powering down PHY
May  5 10:30:51 wagstaff kernel: [207879.621945] wlan0: disassociating by local choice (reason=3)
May  5 11:12:28 wagstaff kernel: [207882.030619] PM: Syncing filesystems ... done.
May  5 11:12:28 wagstaff kernel: [207882.043412] PM: Preparing system for mem sleep
May  5 11:12:28 wagstaff kernel: [207882.043417] Freezing user space processes ... (elapsed 0.00 seconds) done.
May  5 11:12:28 wagstaff kernel: [207882.045225] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
May  5 11:12:28 wagstaff kernel: [207882.045293] PM: Entering mem sleep
May  5 11:12:28 wagstaff kernel: [207882.045307] Suspending console(s) (use no_console_suspend to debug)
May  5 11:12:28 wagstaff kernel: [207882.540279] sd 0:0:0:0: [sda] Synchronizing SCSI cache
May  5 11:12:28 wagstaff kernel: [207882.540704] sd 0:0:0:0: [sda] Stopping disk
May  5 11:12:28 wagstaff kernel: [207882.862732] ricoh-mmc: Suspending.
May  5 11:12:28 wagstaff kernel: [207882.862741] ricoh-mmc: Controller is now re-enabled.
May  5 11:12:28 wagstaff kernel: [207882.862796] ACPI handle has no context!
May  5 11:12:28 wagstaff kernel: [207882.862803] sdhci-pci 0000:03:01.1: PCI INT B disabled
May  5 11:12:28 wagstaff kernel: [207882.862809] ACPI handle has no context!
May  5 11:12:28 wagstaff kernel: [207882.896097] b44 0000:03:00.0: PCI INT A disabled
May  5 11:12:28 wagstaff kernel: [207882.896103] ACPI handle has no context!
May  5 11:12:28 wagstaff kernel: [207882.928075] NVRM: RmPowerManagement: 4
May  5 11:12:28 wagstaff kernel: [207884.363096] ata_piix 0000:00:1f.2: PCI INT B disabled
May  5 11:12:28 wagstaff kernel: [207884.376201] ehci_hcd 0000:00:1d.7: PCI INT A disabled
May  5 11:12:28 wagstaff kernel: [207884.392099] uhci_hcd 0000:00:1d.3: PCI INT D disabled
May  5 11:12:28 wagstaff kernel: [207884.392133] uhci_hcd 0000:00:1d.2: PCI INT C disabled
May  5 11:12:28 wagstaff kernel: [207884.392167] uhci_hcd 0000:00:1d.1: PCI INT B disabled
May  5 11:12:28 wagstaff kernel: [207884.392201] uhci_hcd 0000:00:1d.0: PCI INT A disabled
May  5 11:12:28 wagstaff kernel: [207884.408216] HDA Intel 0000:00:1b.0: PCI INT A disabled
May  5 11:12:28 wagstaff kernel: [207884.424165] PM: suspend devices took 2.380 seconds
May  5 11:12:28 wagstaff kernel: [207884.427911] ACPI: Preparing to enter system sleep state S3
May  5 11:12:28 wagstaff kernel: [207884.428258] Disabling non-boot CPUs ...
May  5 11:12:28 wagstaff kernel: [207884.528027] CPU 1 is now offline
May  5 11:12:28 wagstaff kernel: [207884.528031] SMP alternatives: switching to UP code
May  5 11:12:28 wagstaff kernel: [207884.684669] CPU0 attaching NULL sched-domain.
May  5 11:12:28 wagstaff kernel: [207884.684673] CPU1 attaching NULL sched-domain.
May  5 11:12:28 wagstaff kernel: [207884.684928] CPU0 attaching NULL sched-domain.
May  5 11:12:28 wagstaff kernel: [207884.685096] CPU1 is down
May  5 11:12:28 wagstaff kernel: [207884.685096] Back to C!
May  5 11:12:28 wagstaff kernel: [207884.685096] Enabling non-boot CPUs ...
May  5 11:12:28 wagstaff kernel: [207884.685096] SMP alternatives: switching to SMP code
May  5 11:12:28 wagstaff kernel: [207884.841808] Booting processor 1 APIC 0x1 ip 0x6000
May  5 11:12:28 wagstaff kernel: [207884.684517] Initializing CPU#1
May  5 11:12:28 wagstaff kernel: [207884.684517] Calibrating delay using timer specific routine.. 3990.16 BogoMIPS (lpj=7980338)
May  5 11:12:28 wagstaff kernel: [207884.684517] CPU: L1 I cache: 32K, L1 D cache: 32K
May  5 11:12:28 wagstaff kernel: [207884.684517] CPU: L2 cache: 2048K
May  5 11:12:28 wagstaff kernel: [207884.684517] CPU: Physical Processor ID: 0
May  5 11:12:28 wagstaff kernel: [207884.684517] CPU: Processor Core ID: 1
May  5 11:12:28 wagstaff kernel: [207884.932456] CPU1: Genuine Intel(R) CPU           T2500  @ 2.00GHz stepping 08
May  5 11:12:28 wagstaff kernel: [207884.932527] CPU0 attaching NULL sched-domain.
May  5 11:12:28 wagstaff kernel: [207884.933163] CPU0 attaching sched-domain:
May  5 11:12:28 wagstaff kernel: [207884.933166]  domain 0: span 0-1 level MC
May  5 11:12:28 wagstaff kernel: [207884.933168]   groups: 0 1
May  5 11:12:28 wagstaff kernel: [207884.933173] CPU1 attaching sched-domain:
May  5 11:12:28 wagstaff kernel: [207884.933175]  domain 0: span 0-1 level MC
May  5 11:12:28 wagstaff kernel: [207884.933176]   groups: 1 0
May  5 11:12:28 wagstaff kernel: [207884.936024] Switched to high resolution mode on CPU 1
May  5 11:12:28 wagstaff kernel: [207884.936036] CPU1 is up
May  5 11:12:28 wagstaff kernel: [207884.936039] ACPI: Waking up from system sleep state S3
May  5 11:12:28 wagstaff kernel: [207885.004272] pcieport-driver 0000:00:01.0: restoring config space at offset 0xf (was 0x100, writing 0x1a0100)
May  5 11:12:28 wagstaff kernel: [207885.004279] pcieport-driver 0000:00:01.0: restoring config space at offset 0xa (was 0xf, writing 0x0)
May  5 11:12:28 wagstaff kernel: [207885.004523] pcieport-driver 0000:00:01.0: restoring config space at offset 0x9 (was 0x1fff1, writing 0xdff1d001)
May  5 11:12:28 wagstaff kernel: [207885.004528] pcieport-driver 0000:00:01.0: restoring config space at offset 0x8 (was 0xfff0, writing 0xefe0ed00)
May  5 11:12:28 wagstaff kernel: [207885.004532] pcieport-driver 0000:00:01.0: restoring config space at offset 0x7 (was 0xf0, writing 0x200000f0)
May  5 11:12:28 wagstaff kernel: [207885.004536] pcieport-driver 0000:00:01.0: restoring config space at offset 0x6 (was 0x0, writing 0x10100)
May  5 11:12:28 wagstaff kernel: [207885.004542] pcieport-driver 0000:00:01.0: restoring config space at offset 0x3 (was 0x10000, writing 0x10010)
May  5 11:12:28 wagstaff kernel: [207885.004546] pcieport-driver 0000:00:01.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
May  5 11:12:28 wagstaff kernel: [207885.004567] pcieport-driver 0000:00:01.0: setting latency timer to 64
May  5 11:12:28 wagstaff kernel: [207885.020120] HDA Intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
May  5 11:12:28 wagstaff kernel: [207885.020147] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0xffa7c004, writing 0xefffc004)
May  5 11:12:28 wagstaff kernel: [207885.020156] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
May  5 11:12:28 wagstaff kernel: [207885.020167] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100102)
May  5 11:12:28 wagstaff kernel: [207885.020198] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
May  5 11:12:28 wagstaff kernel: [207885.020208] HDA Intel 0000:00:1b.0: setting latency timer to 64
May  5 11:12:28 wagstaff kernel: [207885.020247] pcieport-driver 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x20100)
May  5 11:12:28 wagstaff kernel: [207885.020265] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
May  5 11:12:28 wagstaff kernel: [207885.020274] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0xecf0ecf0)
May  5 11:12:28 wagstaff kernel: [207885.020283] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x7 (was 0x20000000, writing 0x200000f0)
May  5 11:12:28 wagstaff kernel: [207885.020292] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x6 (was 0x0, writing 0xb0b00)
May  5 11:12:28 wagstaff kernel: [207885.020305] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
May  5 11:12:28 wagstaff kernel: [207885.020316] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
May  5 11:12:28 wagstaff kernel: [207885.020368] pcieport-driver 0000:00:1c.0: setting latency timer to 64
May  5 11:12:28 wagstaff kernel: [207885.020392] pcieport-driver 0000:00:1c.3: restoring config space at offset 0xf (was 0x400, writing 0x20400)
May  5 11:12:28 wagstaff kernel: [207885.020410] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x9 (was 0x10001, writing 0xe011e001)
May  5 11:12:28 wagstaff kernel: [207885.020419] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x8 (was 0x0, writing 0xece0ecc0)
May  5 11:12:28 wagstaff kernel: [207885.020428] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x7 (was 0x0, writing 0xe0e0)
May  5 11:12:28 wagstaff kernel: [207885.020436] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x6 (was 0x0, writing 0xd0c00)
May  5 11:12:28 wagstaff kernel: [207885.020449] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
May  5 11:12:28 wagstaff kernel: [207885.020460] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
May  5 11:12:28 wagstaff kernel: [207885.020511] pcieport-driver 0000:00:1c.3: setting latency timer to 64
May  5 11:12:28 wagstaff kernel: [207885.020525] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
May  5 11:12:28 wagstaff kernel: [207885.020533] uhci_hcd 0000:00:1d.0: setting latency timer to 64
May  5 11:12:28 wagstaff kernel: [207885.020597] usb usb2: root hub lost power or was reset
May  5 11:12:28 wagstaff kernel: [207885.020621] uhci_hcd 0000:00:1d.1: enabling device (0000 -> 0001)
May  5 11:12:28 wagstaff kernel: [207885.020628] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
May  5 11:12:28 wagstaff kernel: [207885.020637] uhci_hcd 0000:00:1d.1: setting latency timer to 64
May  5 11:12:28 wagstaff kernel: [207885.020647] uhci_hcd 0000:00:1d.1: restoring config space at offset 0xf (was 0x200, writing 0x20b)
May  5 11:12:28 wagstaff kernel: [207885.020667] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x8 (was 0x1, writing 0xbf61)
May  5 11:12:28 wagstaff kernel: [207885.020713] usb usb3: root hub lost power or was reset
May  5 11:12:28 wagstaff kernel: [207885.020735] uhci_hcd 0000:00:1d.2: enabling device (0000 -> 0001)
May  5 11:12:28 wagstaff kernel: [207885.020741] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
May  5 11:12:28 wagstaff kernel: [207885.020750] uhci_hcd 0000:00:1d.2: setting latency timer to 64
May  5 11:12:28 wagstaff kernel: [207885.020760] uhci_hcd 0000:00:1d.2: restoring config space at offset 0xf (was 0x300, writing 0x309)
May  5 11:12:28 wagstaff kernel: [207885.020779] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x8 (was 0x1, writing 0xbf41)
May  5 11:12:28 wagstaff kernel: [207885.020825] usb usb4: root hub lost power or was reset
May  5 11:12:28 wagstaff kernel: [207885.020846] uhci_hcd 0000:00:1d.3: enabling device (0000 -> 0001)
May  5 11:12:28 wagstaff kernel: [207885.020853] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
May  5 11:12:28 wagstaff kernel: [207885.020862] uhci_hcd 0000:00:1d.3: setting latency timer to 64
May  5 11:12:28 wagstaff kernel: [207885.020872] uhci_hcd 0000:00:1d.3: restoring config space at offset 0xf (was 0x400, writing 0x407)
May  5 11:12:28 wagstaff kernel: [207885.020891] uhci_hcd 0000:00:1d.3: restoring config space at offset 0x8 (was 0x1, writing 0xbf21)
May  5 11:12:28 wagstaff kernel: [207885.020937] usb usb5: root hub lost power or was reset
May  5 11:12:28 wagstaff kernel: [207885.036098] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
May  5 11:12:28 wagstaff kernel: [207885.036106] ehci_hcd 0000:00:1d.7: setting latency timer to 64
May  5 11:12:28 wagstaff kernel: [207885.036189] pci 0000:00:1e.0: restoring config space at offset 0x9 (was 0x100f1, writing 0x1fff1)
May  5 11:12:28 wagstaff kernel: [207885.036197] pci 0000:00:1e.0: restoring config space at offset 0x8 (was 0xb0, writing 0xecb0ecb0)
May  5 11:12:28 wagstaff kernel: [207885.036206] pci 0000:00:1e.0: restoring config space at offset 0x7 (was 0x2280e0f0, writing 0x228000f0)
May  5 11:12:28 wagstaff kernel: [207885.036224] pci 0000:00:1e.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100107)
May  5 11:12:28 wagstaff kernel: [207885.036246] pci 0000:00:1e.0: setting latency timer to 64
May  5 11:12:28 wagstaff kernel: [207885.036296] pci 0000:00:1f.0: restoring config space at offset 0x1 (was 0x2100007, writing 0x2100107)
May  5 11:12:28 wagstaff kernel: [207885.052104] ata_piix 0000:00:1f.2: restoring config space at offset 0xf (was 0x200, writing 0x205)
May  5 11:12:28 wagstaff kernel: [207885.052150] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
May  5 11:12:28 wagstaff kernel: [207885.052157] ata_piix 0000:00:1f.2: setting latency timer to 64
May  5 11:12:28 wagstaff kernel: [207885.052186] pci 0000:00:1f.3: restoring config space at offset 0xf (was 0x200, writing 0x205)
May  5 11:12:28 wagstaff kernel: [207885.052227] pci 0000:00:1f.3: restoring config space at offset 0x1 (was 0x2800001, writing 0x2800101)
May  5 11:12:28 wagstaff kernel: [207885.052427] NVRM: RmPowerManagement: 5
May  5 11:12:28 wagstaff kernel: [207885.052567] ata2.00: _GTF evaluation failed (AE 0x1001)
May  5 11:12:28 wagstaff kernel: [207885.636105] iwl3945 0000:0b:00.0: enabling device (0000 -> 0002)
May  5 11:12:28 wagstaff kernel: [207885.636188] iwl3945 0000:0b:00.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
May  5 11:12:28 wagstaff kernel: [207885.636262] iwl3945 0000:0b:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xecfff000)
May  5 11:12:28 wagstaff kernel: [207885.636278] iwl3945 0000:0b:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
May  5 11:12:28 wagstaff kernel: [207885.636301] iwl3945 0000:0b:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100506)
May  5 11:12:28 wagstaff kernel: [207885.652096] b44 0000:03:00.0: enabling device (0000 -> 0002)
May  5 11:12:28 wagstaff kernel: [207885.652106] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
May  5 11:12:28 wagstaff kernel: [207885.652120] b44 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
May  5 11:12:28 wagstaff kernel: [207885.652147] b44 0000:03:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xecbfe000)
May  5 11:12:28 wagstaff kernel: [207885.652156] b44 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x4000)
May  5 11:12:28 wagstaff kernel: [207885.652166] b44 0000:03:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100106)
May  5 11:12:28 wagstaff kernel: [207885.688103] ohci1394 0000:03:01.0: restoring config space at offset 0xf (was 0x4020100, writing 0x4020103)
May  5 11:12:28 wagstaff kernel: [207885.688131] ohci1394 0000:03:01.0: restoring config space at offset 0x4 (was 0x0, writing 0xecbfd800)
May  5 11:12:28 wagstaff kernel: [207885.688140] ohci1394 0000:03:01.0: restoring config space at offset 0x3 (was 0x800000, writing 0x804000)
May  5 11:12:28 wagstaff kernel: [207885.688152] ohci1394 0000:03:01.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
May  5 11:12:28 wagstaff kernel: [207885.740785] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[ecbfd800-ecbfdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
May  5 11:12:28 wagstaff kernel: [207885.760103] sdhci-pci 0000:03:01.1: restoring config space at offset 0xf (was 0x200, writing 0x209)
May  5 11:12:28 wagstaff kernel: [207885.760131] sdhci-pci 0000:03:01.1: restoring config space at offset 0x4 (was 0x0, writing 0xecbfd400)
May  5 11:12:28 wagstaff kernel: [207885.760140] sdhci-pci 0000:03:01.1: restoring config space at offset 0x3 (was 0x800000, writing 0x804000)
May  5 11:12:28 wagstaff kernel: [207885.760151] sdhci-pci 0000:03:01.1: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
May  5 11:12:28 wagstaff kernel: [207885.760172] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
May  5 11:12:28 wagstaff kernel: [207885.761198] ricoh-mmc: Resuming.
May  5 11:12:28 wagstaff kernel: [207885.761210] ricoh-mmc: Controller is now disabled.
May  5 11:12:28 wagstaff kernel: [207885.761225] pci 0000:03:01.3: restoring config space at offset 0xf (was 0x200, writing 0x209)
May  5 11:12:28 wagstaff kernel: [207885.761253] pci 0000:03:01.3: restoring config space at offset 0x4 (was 0x0, writing 0xecbfd700)
May  5 11:12:28 wagstaff kernel: [207885.761265] pci 0000:03:01.3: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100102)
May  5 11:12:28 wagstaff kernel: [207885.761491] sd 0:0:0:0: [sda] Starting disk
May  5 11:12:28 wagstaff kernel: [207885.796526] ata2.00: configured for UDMA/33
May  5 11:12:28 wagstaff kernel: [207887.796401] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
May  5 11:12:28 wagstaff kernel: [207887.808853] ata1.00: configured for UDMA/133
May  5 11:12:28 wagstaff kernel: [207887.861370] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
May  5 11:12:28 wagstaff kernel: [207887.861408] sd 0:0:0:0: [sda] Write Protect is off
May  5 11:12:28 wagstaff kernel: [207887.861412] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
May  5 11:12:28 wagstaff kernel: [207887.861464] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  5 11:12:28 wagstaff kernel: [207888.500391] PM: resume devices took 3.560 seconds
May  5 11:12:28 wagstaff kernel: [207888.500462] PM: Finishing wakeup.
May  5 11:12:28 wagstaff kernel: [207888.500465] Restarting tasks ... done.
May  5 11:12:28 wagstaff kernel: [207888.674597] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
May  5 11:12:36 wagstaff kernel: [207895.762595] ADDRCONF(NETDEV_UP): eth0: link is not ready
May  5 11:12:36 wagstaff kernel: [207897.279339] Registered led device: iwl-phy0:radio
May  5 11:12:36 wagstaff kernel: [207897.279419] Registered led device: iwl-phy0:assoc
May  5 11:12:36 wagstaff kernel: [207897.279453] Registered led device: iwl-phy0:RX
May  5 11:12:36 wagstaff kernel: [207897.279486] Registered led device: iwl-phy0:TX
May  5 11:12:37 wagstaff kernel: [207897.331563] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  5 11:12:37 wagstaff kernel: [207897.339940] wlan0: direct probe to AP 00:13:7f:f1:77:f0 try 1
May  5 11:12:37 wagstaff kernel: [207897.536070] wlan0: direct probe to AP 00:13:7f:f1:77:f0 try 2
May  5 11:12:37 wagstaff kernel: [207897.736063] wlan0: direct probe to AP 00:13:7f:f1:77:f0 try 3
May  5 11:12:37 wagstaff kernel: [207897.936061] wlan0: direct probe to AP 00:13:7f:f1:77:f0 timed out

```

---

### Post by clconway on 2009-05-12
This happened again today. Does anybody have any idea how I can debug this?

---

### Post by SgtPepperKSU on 2009-05-27
The same thing is happening on my Inspiron 8600, except that it is waking up every 6-9 minutes (and going back to standby after configured amount of idle time).

Unfortunately, I don't have any ideas on how to debug.

---

### Post by meschareth on 2009-09-14
Hello!

I have the same problem here with a lenovo ThinkPad T61p starting 3 weeks ago. Before, it runs perfectly well ... any software updates which would be blameable???

---

