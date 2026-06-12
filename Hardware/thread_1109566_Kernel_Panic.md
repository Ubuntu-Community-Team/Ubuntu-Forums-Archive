---
title: "Kernel Panic?????"
date: 2009-03-28
forum: Hardware
---

### Post by Nata-Bunny on 2009-03-28
Hello,

I was wondering if anyone would be able to help me troubleshoot why my computer is going in to kernel panic for no reason that I can determine.  I am not sure what you need me to post so please request additional information and I will provide it.

---

### Post by pytheas22 on 2009-03-28
The next time the system crashes, reboot, then post the output of this command:
```

cat /var/log/syslog
```

---

### Post by Nata-Bunny on 2009-03-29
> **pytheas22 said:**
> The next time the system crashes, reboot, then post the output of this command:
```

cat /var/log/syslog
```

Mar 29 12:49:51 Surtur syslogd 1.5.0#2ubuntu6: restart.
Mar 29 12:51:38 Surtur anacron[7408]: Job `cron.weekly' started
Mar 29 12:51:38 Surtur anacron[8022]: Updated timestamp for job `cron.weekly' to 2009-03-29
Mar 29 12:54:37 Surtur syslogd 1.5.0#2ubuntu6: restart.
Mar 29 12:54:37 Surtur anacron[7408]: Job `cron.weekly' terminated
Mar 29 12:54:37 Surtur anacron[7408]: Normal exit (1 job run)
Mar 29 13:17:01 Surtur /USR/SBIN/CRON[8579]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 29 13:31:47 Surtur NetworkManager: <debug> [1238347907.042830] periodic_update(): Roamed from BSSID 00:13:49:54:59:1E (Gridscape) to (none) ((none)) 
Mar 29 13:31:53 Surtur NetworkManager: <debug> [1238347913.046983] periodic_update(): Roamed from BSSID (none) ((none)) to 00:13:49:54:59:1E (Gridscape) 
Mar 29 13:33:47 Surtur NetworkManager: <debug> [1238348027.122813] periodic_update(): Roamed from BSSID 00:13:49:54:59:1E (Gridscape) to (none) ((none)) 
Mar 29 13:33:53 Surtur NetworkManager: <debug> [1238348033.126467] periodic_update(): Roamed from BSSID (none) ((none)) to 00:13:49:54:59:1E (Gridscape) 
Mar 29 13:35:47 Surtur NetworkManager: <debug> [1238348147.198363] periodic_update(): Roamed from BSSID 00:13:49:54:59:1E (Gridscape) to (none) ((none)) 
Mar 29 13:35:53 Surtur NetworkManager: <debug> [1238348153.202916] periodic_update(): Roamed from BSSID (none) ((none)) to 00:13:49:54:59:1E (Gridscape) 
Mar 29 13:37:47 Surtur NetworkManager: <debug> [1238348267.274643] periodic_update(): Roamed from BSSID 00:13:49:54:59:1E (Gridscape) to (none) ((none)) 
Mar 29 13:37:53 Surtur NetworkManager: <debug> [1238348273.278480] periodic_update(): Roamed from BSSID (none) ((none)) to 00:13:49:54:59:1E (Gridscape) 
Mar 29 13:39:47 Surtur NetworkManager: <debug> [1238348387.354350] periodic_update(): Roamed from BSSID 00:13:49:54:59:1E (Gridscape) to (none) ((none)) 
Mar 29 13:39:53 Surtur NetworkManager: <debug> [1238348393.358863] periodic_update(): Roamed from BSSID (none) ((none)) to 00:13:49:54:59:1E (Gridscape) 
Mar 29 13:41:47 Surtur NetworkManager: <debug> [1238348507.434354] periodic_update(): Roamed from BSSID 00:13:49:54:59:1E (Gridscape) to (none) ((none)) 
Mar 29 13:41:53 Surtur NetworkManager: <debug> [1238348513.438359] periodic_update(): Roamed from BSSID (none) ((none)) to 00:13:49:54:59:1E (Gridscape) 
Mar 29 13:43:47 Surtur NetworkManager: <debug> [1238348627.518838] periodic_update(): Roamed from BSSID 00:13:49:54:59:1E (Gridscape) to (none) ((none)) 
Mar 29 13:43:53 Surtur NetworkManager: <debug> [1238348633.518399] periodic_update(): Roamed from BSSID (none) ((none)) to 00:13:49:54:59:1E (Gridscape) 
Mar 29 13:45:47 Surtur NetworkManager: <debug> [1238348747.594391] periodic_update(): Roamed from BSSID 00:13:49:54:59:1E (Gridscape) to (none) ((none)) 
Mar 29 13:45:53 Surtur NetworkManager: <debug> [1238348753.598465] periodic_update(): Roamed from BSSID (none) ((none)) to 00:13:49:54:59:1E (Gridscape) 
Mar 29 13:47:47 Surtur NetworkManager: <debug> [1238348867.674369] periodic_update(): Roamed from BSSID 00:13:49:54:59:1E (Gridscape) to (none) ((none)) 
Mar 29 13:47:53 Surtur NetworkManager: <debug> [1238348873.678583] periodic_update(): Roamed from BSSID (none) ((none)) to 00:13:49:54:59:1E (Gridscape) 
Mar 29 13:49:47 Surtur NetworkManager: <debug> [1238348987.754295] periodic_update(): Roamed from BSSID 00:13:49:54:59:1E (Gridscape) to (none) ((none)) 
Mar 29 13:49:53 Surtur NetworkManager: <debug> [1238348993.758383] periodic_update(): Roamed from BSSID (none) ((none)) to 00:13:49:54:59:1E (Gridscape) 
Mar 29 13:51:47 Surtur NetworkManager: <debug> [1238349107.826871] periodic_update(): Roamed from BSSID 00:13:49:54:59:1E (Gridscape) to (none) ((none)) 
Mar 29 13:51:53 Surtur NetworkManager: <debug> [1238349113.830867] periodic_update(): Roamed from BSSID (none) ((none)) to 00:13:49:54:59:1E (Gridscape) 
Mar 29 13:53:47 Surtur NetworkManager: <debug> [1238349227.905637] periodic_update(): Roamed from BSSID 00:13:49:54:59:1E (Gridscape) to (none) ((none)) 
Mar 29 13:53:53 Surtur NetworkManager: <debug> [1238349233.910876] periodic_update(): Roamed from BSSID (none) ((none)) to 00:13:49:54:59:1E (Gridscape) 
Mar 29 14:05:57 Surtur kernel: [ 7373.742428] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
Mar 29 14:17:01 Surtur /USR/SBIN/CRON[9478]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 29 14:43:29 Surtur -- MARK --
Mar 29 14:47:49 Surtur kernel: [ 9885.980421] Xorg[5473]: segfault at a02e0014 ip 0811f038 sp bf8d7798 error 6 in Xorg[8048000+18f000]
Mar 29 14:47:49 Surtur gdm[5467]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Mar 29 14:47:49 Surtur NetworkManager: <info>  (wlan0): device state change: 8 -> 3 
Mar 29 14:47:49 Surtur NetworkManager: <info>  (wlan0): deactivating device (reason: 38). 
Mar 29 14:47:50 Surtur bonobo-activation-server (natalie-9956): could not associate with desktop session: Failed to connect to socket /tmp/dbus-RA7xz7hPf0: Connection refused
Mar 29 14:47:50 Surtur NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 7178 
Mar 29 14:47:50 Surtur kernel: [ 9886.408774] wlan0: authenticate with AP f63d6e28
Mar 29 14:47:50 Surtur kernel: [ 9886.410200] wlan0: authenticated
Mar 29 14:47:50 Surtur kernel: [ 9886.410215] wlan0: associate with AP f63d6e28
Mar 29 14:47:50 Surtur NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess  
Mar 29 14:47:50 Surtur avahi-daemon[4977]: Withdrawing address record for 192.168.1.34 on wlan0.
Mar 29 14:47:50 Surtur avahi-daemon[4977]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.34.
Mar 29 14:47:50 Surtur avahi-daemon[4977]: Interface wlan0.IPv4 no longer relevant for mDNS.
Mar 29 14:47:50 Surtur kernel: [ 9886.412115] wlan0: RX AssocResp from f61f908a (capab=0x411 status=1 aid=2)
Mar 29 14:47:50 Surtur kernel: [ 9886.412132] wlan0: AP denied association (code=1)
Mar 29 14:47:50 Surtur kernel: [ 9886.608066] wlan0: associate with AP f63d6e28
Mar 29 14:47:50 Surtur kernel: [ 9886.609884] wlan0: RX AssocResp from f3b0e08a (capab=0x411 status=1 aid=2)
Mar 29 14:47:50 Surtur kernel: [ 9886.609903] wlan0: AP denied association (code=1)
Mar 29 14:47:50 Surtur kernel: [ 9886.808052] wlan0: associate with AP f63d6e28
Mar 29 14:47:50 Surtur kernel: [ 9886.809744] wlan0: RX AssocResp from ef8b508a (capab=0x411 status=1 aid=2)
Mar 29 14:47:50 Surtur kernel: [ 9886.809760] wlan0: AP denied association (code=1)
Mar 29 14:47:50 Surtur kernel: [ 9887.008062] wlan0: association with AP f63d6e28 timed out
Mar 29 14:47:50 Surtur acpid: client connected from 10003[0:0] 
Mar 29 14:47:52 Surtur avahi-daemon[4977]: Disconnected from D-Bus, exiting.
Mar 29 14:47:52 Surtur nm-dispatcher.action: Disconnected from the system bus, exiting.
Mar 29 14:47:52 Surtur nm-system-settings: disconnected from the system bus, exiting.
Mar 29 14:47:52 Surtur avahi-daemon[4977]: Got SIGQUIT, quitting.
Mar 29 14:47:52 Surtur NetworkManager: <info>  disconnected by the system bus. 
Mar 29 14:47:52 Surtur NetworkManager: <WARN>  hal_deinit(): libhal shutdown failed - Connection is closed 
Mar 29 14:47:52 Surtur avahi-daemon[4977]: write() failed: Broken pipe 
Mar 29 14:47:55 Surtur NetworkManager: <WARN>  nm_dbus_manager_init_bus(): Could not get the system bus.  Make sure the message bus daemon is running!  Message: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused 
Mar 29 14:49:01 Surtur syslogd 1.5.0#2ubuntu6: restart.
Mar 29 14:49:01 Surtur kernel: Inspecting /boot/System.map-2.6.27-14-generic
Mar 29 14:49:01 Surtur kernel: Cannot find map file.
Mar 29 14:49:01 Surtur kernel: Loaded 58018 symbols from 167 modules.
Mar 29 14:49:01 Surtur kernel: [    0.000000] Initializing cgroup subsys cpuset
Mar 29 14:49:01 Surtur kernel: [    0.000000] Initializing cgroup subsys cpu
Mar 29 14:49:01 Surtur kernel: [    0.000000] Linux version 2.6.27-14-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu12) ) #1 SMP Fri Mar 13 18:00:20 UTC 2009 (Ubuntu 2.6.27-14.30-generic)
Mar 29 14:49:01 Surtur kernel: [    0.000000] BIOS-provided physical RAM map:
Mar 29 14:49:01 Surtur kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Mar 29 14:49:01 Surtur kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Mar 29 14:49:01 Surtur kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Mar 29 14:49:01 Surtur kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000afdd7000 (usable)
Mar 29 14:49:01 Surtur kernel: [    0.000000]  BIOS-e820: 00000000afdd7000 - 00000000afe3f000 (ACPI NVS)
Mar 29 14:49:01 Surtur kernel: [    0.000000]  BIOS-e820: 00000000afe3f000 - 00000000afe70000 (usable)
Mar 29 14:49:01 Surtur kernel: [    0.000000]  BIOS-e820: 00000000afe70000 - 00000000afebf000 (reserved)
Mar 29 14:49:01 Surtur kernel: [    0.000000]  BIOS-e820: 00000000afebf000 - 00000000afeef000 (usable)
Mar 29 14:49:01 Surtur kernel: [    0.000000]  BIOS-e820: 00000000afeef000 - 00000000afeff000 (ACPI data)
Mar 29 14:49:01 Surtur kernel: [    0.000000]  BIOS-e820: 00000000afeff000 - 00000000aff00000 (usable)
Mar 29 14:49:01 Surtur kernel: [    0.000000]  BIOS-e820: 00000000f7000000 - 00000000f8000000 (reserved)
Mar 29 14:49:01 Surtur kernel: [    0.000000]  BIOS-e820: 00000000feb00000 - 00000000feb01000 (reserved)
Mar 29 14:49:01 Surtur kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Mar 29 14:49:01 Surtur kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Mar 29 14:49:01 Surtur kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Mar 29 14:49:01 Surtur kernel: [    0.000000] DMI 2.4 present.
Mar 29 14:49:01 Surtur kernel: [    0.000000] last_pfn = 0xaff00 max_arch_pfn = 0x100000
Mar 29 14:49:01 Surtur kernel: [    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
Mar 29 14:49:01 Surtur kernel: [    0.000000] RAMDISK: 3781a000 - 37fef9d2
Mar 29 14:49:01 Surtur kernel: [    0.000000] ACPI: RSDP 000FE020, 0024 (r2 TOSINV)
Mar 29 14:49:01 Surtur kernel: [    0.000000] ACPI: XSDT AFEFE120, 005C (r1 TOSINV TOSINV00        3       1000013)
Mar 29 14:49:01 Surtur kernel: [    0.000000] ACPI: FACP AFEFD000, 00F4 (r4 TOSINV TOSINV00        3 MSFT  1000013)
Mar 29 14:49:01 Surtur kernel: [    0.000000] ACPI: DSDT AFEF2000, 77C5 (r1 TOSINV TOSINV00 F0000000 MSFT  1000013)
Mar 29 14:49:01 Surtur kernel: [    0.000000] ACPI: FACS AFDE0000, 0040
Mar 29 14:49:01 Surtur kernel: [    0.000000] ACPI: HPET AFEFC000, 0038 (r1 TOSINV TOSINV00        1 MSFT  1000013)
Mar 29 14:49:01 Surtur kernel: [    0.000000] ACPI: APIC AFEFB000, 0084 (r2 TOSINV TOSINV00        1 MSFT  1000013)
Mar 29 14:49:01 Surtur kernel: [    0.000000] ACPI: MCFG AFEFA000, 003C (r1 TOSINV TOSINV00        1 MSFT  1000013)
Mar 29 14:49:01 Surtur kernel: [    0.000000] ACPI: SLIC AFEF1000, 0176 (r1 TOSINV TOSINV00        1 MSFT  1000013)
Mar 29 14:49:01 Surtur kernel: [    0.000000] ACPI: BOOT AFEF0000, 0028 (r1 TOSINV TOSINV00        1 MSFT  1000013)
Mar 29 14:49:01 Surtur kernel: [    0.000000] ACPI: SSDT AFEEF000, 0390 (r1 AMD    PowerNow        1 AMD         1)
Mar 29 14:49:01 Surtur kernel: [    0.000000] ACPI: DMI detected: Toshiba
Mar 29 14:49:01 Surtur kernel: [    0.000000] 1919MB HIGHMEM available.
Mar 29 14:49:01 Surtur kernel: [    0.000000] 896MB LOWMEM available.
Mar 29 14:49:01 Surtur kernel: [    0.000000]   mapped low ram: 0 - 38000000
Mar 29 14:49:01 Surtur kernel: [    0.000000]   low ram: 00000000 - 38000000
Mar 29 14:49:01 Surtur kernel: [    0.000000]   bootmap 00008000 - 0000f000
Mar 29 14:49:01 Surtur kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
Mar 29 14:49:01 Surtur kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Mar 29 14:49:01 Surtur kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Mar 29 14:49:01 Surtur kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Mar 29 14:49:01 Surtur kernel: [    0.000000]   #3 [0000100000 - 00005c39e0]    TEXT DATA BSS ==> [0000100000 - 00005c39e0]
Mar 29 14:49:01 Surtur kernel: [    0.000000]   #4 [003781a000 - 0037fef9d2]          RAMDISK ==> [003781a000 - 0037fef9d2]
Mar 29 14:49:01 Surtur kernel: [    0.000000]   #5 [00005c4000 - 00005c7000]    INIT_PG_TABLE ==> [00005c4000 - 00005c7000]
Mar 29 14:49:01 Surtur kernel: [    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Mar 29 14:49:01 Surtur kernel: [    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Mar 29 14:49:01 Surtur kernel: [    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
Mar 29 14:49:01 Surtur kernel: [    0.000000] Zone PFN ranges:
Mar 29 14:49:01 Surtur kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Mar 29 14:49:01 Surtur kernel: [    0.000000]   Normal   0x00001000 -> 0x00038000
Mar 29 14:49:01 Surtur kernel: [    0.000000]   HighMem  0x00038000 -> 0x000aff00
Mar 29 14:49:01 Surtur kernel: [    0.000000] Movable zone start PFN for each node
Mar 29 14:49:01 Surtur kernel: [    0.000000] early_node_map[5] active PFN ranges
Mar 29 14:49:01 Surtur kernel: [    0.000000]     0: 0x00000000 -> 0x0000009f
Mar 29 14:49:01 Surtur kernel: [    0.000000]     0: 0x00000100 -> 0x000afdd7
Mar 29 14:49:01 Surtur kernel: [    0.000000]     0: 0x000afe3f -> 0x000afe70
Mar 29 14:49:01 Surtur kernel: [    0.000000]     0: 0x000afebf -> 0x000afeef
Mar 29 14:49:01 Surtur kernel: [    0.000000]     0: 0x000afeff -> 0x000aff00
Mar 29 14:49:01 Surtur kernel: [    0.000000] On node 0 totalpages: 720344
Mar 29 14:49:01 Surtur kernel: [    0.000000] free_area_init_node: node 0, pgdat c048c700, node_mem_map c1000000
Mar 29 14:49:01 Surtur kernel: [    0.000000]   DMA zone: 3963 pages, LIFO batch:0
Mar 29 14:49:01 Surtur kernel: [    0.000000]   Normal zone: 223300 pages, LIFO batch:31
Mar 29 14:49:01 Surtur kernel: [    0.000000]   HighMem zone: 486747 pages, LIFO batch:31
Mar 29 14:49:01 Surtur kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Mar 29 14:49:01 Surtur kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Mar 29 14:49:01 Surtur kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Mar 29 14:49:01 Surtur kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Mar 29 14:49:01 Surtur kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
Mar 29 14:49:01 Surtur kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
Mar 29 14:49:01 Surtur kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Mar 29 14:49:01 Surtur kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Mar 29 14:49:01 Surtur kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Mar 29 14:49:01 Surtur kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Mar 29 14:49:01 Surtur kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Mar 29 14:49:01 Surtur kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
Mar 29 14:49:01 Surtur kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Mar 29 14:49:01 Surtur kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Mar 29 14:49:01 Surtur kernel: [    0.000000] ACPI: IRQ0 used by override.
Mar 29 14:49:01 Surtur kernel: [    0.000000] ACPI: IRQ2 used by override.
Mar 29 14:49:01 Surtur kernel: [    0.000000] ACPI: IRQ9 used by override.
Mar 29 14:49:01 Surtur kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Mar 29 14:49:01 Surtur kernel: [    0.000000] ACPI: HPET id: 0x1002a201 base: 0xfed00000
Mar 29 14:49:01 Surtur kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Mar 29 14:49:01 Surtur kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Mar 29 14:49:01 Surtur kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Mar 29 14:49:01 Surtur kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Mar 29 14:49:01 Surtur kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Mar 29 14:49:01 Surtur kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Mar 29 14:49:01 Surtur kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Mar 29 14:49:01 Surtur kernel: [    0.000000] Allocating PCI resources starting at b0000000 (gap: aff00000:47100000)
Mar 29 14:49:01 Surtur kernel: [    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
Mar 29 14:49:01 Surtur kernel: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
Mar 29 14:49:01 Surtur kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 714010
Mar 29 14:49:01 Surtur kernel: [    0.000000] Kernel command line: root=UUID=12fdf8b7-8c40-4633-aebe-f3924307e918 ro quiet splash 
Mar 29 14:49:01 Surtur kernel: [    0.000000] Enabling fast FPU save and restore... done.
Mar 29 14:49:01 Surtur kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Mar 29 14:49:01 Surtur kernel: [    0.000000] Initializing CPU#0
Mar 29 14:49:01 Surtur kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Mar 29 14:49:01 Surtur kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
Mar 29 14:49:01 Surtur kernel: [    0.000000] TSC: using PIT calibration value
Mar 29 14:49:01 Surtur kernel: [    0.000000] Detected 2099.100 MHz processor.
Mar 29 14:49:01 Surtur kernel: [    0.004000] Console: colour VGA+ 80x25
Mar 29 14:49:01 Surtur kernel: [    0.004000] console [tty0] enabled
Mar 29 14:49:01 Surtur kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Mar 29 14:49:01 Surtur kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Mar 29 14:49:01 Surtur kernel: [    0.004000] Memory: 2841168k/2882560k available (2577k kernel code, 39296k reserved, 1163k data, 428k init, 1964260k highmem)
Mar 29 14:49:01 Surtur kernel: [    0.004000] virtual kernel memory layout:
Mar 29 14:49:01 Surtur kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Mar 29 14:49:01 Surtur kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Mar 29 14:49:01 Surtur kernel: [    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
Mar 29 14:49:01 Surtur kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Mar 29 14:49:01 Surtur kernel: [    0.004000]       .init : 0xc04ad000 - 0xc0518000   ( 428 kB)
Mar 29 14:49:01 Surtur kernel: [    0.004000]       .data : 0xc038473a - 0xc04a7680   (1163 kB)
Mar 29 14:49:01 Surtur kernel: [    0.004000]       .text : 0xc0100000 - 0xc038473a   (2577 kB)
Mar 29 14:49:01 Surtur kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Mar 29 14:49:01 Surtur kernel: [    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
Mar 29 14:49:01 Surtur kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Mar 29 14:49:01 Surtur kernel: [    0.004000] hpet clockevent registered
Mar 29 14:49:01 Surtur kernel: [    0.004010] Calibrating delay loop (skipped), value calculated using timer frequency.. 4198.20 BogoMIPS (lpj=8396400)
Mar 29 14:49:01 Surtur kernel: [    0.004027] Security Framework initialized
Mar 29 14:49:01 Surtur kernel: [    0.004033] SELinux:  Disabled at boot.
Mar 29 14:49:01 Surtur kernel: [    0.004052] AppArmor: AppArmor initialized
Mar 29 14:49:01 Surtur kernel: [    0.004060] Mount-cache hash table entries: 512
Mar 29 14:49:01 Surtur kernel: [    0.004221] Initializing cgroup subsys ns
Mar 29 14:49:01 Surtur kernel: [    0.004225] Initializing cgroup subsys cpuacct
Mar 29 14:49:01 Surtur kernel: [    0.004228] Initializing cgroup subsys memory
Mar 29 14:49:01 Surtur kernel: [    0.004242] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Mar 29 14:49:01 Surtur kernel: [    0.004245] CPU: L2 Cache: 512K (64 bytes/line)
Mar 29 14:49:01 Surtur kernel: [    0.004247] CPU 0(2) -> Core 0
Mar 29 14:49:01 Surtur kernel: [    0.004250] using C1E aware idle routine
Mar 29 14:49:01 Surtur kernel: [    0.004260] Checking 'hlt' instruction... OK.
Mar 29 14:49:01 Surtur kernel: [    0.022120] ACPI: Core revision 20080609
Mar 29 14:49:01 Surtur kernel: [    0.024372] ACPI: Checking initramfs for custom DSDT
Mar 29 14:49:01 Surtur kernel: [    0.352236] ENABLING IO-APIC IRQs
Mar 29 14:49:01 Surtur kernel: [    0.352414] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Mar 29 14:49:01 Surtur kernel: [    0.394156] CPU0: AMD Turion(tm) X2 Dual-Core Mobile RM-72 stepping 01
Mar 29 14:49:01 Surtur kernel: [    0.396024] Booting processor 1/1 ip 6000
Mar 29 14:49:01 Surtur kernel: [    0.004000] Initializing CPU#1
Mar 29 14:49:01 Surtur kernel: [    0.004000] Calibrating delay using timer specific routine.. 4189.64 BogoMIPS (lpj=8379284)
Mar 29 14:49:01 Surtur kernel: [    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Mar 29 14:49:01 Surtur kernel: [    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
Mar 29 14:49:01 Surtur kernel: [    0.004000] CPU 1(2) -> Core 1
Mar 29 14:49:01 Surtur kernel: [    0.480266] CPU1: AMD Turion(tm) X2 Dual-Core Mobile RM-72 stepping 01
Mar 29 14:49:01 Surtur kernel: [    0.480288] checking TSC synchronization [CPU#0 -> CPU#1]:
Mar 29 14:49:01 Surtur kernel: [    0.484030] Measured 75635119 cycles TSC warp between CPUs, turning off TSC clock.
Mar 29 14:49:01 Surtur kernel: [    0.484030] Marking TSC unstable due to check_tsc_sync_source failed
Mar 29 14:49:01 Surtur kernel: [    0.484039] Brought up 2 CPUs
Mar 29 14:49:01 Surtur kernel: [    0.484042] Total of 2 processors activated (8387.84 BogoMIPS).
Mar 29 14:49:01 Surtur kernel: [    0.484058] CPU0 attaching sched-domain:
Mar 29 14:49:01 Surtur kernel: [    0.484061]  domain 0: span 0-1 level CPU
Mar 29 14:49:01 Surtur kernel: [    0.484064]   groups: 0 1
Mar 29 14:49:01 Surtur kernel: [    0.484070] CPU1 attaching sched-domain:
Mar 29 14:49:01 Surtur kernel: [    0.484072]  domain 0: span 0-1 level CPU
Mar 29 14:49:01 Surtur kernel: [    0.484074]   groups: 1 0
Mar 29 14:49:01 Surtur kernel: [    0.484141] net_namespace: 840 bytes
Mar 29 14:49:01 Surtur kernel: [    0.484141] Booting paravirtualized kernel on bare hardware
Mar 29 14:49:01 Surtur kernel: [    0.484265] Time: 18:48:29  Date: 03/29/09
Mar 29 14:49:01 Surtur kernel: [    0.484299] NET: Registered protocol family 16
Mar 29 14:49:01 Surtur kernel: [    0.484322] EISA bus registered
Mar 29 14:49:01 Surtur kernel: [    0.484322] ACPI: bus type pci registered
Mar 29 14:49:01 Surtur kernel: [    0.484322] PCI: MCFG configuration 0: base f7000000 segment 0 buses 0 - 15
Mar 29 14:49:01 Surtur kernel: [    0.484322] PCI: MCFG area at f7000000 reserved in E820
Mar 29 14:49:01 Surtur kernel: [    0.484322] PCI: Using MMCONFIG for extended config space
Mar 29 14:49:01 Surtur kernel: [    0.484322] PCI: Using configuration type 1 for base access
Mar 29 14:49:01 Surtur kernel: [    0.485021] ACPI: EC: Look up EC in DSDT
Mar 29 14:49:01 Surtur kernel: [    0.492174] ACPI: BIOS _OSI(Linux) query ignored via DMI
Mar 29 14:49:01 Surtur kernel: [    0.497877] ACPI: Interpreter enabled
Mar 29 14:49:01 Surtur kernel: [    0.497885] ACPI: (supports S0 S1 S3 S4 S5)
Mar 29 14:49:01 Surtur kernel: [    0.497910] ACPI: Using IOAPIC for interrupt routing
Mar 29 14:49:01 Surtur kernel: [    0.498129] ACPI: EC: non-query interrupt received, switching to interrupt mode
Mar 29 14:49:01 Surtur kernel: [    0.981455] ACPI: EC: GPE = 0x7, I/O: command/status = 0x66, data = 0x62
Mar 29 14:49:01 Surtur kernel: [    0.981455] ACPI: EC: driver started in interrupt mode
Mar 29 14:49:01 Surtur kernel: [    0.981455] ACPI: PCI Root Bridge [PCI0] (0000:00)
Mar 29 14:49:01 Surtur kernel: [    0.981455] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
Mar 29 14:49:01 Surtur kernel: [    0.981455] pci 0000:00:04.0: PME# disabled
Mar 29 14:49:01 Surtur kernel: [    0.981455] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
Mar 29 14:49:01 Surtur kernel: [    0.981455] pci 0000:00:05.0: PME# disabled
Mar 29 14:49:01 Surtur kernel: [    0.981455] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
Mar 29 14:49:01 Surtur kernel: [    0.981455] pci 0000:00:06.0: PME# disabled
Mar 29 14:49:01 Surtur kernel: [    0.981455] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
Mar 29 14:49:01 Surtur kernel: [    0.981455] pci 0000:00:07.0: PME# disabled
Mar 29 14:49:01 Surtur kernel: [    0.981455] PCI: 0000:00:11.0 reg 10 io port: [7038, 703f]
Mar 29 14:49:01 Surtur kernel: [    0.981455] PCI: 0000:00:11.0 reg 14 io port: [704c, 704f]
Mar 29 14:49:01 Surtur kernel: [    0.981455] PCI: 0000:00:11.0 reg 18 io port: [7030, 7037]
Mar 29 14:49:01 Surtur kernel: [    0.981455] PCI: 0000:00:11.0 reg 1c io port: [7048, 704b]
Mar 29 14:49:01 Surtur kernel: [    0.981455] PCI: 0000:00:11.0 reg 20 io port: [7010, 701f]
Mar 29 14:49:01 Surtur kernel: [    0.981455] PCI: 0000:00:11.0 reg 24 32bit mmio: [d6408000, d64083ff]
Mar 29 14:49:01 Surtur kernel: [    0.981455] PCI: 0000:00:12.0 reg 10 32bit mmio: [d6407000, d6407fff]
Mar 29 14:49:01 Surtur kernel: [    0.981455] PCI: 0000:00:12.1 reg 10 32bit mmio: [d6406000, d6406fff]
Mar 29 14:49:01 Surtur kernel: [    0.981455] PCI: 0000:00:12.2 reg 10 32bit mmio: [d6408500, d64085ff]
Mar 29 14:49:01 Surtur kernel: [    0.984036] pci 0000:00:12.2: supports D1
Mar 29 14:49:01 Surtur kernel: [    0.984038] pci 0000:00:12.2: supports D2
Mar 29 14:49:01 Surtur kernel: [    0.984040] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Mar 29 14:49:01 Surtur kernel: [    0.984045] pci 0000:00:12.2: PME# disabled
Mar 29 14:49:01 Surtur kernel: [    0.984074] PCI: 0000:00:13.0 reg 10 32bit mmio: [d6405000, d6405fff]
Mar 29 14:49:01 Surtur kernel: [    0.984138] PCI: 0000:00:13.1 reg 10 32bit mmio: [d6404000, d6404fff]
Mar 29 14:49:01 Surtur kernel: [    0.984225] PCI: 0000:00:13.2 reg 10 32bit mmio: [d6408400, d64084ff]
Mar 29 14:49:01 Surtur kernel: [    0.984297] pci 0000:00:13.2: supports D1
Mar 29 14:49:01 Surtur kernel: [    0.984298] pci 0000:00:13.2: supports D2
Mar 29 14:49:01 Surtur kernel: [    0.984301] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Mar 29 14:49:01 Surtur kernel: [    0.984306] pci 0000:00:13.2: PME# disabled
Mar 29 14:49:01 Surtur kernel: [    0.984435] PCI: 0000:00:14.1 reg 10 io port: [0, 7]
Mar 29 14:49:01 Surtur kernel: [    0.984443] PCI: 0000:00:14.1 reg 14 io port: [0, 3]
Mar 29 14:49:01 Surtur kernel: [    0.984450] PCI: 0000:00:14.1 reg 18 io port: [0, 7]
Mar 29 14:49:01 Surtur kernel: [    0.984458] PCI: 0000:00:14.1 reg 1c io port: [0, 3]
Mar 29 14:49:01 Surtur kernel: [    0.984466] PCI: 0000:00:14.1 reg 20 io port: [7000, 700f]
Mar 29 14:49:01 Surtur kernel: [    0.984545] PCI: 0000:00:14.2 reg 10 64bit mmio: [d6400000, d6403fff]
Mar 29 14:49:01 Surtur kernel: [    0.984603] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Mar 29 14:49:01 Surtur kernel: [    0.984608] pci 0000:00:14.2: PME# disabled
Mar 29 14:49:01 Surtur kernel: [    0.984908] PCI: 0000:01:05.0 reg 10 32bit mmio: [c0000000, cfffffff]
Mar 29 14:49:01 Surtur kernel: [    0.984913] PCI: 0000:01:05.0 reg 14 io port: [6000, 60ff]
Mar 29 14:49:01 Surtur kernel: [    0.984919] PCI: 0000:01:05.0 reg 18 32bit mmio: [d6300000, d630ffff]
Mar 29 14:49:01 Surtur kernel: [    0.984930] PCI: 0000:01:05.0 reg 24 32bit mmio: [d6200000, d62fffff]
Mar 29 14:49:01 Surtur kernel: [    0.984952] pci 0000:01:05.0: supports D1
Mar 29 14:49:01 Surtur kernel: [    0.984954] pci 0000:01:05.0: supports D2
Mar 29 14:49:01 Surtur kernel: [    0.985000] PCI: bridge 0000:00:01.0 io port: [6000, 6fff]
Mar 29 14:49:01 Surtur kernel: [    0.985004] PCI: bridge 0000:00:01.0 32bit mmio: [d6200000, d63fffff]
Mar 29 14:49:01 Surtur kernel: [    0.985010] PCI: bridge 0000:00:01.0 64bit mmio pref: [c0000000, cfffffff]
Mar 29 14:49:01 Surtur kernel: [    0.985065] PCI: bridge 0000:00:04.0 io port: [5000, 5fff]
Mar 29 14:49:01 Surtur kernel: [    0.985068] PCI: bridge 0000:00:04.0 32bit mmio: [d5200000, d61fffff]
Mar 29 14:49:01 Surtur kernel: [    0.985074] PCI: bridge 0000:00:04.0 64bit mmio pref: [d0000000, d0ffffff]
Mar 29 14:49:01 Surtur kernel: [    0.985115] PCI: 0000:04:00.0 reg 10 io port: [3000, 30ff]
Mar 29 14:49:01 Surtur kernel: [    0.985133] PCI: 0000:04:00.0 reg 18 64bit mmio: [d1010000, d1010fff]
Mar 29 14:49:01 Surtur kernel: [    0.985146] PCI: 0000:04:00.0 reg 20 64bit mmio: [d1000000, d100ffff]
Mar 29 14:49:01 Surtur kernel: [    0.985154] PCI: 0000:04:00.0 reg 30 32bit mmio: [fffe0000, ffffffff]
Mar 29 14:49:01 Surtur kernel: [    0.985206] pci 0000:04:00.0: supports D1
Mar 29 14:49:01 Surtur kernel: [    0.985207] pci 0000:04:00.0: supports D2
Mar 29 14:49:01 Surtur kernel: [    0.985210] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 29 14:49:01 Surtur kernel: [    0.985215] pci 0000:04:00.0: PME# disabled
Mar 29 14:49:01 Surtur kernel: [    0.985268] PCI: bridge 0000:00:05.0 io port: [3000, 4fff]
Mar 29 14:49:01 Surtur kernel: [    0.985271] PCI: bridge 0000:00:05.0 32bit mmio: [d4200000, d51fffff]
Mar 29 14:49:01 Surtur kernel: [    0.985276] PCI: bridge 0000:00:05.0 64bit mmio pref: [d1000000, d20fffff]
Mar 29 14:49:01 Surtur kernel: [    0.985466] PCI: 0000:05:00.0 reg 10 64bit mmio: [d3100000, d310ffff]
Mar 29 14:49:01 Surtur kernel: [    0.985852] PCI: bridge 0000:00:06.0 io port: [2000, 2fff]
Mar 29 14:49:01 Surtur kernel: [    0.985856] PCI: bridge 0000:00:06.0 32bit mmio: [d3100000, d41fffff]
Mar 29 14:49:01 Surtur kernel: [    0.985861] PCI: bridge 0000:00:06.0 64bit mmio pref: [d2100000, d30fffff]
Mar 29 14:49:01 Surtur kernel: [    0.985988] PCI: bridge 0000:00:14.4 io port: [1000, 1fff]
Mar 29 14:49:01 Surtur kernel: [    0.986017] bus 00 -> node 0
Mar 29 14:49:01 Surtur kernel: [    0.986027] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Mar 29 14:49:01 Surtur kernel: [    0.986318] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Mar 29 14:49:01 Surtur kernel: [    0.986482] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
Mar 29 14:49:01 Surtur kernel: [    0.986674] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
Mar 29 14:49:01 Surtur kernel: [    0.986855] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
Mar 29 14:49:01 Surtur kernel: [    0.987035] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
Mar 29 14:49:01 Surtur kernel: [    0.987252] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
Mar 29 14:49:01 Surtur kernel: [    1.004193] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Mar 29 14:49:01 Surtur kernel: [    1.004374] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Mar 29 14:49:01 Surtur kernel: [    1.004553] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Mar 29 14:49:01 Surtur kernel: [    1.004735] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Mar 29 14:49:01 Surtur kernel: [    1.004917] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Mar 29 14:49:01 Surtur kernel: [    1.005092] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Mar 29 14:49:01 Surtur kernel: [    1.005267] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Mar 29 14:49:01 Surtur kernel: [    1.005450] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Mar 29 14:49:01 Surtur kernel: [    1.005537] ACPI: Power Resource [PFA1] (off)
Mar 29 14:49:01 Surtur kernel: [    1.005537] Linux Plug and Play Support v0.97 (c) Adam Belay
Mar 29 14:49:01 Surtur kernel: [    1.005537] pnp: PnP ACPI init
Mar 29 14:49:01 Surtur kernel: [    1.005537] ACPI: bus type pnp registered
Mar 29 14:49:01 Surtur kernel: [    1.009152] pnp: PnP ACPI: found 11 devices
Mar 29 14:49:01 Surtur kernel: [    1.009154] ACPI: ACPI bus type pnp unregistered
Mar 29 14:49:01 Surtur kernel: [    1.009157] PnPBIOS: Disabled by ACPI PNP
Mar 29 14:49:01 Surtur kernel: [    1.009190] PCI: Using ACPI for IRQ routing
Mar 29 14:49:01 Surtur kernel: [    1.012045] NET: Registered protocol family 8
Mar 29 14:49:01 Surtur kernel: [    1.012047] NET: Registered protocol family 20
Mar 29 14:49:01 Surtur kernel: [    1.012073] NetLabel: Initializing
Mar 29 14:49:01 Surtur kernel: [    1.012073] NetLabel:  domain hash size = 128
Mar 29 14:49:01 Surtur kernel: [    1.012073] NetLabel:  protocols = UNLABELED CIPSOv4
Mar 29 14:49:01 Surtur kernel: [    1.012073] NetLabel:  unlabeled traffic allowed by default
Mar 29 14:49:01 Surtur kernel: [    1.012073] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Mar 29 14:49:01 Surtur kernel: [    1.012073] hpet0: 4 32-bit timers, 14318180 Hz
Mar 29 14:49:01 Surtur kernel: [    1.014162] tracer: 772 pages allocated for 65536 entries of 48 bytes
Mar 29 14:49:01 Surtur kernel: [    1.014165]    actual entries 65620
Mar 29 14:49:01 Surtur kernel: [    1.014303] AppArmor: AppArmor Filesystem Enabled
Mar 29 14:49:01 Surtur kernel: [    1.014330] ACPI: RTC can wake from S4
Mar 29 14:49:01 Surtur kernel: [    1.016044] Switched to high resolution mode on CPU 0
Mar 29 14:49:01 Surtur kernel: [    1.016370] Switched to high resolution mode on CPU 1
Mar 29 14:49:01 Surtur kernel: [    1.016393] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
Mar 29 14:49:01 Surtur kernel: [    1.016397] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
Mar 29 14:49:01 Surtur kernel: [    1.016409] system 00:09: ioport range 0x400-0x4cf has been reserved
Mar 29 14:49:01 Surtur kernel: [    1.016412] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
Mar 29 14:49:01 Surtur kernel: [    1.016415] system 00:09: ioport range 0x4d6-0x4d6 has been reserved
Mar 29 14:49:01 Surtur kernel: [    1.016418] system 00:09: ioport range 0x680-0x6ff has been reserved
Mar 29 14:49:01 Surtur kernel: [    1.016421] system 00:09: ioport range 0x77a-0x77a has been reserved
Mar 29 14:49:01 Surtur kernel: [    1.016424] system 00:09: ioport range 0xc00-0xc01 has been reserved
Mar 29 14:49:01 Surtur kernel: [    1.016426] system 00:09: ioport range 0xc14-0xc14 has been reserved
Mar 29 14:49:01 Surtur kernel: [    1.016429] system 00:09: ioport range 0xc50-0xc52 has been reserved
Mar 29 14:49:01 Surtur kernel: [    1.016432] system 00:09: ioport range 0xc6c-0xc6c has been reserved
Mar 29 14:49:01 Surtur kernel: [    1.016435] system 00:09: ioport range 0xc6f-0xc6f has been reserved
Mar 29 14:49:01 Surtur kernel: [    1.016438] system 00:09: ioport range 0xcd0-0xcdb has been reserved
Mar 29 14:49:01 Surtur kernel: [    1.016441] system 00:09: ioport range 0x800-0x804 has been reserved
Mar 29 14:49:01 Surtur kernel: [    1.016444] system 00:09: ioport range 0xb00-0xb3f has been reserved
Mar 29 14:49:01 Surtur kernel: [    1.016447] system 00:09: ioport range 0xcdc-0xcdf has been reserved
Mar 29 14:49:01 Surtur kernel: [    1.016454] system 00:0a: iomem range 0xff800000-0xff80ffff has been reserved
Mar 29 14:49:01 Surtur kernel: [    1.016457] system 00:0a: iomem range 0xe0000-0xfffff could not be reserved
Mar 29 14:49:01 Surtur kernel: [    1.016460] system 00:0a: iomem range 0xfeb00000-0xfeb00fff could not be reserved
Mar 29 14:49:01 Surtur kernel: [    1.016464] system 00:0a: iomem range 0xfff00000-0xffffffff could not be reserved
Mar 29 14:49:01 Surtur kernel: [    1.051844] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Mar 29 14:49:01 Surtur kernel: [    1.051848] pci 0000:00:01.0:   IO window: 0x6000-0x6fff
Mar 29 14:49:01 Surtur kernel: [    1.051853] pci 0000:00:01.0:   MEM window: 0xd6200000-0xd63fffff
Mar 29 14:49:01 Surtur kernel: [    1.051857] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
Mar 29 14:49:01 Surtur kernel: [    1.051863] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02
Mar 29 14:49:01 Surtur kernel: [    1.051866] pci 0000:00:04.0:   IO window: 0x5000-0x5fff
Mar 29 14:49:01 Surtur kernel: [    1.051870] pci 0000:00:04.0:   MEM window: 0xd5200000-0xd61fffff
Mar 29 14:49:01 Surtur kernel: [    1.051874] pci 0000:00:04.0:   PREFETCH window: 0x000000d0000000-0x000000d0ffffff
Mar 29 14:49:01 Surtur kernel: [    1.051882] pci 0000:00:05.0: PCI bridge, secondary bus 0000:04
Mar 29 14:49:01 Surtur kernel: [    1.051885] pci 0000:00:05.0:   IO window: 0x3000-0x4fff
Mar 29 14:49:01 Surtur kernel: [    1.051889] pci 0000:00:05.0:   MEM window: 0xd4200000-0xd51fffff
Mar 29 14:49:01 Surtur kernel: [    1.051893] pci 0000:00:05.0:   PREFETCH window: 0x000000d1000000-0x000000d20fffff
Mar 29 14:49:01 Surtur kernel: [    1.051899] pci 0000:00:06.0: PCI bridge, secondary bus 0000:05
Mar 29 14:49:01 Surtur kernel: [    1.051902] pci 0000:00:06.0:   IO window: 0x2000-0x2fff
Mar 29 14:49:01 Surtur kernel: [    1.051906] pci 0000:00:06.0:   MEM window: 0xd3100000-0xd41fffff
Mar 29 14:49:01 Surtur kernel: [    1.051910] pci 0000:00:06.0:   PREFETCH window: 0x000000d2100000-0x000000d30fffff
Mar 29 14:49:01 Surtur kernel: [    1.051915] pci 0000:00:07.0: PCI bridge, secondary bus 0000:06
Mar 29 14:49:01 Surtur kernel: [    1.051918] pci 0000:00:07.0:   IO window: disabled
Mar 29 14:49:01 Surtur kernel: [    1.051921] pci 0000:00:07.0:   MEM window: disabled
Mar 29 14:49:01 Surtur kernel: [    1.051925] pci 0000:00:07.0:   PREFETCH window: disabled
Mar 29 14:49:01 Surtur kernel: [    1.051930] pci 0000:00:14.4: PCI bridge, secondary bus 0000:80
Mar 29 14:49:01 Surtur kernel: [    1.051934] pci 0000:00:14.4:   IO window: 0x1000-0x1fff
Mar 29 14:49:01 Surtur kernel: [    1.051940] pci 0000:00:14.4:   MEM window: disabled
Mar 29 14:49:01 Surtur kernel: [    1.051945] pci 0000:00:14.4:   PREFETCH window: disabled
Mar 29 14:49:01 Surtur kernel: [    1.051959] pci 0000:00:01.0: setting latency timer to 64
Mar 29 14:49:01 Surtur kernel: [    1.051972] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 29 14:49:01 Surtur kernel: [    1.051975] pci 0000:00:04.0: setting latency timer to 64
Mar 29 14:49:01 Surtur kernel: [    1.051982] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Mar 29 14:49:01 Surtur kernel: [    1.051986] pci 0000:00:05.0: setting latency timer to 64
Mar 29 14:49:01 Surtur kernel: [    1.051995] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Mar 29 14:49:01 Surtur kernel: [    1.051999] pci 0000:00:06.0: setting latency timer to 64
Mar 29 14:49:01 Surtur kernel: [    1.052007] pci 0000:00:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Mar 29 14:49:01 Surtur kernel: [    1.052012] pci 0000:00:07.0: setting latency timer to 64
Mar 29 14:49:01 Surtur kernel: [    1.052021] bus: 00 index 0 io port: [0, ffff]
Mar 29 14:49:01 Surtur kernel: [    1.052023] bus: 00 index 1 mmio: [0, ffffffff]
Mar 29 14:49:01 Surtur kernel: [    1.052026] bus: 01 index 0 io port: [6000, 6fff]
Mar 29 14:49:01 Surtur kernel: [    1.052028] bus: 01 index 1 mmio: [d6200000, d63fffff]
Mar 29 14:49:01 Surtur kernel: [    1.052031] bus: 01 index 2 mmio: [c0000000, cfffffff]
Mar 29 14:49:01 Surtur kernel: [    1.052033] bus: 01 index 3 mmio: [0, 0]
Mar 29 14:49:01 Surtur kernel: [    1.052035] bus: 02 index 0 io port: [5000, 5fff]
Mar 29 14:49:01 Surtur kernel: [    1.052038] bus: 02 index 1 mmio: [d5200000, d61fffff]
Mar 29 14:49:01 Surtur kernel: [    1.052040] bus: 02 index 2 mmio: [d0000000, d0ffffff]
Mar 29 14:49:01 Surtur kernel: [    1.052042] bus: 02 index 3 mmio: [0, 0]
Mar 29 14:49:01 Surtur kernel: [    1.052045] bus: 04 index 0 io port: [3000, 4fff]
Mar 29 14:49:01 Surtur kernel: [    1.052047] bus: 04 index 1 mmio: [d4200000, d51fffff]
Mar 29 14:49:01 Surtur kernel: [    1.052049] bus: 04 index 2 mmio: [d1000000, d20fffff]
Mar 29 14:49:01 Surtur kernel: [    1.052052] bus: 04 index 3 mmio: [0, 0]
Mar 29 14:49:01 Surtur kernel: [    1.052054] bus: 05 index 0 io port: [2000, 2fff]
Mar 29 14:49:01 Surtur kernel: [    1.052056] bus: 05 index 1 mmio: [d3100000, d41fffff]
Mar 29 14:49:01 Surtur kernel: [    1.052059] bus: 05 index 2 mmio: [d2100000, d30fffff]
Mar 29 14:49:01 Surtur kernel: [    1.052061] bus: 05 index 3 mmio: [0, 0]
Mar 29 14:49:01 Surtur kernel: [    1.052063] bus: 06 index 0 mmio: [0, 0]
Mar 29 14:49:01 Surtur kernel: [    1.052065] bus: 06 index 1 mmio: [0, 0]
Mar 29 14:49:01 Surtur kernel: [    1.052067] bus: 06 index 2 mmio: [0, 0]
Mar 29 14:49:01 Surtur kernel: [    1.052069] bus: 06 index 3 mmio: [0, 0]
Mar 29 14:49:01 Surtur kernel: [    1.052072] bus: 80 index 0 io port: [1000, 1fff]
Mar 29 14:49:01 Surtur kernel: [    1.052074] bus: 80 index 1 mmio: [0, 0]
Mar 29 14:49:01 Surtur kernel: [    1.052076] bus: 80 index 2 mmio: [0, 0]
Mar 29 14:49:01 Surtur kernel: [    1.052078] bus: 80 index 3 mmio: [0, 0]
Mar 29 14:49:01 Surtur kernel: [    1.052091] NET: Registered protocol family 2
Mar 29 14:49:01 Surtur kernel: [    1.064573] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Mar 29 14:49:01 Surtur kernel: [    1.064851] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Mar 29 14:49:01 Surtur kernel: [    1.065470] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Mar 29 14:49:01 Surtur kernel: [    1.065752] TCP: Hash tables configured (established 131072 bind 65536)
Mar 29 14:49:01 Surtur kernel: [    1.065756] TCP reno registered
Mar 29 14:49:01 Surtur kernel: [    1.068616] NET: Registered protocol family 1
Mar 29 14:49:01 Surtur kernel: [    1.068736] checking if image is initramfs... it is
Mar 29 14:49:01 Surtur kernel: [    1.739220] Freeing initrd memory: 8022k freed
Mar 29 14:49:01 Surtur kernel: [    1.739379] Simple Boot Flag at 0x44 set to 0x1
Mar 29 14:49:01 Surtur kernel: [    1.740456] audit: initializing netlink socket (disabled)
Mar 29 14:49:01 Surtur kernel: [    1.740470] type=2000 audit(1238352509.740:1): initialized
Mar 29 14:49:01 Surtur kernel: [    1.746321] highmem bounce pool size: 64 pages
Mar 29 14:49:01 Surtur kernel: [    1.746327] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Mar 29 14:49:01 Surtur kernel: [    1.748963] VFS: Disk quotas dquot_6.5.1
Mar 29 14:49:01 Surtur kernel: [    1.749060] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Mar 29 14:49:01 Surtur kernel: [    1.749172] msgmni has been set to 1730
Mar 29 14:49:01 Surtur kernel: [    1.749306] io scheduler noop registered
Mar 29 14:49:01 Surtur kernel: [    1.749309] io scheduler anticipatory registered
Mar 29 14:49:01 Surtur kernel: [    1.749311] io scheduler deadline registered
Mar 29 14:49:01 Surtur kernel: [    1.749324] io scheduler cfq registered (default)
Mar 29 14:49:01 Surtur kernel: [    1.924049] pci 0000:01:05.0: Boot video device
Mar 29 14:49:01 Surtur kernel: [    1.924204] pcieport-driver 0000:00:04.0: setting latency timer to 64
Mar 29 14:49:01 Surtur kernel: [    1.924238] pcieport-driver 0000:00:04.0: found MSI capability
Mar 29 14:49:01 Surtur kernel: [    1.924274] pci_express 0000:00:04.0:pcie00: allocate port service
Mar 29 14:49:01 Surtur kernel: [    1.924329] pci_express 0000:00:04.0:pcie02: allocate port service
Mar 29 14:49:01 Surtur kernel: [    1.924428] pcieport-driver 0000:00:05.0: setting latency timer to 64
Mar 29 14:49:01 Surtur kernel: [    1.924459] pcieport-driver 0000:00:05.0: found MSI capability
Mar 29 14:49:01 Surtur kernel: [    1.924490] pci_express 0000:00:05.0:pcie00: allocate port service
Mar 29 14:49:01 Surtur kernel: [    1.924601] pcieport-driver 0000:00:06.0: setting latency timer to 64
Mar 29 14:49:01 Surtur kernel: [    1.924633] pcieport-driver 0000:00:06.0: found MSI capability
Mar 29 14:49:01 Surtur kernel: [    1.924664] pci_express 0000:00:06.0:pcie00: allocate port service
Mar 29 14:49:01 Surtur kernel: [    1.924753] pcieport-driver 0000:00:07.0: setting latency timer to 64
Mar 29 14:49:01 Surtur kernel: [    1.924784] pcieport-driver 0000:00:07.0: found MSI capability
Mar 29 14:49:01 Surtur kernel: [    1.924814] pci_express 0000:00:07.0:pcie00: allocate port service
Mar 29 14:49:01 Surtur kernel: [    1.925204] isapnp: Scanning for PnP cards...
Mar 29 14:49:01 Surtur kernel: [    2.282212] isapnp: No Plug & Play device found
Mar 29 14:49:01 Surtur kernel: [    2.323712] hpet_resources: 0xfed00000 is busy
Mar 29 14:49:01 Surtur kernel: [    2.323832] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Mar 29 14:49:01 Surtur kernel: [    2.326629] brd: module loaded
Mar 29 14:49:01 Surtur kernel: [    2.326723] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Mar 29 14:49:01 Surtur kernel: [    2.326857] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Mar 29 14:49:01 Surtur kernel: [    2.354819] serio: i8042 KBD port at 0x60,0x64 irq 1
Mar 29 14:49:01 Surtur kernel: [    2.354826] serio: i8042 AUX port at 0x60,0x64 irq 12
Mar 29 14:49:01 Surtur kernel: [    2.355162] mice: PS/2 mouse device common for all mice
Mar 29 14:49:01 Surtur kernel: [    2.355319] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Mar 29 14:49:01 Surtur kernel: [    2.355345] rtc0: alarms up to one day, hpet irqs
Mar 29 14:49:01 Surtur kernel: [    2.355470] EISA: Probing bus 0 at eisa.0
Mar 29 14:49:01 Surtur kernel: [    2.355477] Cannot allocate resource for EISA slot 1
Mar 29 14:49:01 Surtur kernel: [    2.355480] Cannot allocate resource for EISA slot 2
Mar 29 14:49:01 Surtur kernel: [    2.355482] Cannot allocate resource for EISA slot 3
Mar 29 14:49:01 Surtur kernel: [    2.355485] Cannot allocate resource for EISA slot 4
Mar 29 14:49:01 Surtur kernel: [    2.355487] Cannot allocate resource for EISA slot 5
Mar 29 14:49:01 Surtur kernel: [    2.355489] Cannot allocate resource for EISA slot 6
Mar 29 14:49:01 Surtur kernel: [    2.355491] Cannot allocate resource for EISA slot 7
Mar 29 14:49:01 Surtur kernel: [    2.355498] EISA: Detected 0 cards.
Mar 29 14:49:01 Surtur kernel: [    2.355501] cpuidle: using governor ladder
Mar 29 14:49:01 Surtur kernel: [    2.355503] cpuidle: using governor menu
Mar 29 14:49:01 Surtur kernel: [    2.355985] TCP cubic registered
Mar 29 14:49:01 Surtur kernel: [    2.356014] Using IPI No-Shortcut mode
Mar 29 14:49:01 Surtur kernel: [    2.356251] registered taskstats version 1
Mar 29 14:49:01 Surtur kernel: [    2.356408]   Magic number: 1:857:848
Mar 29 14:49:01 Surtur kernel: [    2.356496] tty ptyv0: hash matches
Mar 29 14:49:01 Surtur kernel: [    2.356615] rtc_cmos 00:05: setting system clock to 2009-03-29 18:48:31 UTC (1238352511)
Mar 29 14:49:01 Surtur kernel: [    2.356619] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Mar 29 14:49:01 Surtur kernel: [    2.356621] EDD information not available.
Mar 29 14:49:01 Surtur kernel: [    2.356921] Freeing unused kernel memory: 428k freed
Mar 29 14:49:01 Surtur kernel: [    2.356990] Write protecting the kernel text: 2580k
Mar 29 14:49:01 Surtur kernel: [    2.357030] Write protecting the kernel read-only data: 940k
Mar 29 14:49:01 Surtur kernel: [    2.388357] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Mar 29 14:49:01 Surtur kernel: [    2.556683] fuse init (API version 7.9)
Mar 29 14:49:01 Surtur kernel: [    2.580860] ACPI: Transitioning device [FAN1] to D3
Mar 29 14:49:01 Surtur kernel: [    2.580936] fan PNP0C0B:00: registered as cooling_device0
Mar 29 14:49:01 Surtur kernel: [    2.580943] ACPI: Fan [FAN1] (off)
Mar 29 14:49:01 Surtur kernel: [    2.648022] processor ACPI0007:00: registered as cooling_device1
Mar 29 14:49:01 Surtur kernel: [    2.648029] ACPI: Processor [CPU0] (supports 8 throttling states)
Mar 29 14:49:01 Surtur kernel: [    2.652528] processor ACPI0007:01: registered as cooling_device2
Mar 29 14:49:01 Surtur kernel: [    2.661301] thermal LNXTHERM:01: registered as thermal_zone0
Mar 29 14:49:01 Surtur kernel: [    2.673755] ACPI: Thermal Zone [THZN] (56 C)
Mar 29 14:49:01 Surtur kernel: [    3.060769] No dock devices found.
Mar 29 14:49:01 Surtur kernel: [    3.065758] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Mar 29 14:49:01 Surtur kernel: [    3.065777] r8169 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Mar 29 14:49:01 Surtur kernel: [    3.065796] r8169 0000:04:00.0: setting latency timer to 64
Mar 29 14:49:01 Surtur kernel: [    3.066128] eth0: RTL8102e at 0xf8844000, 00:1e:33:97:e3:dc, XID 34a00000 IRQ 219
Mar 29 14:49:01 Surtur kernel: [    3.100469] SCSI subsystem initialized
Mar 29 14:49:01 Surtur kernel: [    3.138168] libata version 3.00 loaded.
Mar 29 14:49:01 Surtur kernel: [    3.139865] usbcore: registered new interface driver usbfs
Mar 29 14:49:01 Surtur kernel: [    3.139888] usbcore: registered new interface driver hub
Mar 29 14:49:01 Surtur kernel: [    3.139936] usbcore: registered new device driver usb
Mar 29 14:49:01 Surtur kernel: [    3.140048] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 29 14:49:01 Surtur kernel: [    3.140103] pata_acpi 0000:00:14.1: setting latency timer to 64
Mar 29 14:49:01 Surtur kernel: [    3.165701] scsi0 : pata_atiixp
Mar 29 14:49:01 Surtur kernel: [    3.165832] scsi1 : pata_atiixp
Mar 29 14:49:01 Surtur kernel: [    3.166951] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x7000 irq 14
Mar 29 14:49:01 Surtur kernel: [    3.166955] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x7008 irq 15
Mar 29 14:49:01 Surtur kernel: [    3.186129] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Mar 29 14:49:01 Surtur kernel: [    3.488440] ahci 0000:00:11.0: version 3.0
Mar 29 14:49:01 Surtur kernel: [    3.488470] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Mar 29 14:49:01 Surtur kernel: [    3.488641] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
Mar 29 14:49:01 Surtur kernel: [    3.488645] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck led clo pmp pio 
Mar 29 14:49:01 Surtur kernel: [    3.489186] scsi2 : ahci
Mar 29 14:49:01 Surtur kernel: [    3.490086] scsi3 : ahci
Mar 29 14:49:01 Surtur kernel: [    3.490183] scsi4 : ahci
Mar 29 14:49:01 Surtur kernel: [    3.490242] scsi5 : ahci
Mar 29 14:49:01 Surtur kernel: [    3.490303] scsi6 : ahci
Mar 29 14:49:01 Surtur kernel: [    3.490370] scsi7 : ahci
Mar 29 14:49:01 Surtur kernel: [    3.490556] ata3: SATA max UDMA/133 abar m1024@0xd6408000 port 0xd6408100 irq 22
Mar 29 14:49:01 Surtur kernel: [    3.490560] ata4: SATA max UDMA/133 abar m1024@0xd6408000 port 0xd6408180 irq 22
Mar 29 14:49:01 Surtur kernel: [    3.490564] ata5: SATA max UDMA/133 abar m1024@0xd6408000 port 0xd6408200 irq 22
Mar 29 14:49:01 Surtur kernel: [    3.490568] ata6: SATA max UDMA/133 abar m1024@0xd6408000 port 0xd6408280 irq 22
Mar 29 14:49:01 Surtur kernel: [    3.490572] ata7: SATA max UDMA/133 abar m1024@0xd6408000 port 0xd6408300 irq 22
Mar 29 14:49:01 Surtur kernel: [    3.490576] ata8: SATA max UDMA/133 abar m1024@0xd6408000 port 0xd6408380 irq 22
Mar 29 14:49:01 Surtur kernel: [    3.972025] ata3: softreset failed (device not ready)
Mar 29 14:49:01 Surtur kernel: [    3.972032] ata3: failed due to HW bug, retry pmp=0
Mar 29 14:49:01 Surtur kernel: [    4.136035] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar 29 14:49:01 Surtur kernel: [    4.183713] ata3.00: ATA-8: WDC WD2500BEVS-26UST0, 01.01A01, max UDMA/133
Mar 29 14:49:01 Surtur kernel: [    4.183718] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Mar 29 14:49:01 Surtur kernel: [    4.184584] ata3.00: configured for UDMA/133
Mar 29 14:49:01 Surtur kernel: [    4.504538] ata4: SATA link down (SStatus 0 SControl 300)
Mar 29 14:49:01 Surtur kernel: [    4.988024] ata5: softreset failed (device not ready)
Mar 29 14:49:01 Surtur kernel: [    4.988029] ata5: failed due to HW bug, retry pmp=0
Mar 29 14:49:01 Surtur kernel: [    5.152036] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar 29 14:49:01 Surtur kernel: [    5.167887] ata5.00: ATAPI: TSSTcorp CDDVDW TS-L633P, TO01, max UDMA/100, ATAPI AN
Mar 29 14:49:01 Surtur kernel: [    5.181807] ata5.00: configured for UDMA/100
Mar 29 14:49:01 Surtur kernel: [    5.500047] ata6: SATA link down (SStatus 0 SControl 300)
Mar 29 14:49:01 Surtur kernel: [    5.820038] ata7: SATA link down (SStatus 0 SControl 300)
Mar 29 14:49:01 Surtur kernel: [    6.140040] ata8: SATA link down (SStatus 0 SControl 300)
Mar 29 14:49:01 Surtur kernel: [    6.140154] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-2 01.0 PQ: 0 ANSI: 5
Mar 29 14:49:01 Surtur kernel: [    6.142890] scsi 4:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633P  TO01 PQ: 0 ANSI: 5
Mar 29 14:49:01 Surtur kernel: [    6.142993] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 29 14:49:01 Surtur kernel: [    6.143010] ohci_hcd 0000:00:12.0: setting latency timer to 64
Mar 29 14:49:01 Surtur kernel: [    6.143015] ohci_hcd 0000:00:12.0: OHCI Host Controller
Mar 29 14:49:01 Surtur kernel: [    6.143074] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 1
Mar 29 14:49:01 Surtur kernel: [    6.143112] ohci_hcd 0000:00:12.0: irq 16, io mem 0xd6407000
Mar 29 14:49:01 Surtur kernel: [    6.200659] usb usb1: configuration #1 chosen from 1 choice
Mar 29 14:49:01 Surtur kernel: [    6.200687] hub 1-0:1.0: USB hub found
Mar 29 14:49:01 Surtur kernel: [    6.200703] hub 1-0:1.0: 3 ports detected
Mar 29 14:49:01 Surtur kernel: [    6.306251] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 29 14:49:01 Surtur kernel: [    6.306270] ohci_hcd 0000:00:12.1: setting latency timer to 64
Mar 29 14:49:01 Surtur kernel: [    6.306275] ohci_hcd 0000:00:12.1: OHCI Host Controller
Mar 29 14:49:01 Surtur kernel: [    6.306503] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 2
Mar 29 14:49:01 Surtur kernel: [    6.306529] ohci_hcd 0000:00:12.1: irq 16, io mem 0xd6406000
Mar 29 14:49:01 Surtur kernel: [    6.364182] usb usb2: configuration #1 chosen from 1 choice
Mar 29 14:49:01 Surtur kernel: [    6.364213] hub 2-0:1.0: USB hub found
Mar 29 14:49:01 Surtur kernel: [    6.364229] hub 2-0:1.0: 3 ports detected
Mar 29 14:49:01 Surtur kernel: [    6.468237] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Mar 29 14:49:01 Surtur kernel: [    6.468255] ehci_hcd 0000:00:12.2: setting latency timer to 64
Mar 29 14:49:01 Surtur kernel: [    6.468260] ehci_hcd 0000:00:12.2: EHCI Host Controller
Mar 29 14:49:01 Surtur kernel: [    6.468285] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 3
Mar 29 14:49:01 Surtur kernel: [    6.468314] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
Mar 29 14:49:01 Surtur kernel: [    6.468336] ehci_hcd 0000:00:12.2: debug port 1
Mar 29 14:49:01 Surtur kernel: [    6.468358] ehci_hcd 0000:00:12.2: irq 17, io mem 0xd6408500
Mar 29 14:49:01 Surtur kernel: [    6.480021] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Mar 29 14:49:01 Surtur kernel: [    6.480114] usb usb3: configuration #1 chosen from 1 choice
Mar 29 14:49:01 Surtur kernel: [    6.480145] hub 3-0:1.0: USB hub found
Mar 29 14:49:01 Surtur kernel: [    6.480154] hub 3-0:1.0: 6 ports detected
Mar 29 14:49:01 Surtur kernel: [    6.584261] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Mar 29 14:49:01 Surtur kernel: [    6.584279] ohci_hcd 0000:00:13.0: setting latency timer to 64
Mar 29 14:49:01 Surtur kernel: [    6.584283] ohci_hcd 0000:00:13.0: OHCI Host Controller
Mar 29 14:49:01 Surtur kernel: [    6.584308] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 4
Mar 29 14:49:01 Surtur kernel: [    6.584335] ohci_hcd 0000:00:13.0: irq 18, io mem 0xd6405000
Mar 29 14:49:01 Surtur kernel: [    6.644158] usb usb4: configuration #1 chosen from 1 choice
Mar 29 14:49:01 Surtur kernel: [    6.644188] hub 4-0:1.0: USB hub found
Mar 29 14:49:01 Surtur kernel: [    6.644203] hub 4-0:1.0: 3 ports detected
Mar 29 14:49:01 Surtur kernel: [    6.852249] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Mar 29 14:49:01 Surtur kernel: [    6.852266] ohci_hcd 0000:00:13.1: setting latency timer to 64
Mar 29 14:49:01 Surtur kernel: [    6.852271] ohci_hcd 0000:00:13.1: OHCI Host Controller
Mar 29 14:49:01 Surtur kernel: [    6.852297] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 5
Mar 29 14:49:01 Surtur kernel: [    6.852317] ohci_hcd 0000:00:13.1: irq 18, io mem 0xd6404000
Mar 29 14:49:01 Surtur kernel: [    6.912119] usb usb5: configuration #1 chosen from 1 choice
Mar 29 14:49:01 Surtur kernel: [    6.912147] hub 5-0:1.0: USB hub found
Mar 29 14:49:01 Surtur kernel: [    6.912159] hub 5-0:1.0: 3 ports detected
Mar 29 14:49:01 Surtur kernel: [    6.988025] usb 4-2: new full speed USB device using ohci_hcd and address 2
Mar 29 14:49:01 Surtur kernel: [    7.124336] ehci_hcd 0000:00:13.2: power state changed by ACPI to D0
Mar 29 14:49:01 Surtur kernel: [    7.124352] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Mar 29 14:49:01 Surtur kernel: [    7.124369] ehci_hcd 0000:00:13.2: setting latency timer to 64
Mar 29 14:49:01 Surtur kernel: [    7.124374] ehci_hcd 0000:00:13.2: EHCI Host Controller
Mar 29 14:49:01 Surtur kernel: [    7.124401] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 6
Mar 29 14:49:01 Surtur kernel: [    7.124429] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
Mar 29 14:49:01 Surtur kernel: [    7.124451] ehci_hcd 0000:00:13.2: debug port 1
Mar 29 14:49:01 Surtur kernel: [    7.124473] ehci_hcd 0000:00:13.2: irq 19, io mem 0xd6408400
Mar 29 14:49:01 Surtur kernel: [    7.128037] usb 4-2: device descriptor read/64, error -62
Mar 29 14:49:01 Surtur kernel: [    7.140027] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Mar 29 14:49:01 Surtur kernel: [    7.140180] usb usb6: configuration #1 chosen from 1 choice
Mar 29 14:49:01 Surtur kernel: [    7.140209] hub 6-0:1.0: USB hub found
Mar 29 14:49:01 Surtur kernel: [    7.140220] hub 6-0:1.0: 6 ports detected
Mar 29 14:49:01 Surtur kernel: [    7.292032] hub 4-0:1.0: unable to enumerate USB device on port 2
Mar 29 14:49:01 Surtur kernel: [    7.366501] scsi 2:0:0:0: Attached scsi generic sg0 type 0
Mar 29 14:49:01 Surtur kernel: [    7.366549] scsi 4:0:0:0: Attached scsi generic sg1 type 5
Mar 29 14:49:01 Surtur kernel: [    7.436699] Driver 'sr' needs updating - please use bus_type methods
Mar 29 14:49:01 Surtur kernel: [    7.440323] Driver 'sd' needs updating - please use bus_type methods
Mar 29 14:49:01 Surtur kernel: [    7.440450] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Mar 29 14:49:01 Surtur kernel: [    7.440467] sd 2:0:0:0: [sda] Write Protect is off
Mar 29 14:49:01 Surtur kernel: [    7.440470] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Mar 29 14:49:01 Surtur kernel: [    7.440530] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 29 14:49:01 Surtur kernel: [    7.440604] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Mar 29 14:49:01 Surtur kernel: [    7.440618] sd 2:0:0:0: [sda] Write Protect is off
Mar 29 14:49:01 Surtur kernel: [    7.440621] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Mar 29 14:49:01 Surtur kernel: [    7.440646] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 29 14:49:01 Surtur kernel: [    7.440650]  sda:sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Mar 29 14:49:01 Surtur kernel: [    7.446204] Uniform CD-ROM driver Revision: 3.20
Mar 29 14:49:01 Surtur kernel: [    7.446305] sr 4:0:0:0: Attached scsi CD-ROM sr0
Mar 29 14:49:01 Surtur kernel: [    7.487654]  sda1 sda2 sda3 < sda5 sda6 sda7 >
Mar 29 14:49:01 Surtur kernel: [    7.553654] sd 2:0:0:0: [sda] Attached SCSI disk
Mar 29 14:49:01 Surtur kernel: [    7.660536] usb 6-2: new high speed USB device using ehci_hcd and address 2
Mar 29 14:49:01 Surtur kernel: [    7.831781] usb 6-2: configuration #1 chosen from 1 choice
Mar 29 14:49:01 Surtur kernel: [    7.944030] usb 6-4: new high speed USB device using ehci_hcd and address 3
Mar 29 14:49:01 Surtur kernel: [    7.970931] PM: Starting manual resume from disk
Mar 29 14:49:01 Surtur kernel: [    7.970935] PM: Resume from partition 8:2
Mar 29 14:49:01 Surtur kernel: [    7.970937] PM: Checking hibernation image.
Mar 29 14:49:01 Surtur kernel: [    7.971186] PM: Resume from disk failed.
Mar 29 14:49:01 Surtur kernel: [    7.989104] EXT3-fs: INFO: recovery required on readonly filesystem.
Mar 29 14:49:01 Surtur kernel: [    7.989109] EXT3-fs: write access will be enabled during recovery.
Mar 29 14:49:01 Surtur kernel: [    8.087737] usb 6-4: configuration #1 chosen from 1 choice
Mar 29 14:49:01 Surtur kernel: [    8.103234] usbcore: registered new interface driver libusual
Mar 29 14:49:01 Surtur kernel: [    8.110966] Initializing USB Mass Storage driver...
Mar 29 14:49:01 Surtur kernel: [    8.111081] scsi8 : SCSI emulation for USB Mass Storage devices
Mar 29 14:49:01 Surtur kernel: [    8.111176] usbcore: registered new interface driver usb-storage
Mar 29 14:49:01 Surtur kernel: [    8.111180] USB Mass Storage support registered.
Mar 29 14:49:01 Surtur kernel: [    8.111320] usb-storage: device found at 3
Mar 29 14:49:01 Surtur kernel: [    8.111322] usb-storage: waiting for device to settle before scanning
Mar 29 14:49:01 Surtur kernel: [    8.536424] kjournald starting.  Commit interval 5 seconds
Mar 29 14:49:01 Surtur kernel: [    8.536447] EXT3-fs: recovery complete.
Mar 29 14:49:01 Surtur kernel: [    8.539186] EXT3-fs: mounted filesystem with ordered data mode.
Mar 29 14:49:01 Surtur kernel: [   13.108333] usb-storage: device scan complete
Mar 29 14:49:01 Surtur kernel: [   13.110299] scsi 8:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
Mar 29 14:49:01 Surtur kernel: [   13.113240] sd 8:0:0:0: [sdb] Attached SCSI removable disk
Mar 29 14:49:01 Surtur kernel: [   13.113362] sd 8:0:0:0: Attached scsi generic sg2 type 0
Mar 29 14:49:01 Surtur kernel: [   15.059972] udevd version 124 started
Mar 29 14:49:01 Surtur kernel: [   15.876693] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar 29 14:49:01 Surtur kernel: [   15.893336] shpchp: HPC vendor_id 1022 device_id 9602 ss_vid 0 ss_did 0
Mar 29 14:49:01 Surtur kernel: [   15.893342] shpchp: shpc_init: cannot reserve MMIO region
Mar 29 14:49:01 Surtur kernel: [   15.893407] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Mar 29 14:49:01 Surtur kernel: [   15.895741] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
Mar 29 14:49:01 Surtur kernel: [   16.048749] input: PC Speaker as /devices/platform/pcspkr/input/input2
Mar 29 14:49:01 Surtur kernel: [   16.116752] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Mar 29 14:49:01 Surtur kernel: [   16.136538] ACPI: Power Button (FF) [PWRF]
Mar 29 14:49:01 Surtur kernel: [   16.136666] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
Mar 29 14:49:01 Surtur kernel: [   16.168531] ACPI: Power Button (CM) [PWRB]
Mar 29 14:49:01 Surtur kernel: [   16.168640] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input5
Mar 29 14:49:01 Surtur kernel: [   16.170425] ACPI: Lid Switch [LID]
Mar 29 14:49:01 Surtur kernel: [   16.170634] ACPI: AC Adapter [ADP0] (on-line)
Mar 29 14:49:01 Surtur kernel: [   16.204912] ACPI: Battery Slot [BAT0] (battery present)
Mar 29 14:49:01 Surtur kernel: [   16.622436] acpi device:04: registered as cooling_device3
Mar 29 14:49:01 Surtur kernel: [   16.622702] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:02/input/input6
Mar 29 14:49:01 Surtur kernel: [   16.641910] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Mar 29 14:49:01 Surtur kernel: [   16.672470] Linux agpgart interface v0.103
Mar 29 14:49:01 Surtur kernel: [   16.764653] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Mar 29 14:49:01 Surtur kernel: [   16.826181] [fglrx] Maximum main memory to use for locked dma buffers: 2642 MBytes.
Mar 29 14:49:01 Surtur kernel: [   16.826262] [fglrx]   vendor: 1002 device: 9613 count: 1
Mar 29 14:49:01 Surtur kernel: [   16.828785] [fglrx] ioport: bar 1, base 0x6000, size: 0x100
Mar 29 14:49:01 Surtur kernel: [   16.828805] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Mar 29 14:49:01 Surtur kernel: [   16.828811] pci 0000:01:05.0: setting latency timer to 64
Mar 29 14:49:01 Surtur kernel: [   16.829777] [fglrx] Driver built-in PAT support is enabled successfully
Mar 29 14:49:01 Surtur kernel: [   16.831576] [fglrx] module loaded - fglrx 8.58.2 [Feb  4 2009] with 1 minors
Mar 29 14:49:01 Surtur kernel: [   16.880744] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
Mar 29 14:49:01 Surtur kernel: [   17.096255] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 29 14:49:01 Surtur kernel: [   17.096286] HDA Intel 0000:00:14.2: setting latency timer to 64
Mar 29 14:49:01 Surtur kernel: [   17.129830] hda_codec: Unknown model for ALC268, trying auto-probe from BIOS...
Mar 29 14:49:01 Surtur kernel: [   17.152198] Linux video capture interface: v2.00
Mar 29 14:49:01 Surtur kernel: [   17.245008] uvcvideo: Found UVC 1.00 device CNF7051 (04f2:b070)
Mar 29 14:49:01 Surtur kernel: [   17.246512] input: CNF7051 as /devices/pci0000:00/0000:00:13.2/usb6/6-2/6-2:1.0/input/input7
Mar 29 14:49:01 Surtur kernel: [   17.282300] ndiswrapper (check_nt_hdr:156): kernel is 32-bit, but Windows driver is not 32-bit;bad magic: 020B
Mar 29 14:49:01 Surtur kernel: [   17.282307] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netathwx'
Mar 29 14:49:01 Surtur kernel: [   17.283016] ndiswrapper (load_wrap_driver:108): couldn't load driver netathwx; check system log for messages from 'loadndisdriver'
Mar 29 14:49:01 Surtur kernel: [   17.392387] usbcore: registered new interface driver uvcvideo
Mar 29 14:49:01 Surtur kernel: [   17.392380] usbcore: registered new interface driver ndiswrapper
Mar 29 14:49:01 Surtur kernel: [   17.392423] USB Video Class driver (v0.1.0)
Mar 29 14:49:01 Surtur kernel: [   17.927567] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1a0b1, caps: 0xd04711/0xa04000
Mar 29 14:49:01 Surtur kernel: [   17.927574] synaptics: Toshiba Satellite L355D detected, limiting rate to 40pps.
Mar 29 14:49:01 Surtur kernel: [   18.001858] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
Mar 29 14:49:01 Surtur kernel: [   19.054552] lp: driver loaded but no devices found
Mar 29 14:49:01 Surtur kernel: [   19.140569] cfg80211: Using static regulatory domain info
Mar 29 14:49:01 Surtur kernel: [   19.140573] cfg80211: Regulatory domain: US
Mar 29 14:49:01 Surtur kernel: [   19.140575] ^I(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Mar 29 14:49:01 Surtur kernel: [   19.140578] ^I(2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)
Mar 29 14:49:01 Surtur kernel: [   19.140581] ^I(5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
Mar 29 14:49:01 Surtur kernel: [   19.140584] ^I(5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
Mar 29 14:49:01 Surtur kernel: [   19.140587] ^I(5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
Mar 29 14:49:01 Surtur kernel: [   19.140589] ^I(5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
Mar 29 14:49:01 Surtur kernel: [   19.140592] ^I(5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm)
Mar 29 14:49:01 Surtur kernel: [   19.141129] cfg80211: Calling CRDA for country: US
Mar 29 14:49:01 Surtur kernel: [   19.185364] ath5k 0000:05:00.0: enabling device (0000 -> 0002)
Mar 29 14:49:01 Surtur kernel: [   19.185375] ath5k 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Mar 29 14:49:01 Surtur kernel: [   19.185388] ath5k 0000:05:00.0: setting latency timer to 64
Mar 29 14:49:01 Surtur kernel: [   19.185429] ath5k 0000:05:00.0: registered as 'phy0'
Mar 29 14:49:01 Surtur kernel: [   19.255772] phy0: Selected rate control algorithm 'minstrel'
Mar 29 14:49:01 Surtur kernel: [   19.330053] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
Mar 29 14:49:01 Surtur kernel: [   19.463815] Adding 9767512k swap on /dev/sda2.  Priority:-1 extents:1 across:9767512k
Mar 29 14:49:01 Surtur kernel: [   24.526187] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
Mar 29 14:49:01 Surtur kernel: [   24.526437] EXT3 FS on sda1, internal journal
Mar 29 14:49:01 Surtur kernel: [   30.625899] kjournald starting.  Commit interval 5 seconds
Mar 29 14:49:01 Surtur kernel: [   30.626173] EXT3 FS on sda7, internal journal
Mar 29 14:49:01 Surtur kernel: [   30.626181] EXT3-fs: mounted filesystem with ordered data mode.
Mar 29 14:49:01 Surtur kernel: [   30.697129] kjournald starting.  Commit interval 5 seconds
Mar 29 14:49:01 Surtur kernel: [   30.697381] EXT3 FS on sda5, internal journal
Mar 29 14:49:01 Surtur kernel: [   30.697386] EXT3-fs: mounted filesystem with ordered data mode.
Mar 29 14:49:01 Surtur kernel: [   30.745882] kjournald starting.  Commit interval 5 seconds
Mar 29 14:49:01 Surtur kernel: [   30.746165] EXT3 FS on sda6, internal journal
Mar 29 14:49:01 Surtur kernel: [   30.746170] EXT3-fs: mounted filesystem with ordered data mode.
Mar 29 14:49:01 Surtur kernel: [   30.942919] type=1505 audit(1238352540.057:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4469
Mar 29 14:49:01 Surtur kernel: [   31.144473] type=1505 audit(1238352540.260:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4474
Mar 29 14:49:01 Surtur kernel: [   31.144727] type=1505 audit(1238352540.260:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4474
Mar 29 14:49:01 Surtur kernel: [   31.282368] ip_tables: (C) 2000-2006 Netfilter Core Team
Mar 29 14:49:01 Surtur kernel: [   31.764860] ACPI: WMI: Mapper loaded
Mar 29 14:49:01 Surtur kernel: [   32.137347] powernow-k8: Found 1 AMD Turion(tm) X2 Dual-Core Mobile RM-72 processors (2 cpu cores) (version 2.20.00)
Mar 29 14:49:01 Surtur kernel: [   32.137396] powernow-k8:    0 : pstate 0 (2100 MHz)
Mar 29 14:49:01 Surtur kernel: [   32.137400] powernow-k8:    1 : pstate 1 (1050 MHz)
Mar 29 14:49:01 Surtur kernel: [   32.137403] powernow-k8:    2 : pstate 2 (525 MHz)
Mar 29 14:49:01 Surtur avahi-daemon[5081]: Found user 'avahi' (UID 110) and group 'avahi' (GID 121).
Mar 29 14:49:01 Surtur avahi-daemon[5081]: Successfully dropped root privileges.
Mar 29 14:49:01 Surtur kernel: [   32.773811] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Mar 29 14:49:01 Surtur avahi-daemon[5081]: avahi-daemon 0.6.23 starting up.
Mar 29 14:49:01 Surtur avahi-daemon[5081]: Successfully called chroot().
Mar 29 14:49:01 Surtur avahi-daemon[5081]: Successfully dropped remaining capabilities.
Mar 29 14:49:01 Surtur avahi-daemon[5081]: No service file found in /etc/avahi/services.
Mar 29 14:49:01 Surtur avahi-daemon[5081]: Network interface enumeration completed.
Mar 29 14:49:01 Surtur avahi-daemon[5081]: Registering HINFO record with values 'I686'/'LINUX'.
Mar 29 14:49:01 Surtur avahi-daemon[5081]: Server startup complete. Host name is Surtur.local. Local service cookie is 2736881766.
Mar 29 14:49:01 Surtur kernel: [   32.846098] apm: BIOS not found.
Mar 29 14:49:02 Surtur atieventsd[5116]: ATI External Events Daemon started... 
Mar 29 14:49:02 Surtur atieventsd[5116]: Event daemon control socket created 
Mar 29 14:49:02 Surtur acpid: client connected from 5116[0:0] 
Mar 29 14:49:02 Surtur atieventsd[5116]: acpid connection established 
Mar 29 14:49:02 Surtur kernel: [   33.076064] ppdev: user-space parallel port driver
Mar 29 14:49:04 Surtur acpid: client connected from 5416[111:122] 
Mar 29 14:49:05 Surtur bluetoothd[5470]: Bluetooth daemon
Mar 29 14:49:05 Surtur kernel: [   36.064029] Bluetooth: Core ver 2.13
Mar 29 14:49:05 Surtur kernel: [   36.065762] NET: Registered protocol family 31
Mar 29 14:49:05 Surtur kernel: [   36.065776] Bluetooth: HCI device and connection manager initialized
Mar 29 14:49:05 Surtur kernel: [   36.065789] Bluetooth: HCI socket layer initialized
Mar 29 14:49:05 Surtur bluetoothd[5470]: Starting SDP server
Mar 29 14:49:05 Surtur kernel: [   36.128747] Bluetooth: L2CAP ver 2.11
Mar 29 14:49:05 Surtur kernel: [   36.128769] Bluetooth: L2CAP socket layer initialized
Mar 29 14:49:05 Surtur bluetoothd[5470]: Starting experimental netlink support
Mar 29 14:49:05 Surtur bluetoothd[5470]: Failed to find Bluetooth netlink family
Mar 29 14:49:05 Surtur bluetoothd[5470]: Can't init plugin /usr/lib/bluetooth/plugins/netlink.so
Mar 29 14:49:05 Surtur kernel: [   36.199854] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Mar 29 14:49:05 Surtur kernel: [   36.199876] Bluetooth: BNEP filters: protocol multicast
Mar 29 14:49:05 Surtur kernel: [   36.271733] Bridge firewalling registered
Mar 29 14:49:05 Surtur bluetoothd[5470]: bridge pan0 created
Mar 29 14:49:05 Surtur kernel: [   36.309176] Bluetooth: SCO (Voice Link) ver 0.6
Mar 29 14:49:05 Surtur kernel: [   36.309198] Bluetooth: SCO socket layer initialized
Mar 29 14:49:05 Surtur kernel: [   36.395758] Bluetooth: RFCOMM socket layer initialized
Mar 29 14:49:05 Surtur kernel: [   36.397591] Bluetooth: RFCOMM TTY layer initialized
Mar 29 14:49:05 Surtur kernel: [   36.397605] Bluetooth: RFCOMM ver 1.10
Mar 29 14:49:05 Surtur NetworkManager: <info>  starting... 
Mar 29 14:49:05 Surtur NetworkManager: <info>  eth0: driver is 'r8169'. 
Mar 29 14:49:05 Surtur NetworkManager: <info>  Found new Ethernet device 'eth0'. 
Mar 29 14:49:05 Surtur NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_1e_33_97_e3_dc 
Mar 29 14:49:05 Surtur NetworkManager: <info>  wlan0: driver is 'ath5k'. 
Mar 29 14:49:05 Surtur NetworkManager: <info>  wlan0: driver supports SSID scans (scan_capa 0x01). 
Mar 29 14:49:05 Surtur NetworkManager: <info>  Found new 802.11 WiFi device 'wlan0'. 
Mar 29 14:49:05 Surtur NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_21_63_f5_3a_8c 
Mar 29 14:49:05 Surtur NetworkManager: <info>  Trying to start the supplicant... 
Mar 29 14:49:05 Surtur NetworkManager: <info>  Trying to start the system settings daemon... 
Mar 29 14:49:05 Surtur NetworkManager: <info>  (wlan0): supplicant manager is now in state 1 (from 0). 
Mar 29 14:49:05 Surtur nm-system-settings:    SCPlugin-Ifupdown: init!
Mar 29 14:49:05 Surtur nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Mar 29 14:49:05 Surtur nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Mar 29 14:49:05 Surtur nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_1e_33_97_e3_dc, iface: eth0): not well known
Mar 29 14:49:05 Surtur nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_21_63_f5_3a_8c, iface: wlan0): not well known
Mar 29 14:49:05 Surtur nm-system-settings:    SCPlugin-Ifupdown: end _init.
Mar 29 14:49:05 Surtur nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Mar 29 14:49:05 Surtur nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Mar 29 14:49:05 Surtur nm-system-settings:    SCPlugin-Ifupdown: (151413024) ... get_connections.
Mar 29 14:49:05 Surtur nm-system-settings:    SCPlugin-Ifupdown: (151413024) ... get_connections (managed=false): return empty list.
Mar 29 14:49:05 Surtur nm-system-settings:    Ifupdown: get unmanaged devices count: 0
Mar 29 14:49:07 Surtur acpid: client connected from 5578[0:0] 
Mar 29 14:49:08 Surtur anacron[5627]: Anacron 2.3 started on 2009-03-29
Mar 29 14:49:08 Surtur anacron[5627]: Normal exit (0 jobs run)
Mar 29 14:49:08 Surtur /usr/sbin/cron[5670]: (CRON) INFO (pidfile fd = 3)
Mar 29 14:49:08 Surtur /usr/sbin/cron[5671]: (CRON) STARTUP (fork ok)
Mar 29 14:49:08 Surtur /usr/sbin/cron[5671]: (CRON) INFO (Running @reboot jobs)
Mar 29 14:49:09 Surtur NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Mar 29 14:49:09 Surtur NetworkManager: <info>  (eth0): bringing up device. 
Mar 29 14:49:09 Surtur kernel: [   40.549613] r8169: eth0: link down
Mar 29 14:49:09 Surtur NetworkManager: <info>  (eth0): preparing device. 
Mar 29 14:49:09 Surtur NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Mar 29 14:49:09 Surtur NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Mar 29 14:49:09 Surtur NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Mar 29 14:49:09 Surtur NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
Mar 29 14:49:09 Surtur NetworkManager: <info>  (eth0): device state change: 2 -> 3 
Mar 29 14:49:09 Surtur NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Mar 29 14:49:09 Surtur NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
Mar 29 14:49:09 Surtur NetworkManager: <info>  (wlan0): bringing up device. 
Mar 29 14:49:09 Surtur nm-system-settings: Adding default connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_1e_33_97_e3_dc
Mar 29 14:49:09 Surtur NetworkManager: <info>  (wlan0): preparing device. 
Mar 29 14:49:09 Surtur NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
Mar 29 14:49:09 Surtur NetworkManager: <info>  (eth0): carrier now OFF (device state 3) 
Mar 29 14:49:09 Surtur NetworkManager: <info>  (eth0): device state change: 3 -> 2 
Mar 29 14:49:09 Surtur NetworkManager: <info>  (eth0): deactivating device (reason: 0). 
Mar 29 14:49:09 Surtur NetworkManager: <WARN>  auto_activate_device(): Connection 'Auto eth0' auto-activation failed: (2) Device not managed by NetworkManager 
Mar 29 14:49:09 Surtur NetworkManager: <info>  (wlan0): device state change: 2 -> 3 
Mar 29 14:49:10 Surtur kernel: [   41.070416] [fglrx] GART Table is not in FRAME_BUFFER range 
Mar 29 14:49:10 Surtur kernel: [   41.086775] [fglrx] Firegl kernel thread PID: 5762
Mar 29 14:49:10 Surtur kernel: [   41.094937] NET: Registered protocol family 17
Mar 29 14:49:10 Surtur NetworkManager: <info>  (wlan0): supplicant interface state change: 1 -> 2. 
Mar 29 14:49:10 Surtur kernel: [   41.101937] APIC error on CPU1: 00(08)
Mar 29 14:49:10 Surtur kernel: [   41.101948] APIC error on CPU0: 00(08)
Mar 29 14:49:10 Surtur kernel: [   41.120615] [fglrx] Gart USWC size:1327 M.
Mar 29 14:49:10 Surtur kernel: [   41.120620] [fglrx] Gart cacheable size:60 M.
Mar 29 14:49:10 Surtur kernel: [   41.120626] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Mar 29 14:49:10 Surtur kernel: [   41.120629] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
Mar 29 14:49:15 Surtur kernel: [   46.661897] hda-intel: Invalid position buffer, using LPIB read method instead.
Mar 29 14:49:21 Surtur pulseaudio[5886]: ltdl-bind-now.c: Failed to find original dlopen loader.
Mar 29 14:49:21 Surtur pulseaudio[5888]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Mar 29 14:49:21 Surtur pulseaudio[5888]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Mar 29 14:49:24 Surtur x-session-manager[5798]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager' 
Mar 29 14:49:35 Surtur x-session-manager[5798]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 
Mar 29 14:49:45 Surtur x-session-manager[5798]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout 
Mar 29 14:49:45 Surtur pulseaudio[5888]: module-x11-xsmp.c: X11 session manager not running.
Mar 29 14:49:45 Surtur pulseaudio[5888]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Mar 29 14:49:50 Surtur NetworkManager: <info>  Activation (wlan0) starting connection 'Auto 2WIRE786' 
Mar 29 14:49:50 Surtur NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Mar 29 14:49:50 Surtur NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 29 14:49:50 Surtur NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Mar 29 14:49:50 Surtur NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Mar 29 14:49:50 Surtur NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Mar 29 14:49:50 Surtur NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Mar 29 14:49:50 Surtur NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Mar 29 14:49:50 Surtur NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto 2WIRE786' has security, but secrets are required. 
Mar 29 14:49:50 Surtur NetworkManager: <info>  (wlan0): device state change: 5 -> 6 
Mar 29 14:49:50 Surtur NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Mar 29 14:49:50 Surtur anacron[6158]: Anacron 2.3 started on 2009-03-29
Mar 29 14:49:50 Surtur anacron[6158]: Normal exit (0 jobs run)
Mar 29 14:49:50 Surtur kernel: [   81.058930] CPU0 attaching NULL sched-domain.
Mar 29 14:49:50 Surtur kernel: [   81.058946] CPU1 attaching NULL sched-domain.
Mar 29 14:49:50 Surtur kernel: [   81.076064] CPU0 attaching sched-domain:
Mar 29 14:49:50 Surtur kernel: [   81.076070]  domain 0: span 0-1 level CPU
Mar 29 14:49:50 Surtur kernel: [   81.076073]   groups: 0 1
Mar 29 14:49:50 Surtur kernel: [   81.076079] CPU1 attaching sched-domain:
Mar 29 14:49:50 Surtur kernel: [   81.076081]  domain 0: span 0-1 level CPU
Mar 29 14:49:50 Surtur kernel: [   81.076083]   groups: 1 0
Mar 29 14:50:00 Surtur NetworkManager: <info>  (wlan0): supplicant connection state change: 1 -> 2 
Mar 29 14:50:00 Surtur NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: applet-device-wifi.c.1512 (get_secrets_dialog_response_cb): canceled. 
Mar 29 14:50:00 Surtur NetworkManager: <info>  (wlan0): device state change: 6 -> 9 
Mar 29 14:50:00 Surtur NetworkManager: <info>  Activation (wlan0) failed for access point (2WIRE786) 
Mar 29 14:50:00 Surtur NetworkManager: <info>  Marking connection 'Auto 2WIRE786' invalid. 
Mar 29 14:50:00 Surtur NetworkManager: <info>  Activation (wlan0) failed. 
Mar 29 14:50:00 Surtur NetworkManager: <info>  (wlan0): device state change: 9 -> 3 
Mar 29 14:50:00 Surtur NetworkManager: <info>  (wlan0): deactivating device (reason: 0). 
Mar 29 14:50:00 Surtur NetworkManager: <info>  Activation (wlan0) starting connection 'Auto Gridscape' 
Mar 29 14:50:00 Surtur NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Mar 29 14:50:00 Surtur NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 29 14:50:00 Surtur NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Mar 29 14:50:00 Surtur NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Mar 29 14:50:00 Surtur NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Mar 29 14:50:00 Surtur NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 0 
Mar 29 14:50:00 Surtur NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Mar 29 14:50:00 Surtur NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Mar 29 14:50:00 Surtur NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto Gridscape' has security, but secrets are required. 
Mar 29 14:50:00 Surtur NetworkManager: <info>  (wlan0): device state change: 5 -> 6 
Mar 29 14:50:00 Surtur NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Mar 29 14:50:00 Surtur NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 29 14:50:00 Surtur NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Mar 29 14:50:00 Surtur NetworkManager: <info>  (wlan0): device state change: 6 -> 4 
Mar 29 14:50:00 Surtur NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Mar 29 14:50:00 Surtur NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Mar 29 14:50:00 Surtur NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Mar 29 14:50:00 Surtur NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Mar 29 14:50:00 Surtur NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto Gridscape' has security, and secrets exist.  No new secrets needed. 
Mar 29 14:50:00 Surtur NetworkManager: <info>  Config: added 'ssid' value 'Gridscape' 
Mar 29 14:50:00 Surtur NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Mar 29 14:50:00 Surtur NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Mar 29 14:50:00 Surtur NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN' 
Mar 29 14:50:00 Surtur NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>' 
Mar 29 14:50:00 Surtur NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0' 
Mar 29 14:50:00 Surtur NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Mar 29 14:50:00 Surtur NetworkManager: <info>  Config: set interface ap_scan to 1 
Mar 29 14:50:00 Surtur NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Mar 29 14:50:01 Surtur kernel: [   92.114394] wlan0: authenticate with AP f6364e28
Mar 29 14:50:01 Surtur NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
Mar 29 14:50:01 Surtur kernel: [   92.115847] wlan0: authenticated
Mar 29 14:50:01 Surtur kernel: [   92.115864] wlan0: associate with AP f6364e28
Mar 29 14:50:01 Surtur kernel: [   92.118163] wlan0: RX AssocResp from f0cdc08a (capab=0x411 status=0 aid=2)
Mar 29 14:50:01 Surtur kernel: [   92.118181] wlan0: invalid aid value 2; bits 15:14 not set
Mar 29 14:50:01 Surtur kernel: [   92.118189] wlan0: associated
Mar 29 14:50:01 Surtur NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 4 
Mar 29 14:50:01 Surtur NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 7 
Mar 29 14:50:01 Surtur NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Gridscape'. 
Mar 29 14:50:01 Surtur NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Mar 29 14:50:01 Surtur NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Mar 29 14:50:01 Surtur NetworkManager: <info>  (wlan0): device state change: 5 -> 7 
Mar 29 14:50:01 Surtur NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Mar 29 14:50:01 Surtur NetworkManager: <info>  dhclient started with pid 6193 
Mar 29 14:50:01 Surtur NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Mar 29 14:50:01 Surtur dhclient: Internet Systems Consortium DHCP Client V3.1.1
Mar 29 14:50:01 Surtur dhclient: Copyright 2004-2008 Internet Systems Consortium.
Mar 29 14:50:01 Surtur dhclient: All rights reserved.
Mar 29 14:50:01 Surtur dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Mar 29 14:50:01 Surtur dhclient: 
Mar 29 14:50:01 Surtur NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit 
Mar 29 14:50:01 Surtur dhclient: Listening on LPF/wlan0/00:21:63:f5:3a:8c
Mar 29 14:50:01 Surtur dhclient: Sending on   LPF/wlan0/00:21:63:f5:3a:8c
Mar 29 14:50:01 Surtur dhclient: Sending on   Socket/fallback
Mar 29 14:50:02 Surtur dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Mar 29 14:50:02 Surtur dhclient: DHCPOFFER of 192.168.1.34 from 192.168.1.1
Mar 29 14:50:02 Surtur dhclient: DHCPREQUEST of 192.168.1.34 on wlan0 to 255.255.255.255 port 67
Mar 29 14:50:02 Surtur dhclient: DHCPACK of 192.168.1.34 from 192.168.1.1
Mar 29 14:50:02 Surtur NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> bound 
Mar 29 14:50:02 Surtur NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
Mar 29 14:50:02 Surtur NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
Mar 29 14:50:02 Surtur NetworkManager: <info>    address 192.168.1.34 
Mar 29 14:50:02 Surtur NetworkManager: <info>    prefix 24 (255.255.255.0) 
Mar 29 14:50:02 Surtur NetworkManager: <info>    gateway 192.168.1.1 
Mar 29 14:50:02 Surtur NetworkManager: <info>    nameserver '192.168.1.1' 
Mar 29 14:50:02 Surtur NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Mar 29 14:50:02 Surtur NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
Mar 29 14:50:02 Surtur NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
Mar 29 14:50:02 Surtur avahi-daemon[5081]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.34.
Mar 29 14:50:02 Surtur avahi-daemon[5081]: New relevant interface wlan0.IPv4 for mDNS.
Mar 29 14:50:02 Surtur avahi-daemon[5081]: Registering new address record for 192.168.1.34 on wlan0.IPv4.
Mar 29 14:50:02 Surtur dhclient: bound to 192.168.1.34 -- renewal in 281808 seconds.
Mar 29 14:50:03 Surtur NetworkManager: <info>  (wlan0): device state change: 7 -> 8 
Mar 29 14:50:03 Surtur NetworkManager: <info>  Policy set 'Auto Gridscape' (wlan0) as default for routing and DNS. 
Mar 29 14:50:03 Surtur NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Mar 29 14:50:03 Surtur NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Mar 29 14:50:03 Surtur kernel: [   94.593419] NET: Registered protocol family 10
Mar 29 14:50:03 Surtur kernel: [   94.595862] lo: Disabled Privacy Extensions
Mar 29 14:50:03 Surtur kernel: [   94.598159] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 29 14:50:04 Surtur ntpdate[6250]: adjust time server 91.189.94.4 offset -0.360662 sec
Mar 29 14:50:04 Surtur avahi-daemon[5081]: Registering new address record for fe80::221:63ff:fef5:3a8c on wlan0.*.
Mar 29 14:50:13 Surtur kernel: [  104.848025] wlan0: no IPv6 routers present

Here is the requested information

---

### Post by pytheas22 on 2009-03-29
I don't see any concrete explanation of what's causing a kernel panic, but there are some lines in your log suggesting something is going wrong with the hal deamon, which could trigger a freeze.  I also see segfaulting in X--does your screen ever freeze and you have to press control-alt-delete to log back in, or do you have other problems with the graphics?

Do you notice any patterns to the panics?  Do they always occur when you're browsing the Internet or watching a video, for example?  If you're not connected to the Internet, do they still occur?  What about if you turn off desktop effects (you can turn them off by going to System>Preferences>Appearance)?  Do you ever leave your machine idle for extended periods of time and come back to find it frozen, or does it only freeze when you're working on it?  What kind of graphics card do you have (if you know the exact model, that would be good)?

If you answer those questions, it would help to get a better idea of what could be wrong.  It would also be helpful to see the output of:
```

lshw -C Network
lspci -nn
uname -rm
```

---

### Post by Nata-Bunny on 2009-03-30
> **pytheas22 said:**
> I don't see any concrete explanation of what's causing a kernel panic, but there are some lines in your log suggesting something is going wrong with the hal deamon, which could trigger a freeze.  I also see segfaulting in X--does your screen ever freeze and you have to press control-alt-delete to log back in, or do you have other problems with the graphics?

Do you notice any patterns to the panics?  Do they always occur when you're browsing the Internet or watching a video, for example?  If you're not connected to the Internet, do they still occur?  What about if you turn off desktop effects (you can turn them off by going to System>Preferences>Appearance)?  Do you ever leave your machine idle for extended periods of time and come back to find it frozen, or does it only freeze when you're working on it?  What kind of graphics card do you have (if you know the exact model, that would be good)?

If you answer those questions, it would help to get a better idea of what could be wrong.  It would also be helpful to see the output of:
```

lshw -C Network
lspci -nn
uname -rm
```

Generally the panics only occur when I have left my computer idle for a while... though it does occasionally happen when I am using my computer.  I will attempt to turn off desktop effects.  I have never had my screen-saver freeze.  I have some panics associated with the playing of some .wmv files, but not all of them.

My graphics card is an AMD/ATI 3100.  I have installed the ATI fglrx as opposed to the one in the repository.

Output of 'lshw -C Network':
*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:97:e3:dc
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 01
       serial: 00:21:63:f5:3a:8c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.0.101 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: a2:4c:b3:1d:6d:21
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

Output of 'lspci -nn':
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge [1022:9600]
00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx) [1022:9602]
00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) [1022:9604]
00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) [1022:9605]
00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) [1022:9606]
00:07.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3) [1022:9607]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:12.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3a)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB700/SB800 IDE Controller [1002:439c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration [1022:1300] (rev 40)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Address Map [1022:1301]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h DRAM Controller [1022:1302]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control [1022:1303]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Link Control [1022:1304]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics] [1002:9613]
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
05:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)

Output of 'uname -rm':
2.6.27-14-generic i686

let me know if you need anything else

---

### Post by pytheas22 on 2009-03-31
Thanks for the additional information.  I couldn't find anyone else reporting freezes with your particular hardware, but it is very interesting that you mention experiencing panics trying to play certain .wmv files.  Does it consistently freeze whenever you try to play these files, or only sometimes?  Do you have problems with other media files, or only .wmv?

Also, if you have any other operating systems on this computer, do they ever have problems?

And a final series of questions: when the kernel panics, can you still move the mouse cursor?  Does anything happen if you press control-alt-backspace?  If you press the numlock or capslock key, does the corresponding light flash on your keyboard?  Can you reboot your system using [REISUB]("http://kember.net/articles/231/reisub-the-gentle-linux-restart"), or only with a manual power-off?

---

### Post by Nata-Bunny on 2009-03-31
> **pytheas22 said:**
> Thanks for the additional information.  I couldn't find anyone else reporting freezes with your particular hardware, but it is very interesting that you mention experiencing panics trying to play certain .wmv files.  Does it consistently freeze whenever you try to play these files, or only sometimes?  Do you have problems with other media files, or only .wmv?

Also, if you have any other operating systems on this computer, do they ever have problems?

And a final series of questions: when the kernel panics, can you still move the mouse cursor?  Does anything happen if you press control-alt-backspace?  If you press the numlock or capslock key, does the corresponding light flash on your keyboard?  Can you reboot your system using [REISUB]("http://kember.net/articles/231/reisub-the-gentle-linux-restart"), or only with a manual power-off?

Only with .wmv.  Currently not running any other OS's on this computer.  When the kernel panics I only have a flashing caps lock key and can do nothing else save for with a manual power-off.

---

### Post by pytheas22 on 2009-04-01
I googled quite a bit but unfortunately couldn't find anyone complaining of kernel panics when playing wmv files, aside from [this thread]("http://ubuntuforums.org/showthread.php?t=837534"), which went unanswered.

Could you upload one of the files that triggers the crash?  I'd be interested to see what happens if I try to play it.  Also, which application are you using to play the file, and if you try a different one, do you still have freezes?

Last question: has this problem occurred since you first installed Ubuntu, or did it start suddenly?

---

