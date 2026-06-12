---
title: "Ubuntu 10.4 hangs on startup"
date: 2010-06-27
forum: Hardware
---

### Post by rstoya05-lx on 2010-06-27
I've a Dell Precision M2400 laptop and been using Lucid for a week without this issue. It might have been due to a recent upgrade but since yesterday it hangs during startup. It gets to the screen where it's written "Ubuntu" and never continues. Pressing the power button once causes it to stop hanging and shut down properly.

It is consistently reproducible. Based on the logs below I suspected a networking issue. I've been able to boot by physically disabling the networking using a button on the side and then re-enabling it later on.

**Update (Aug 3)**: I correct myself as I don't think that physically disabling networking has anything to do with it. It simply takes one or two or three times to boot successfully.**[end of update]**

This is what I see in the logs:

```
Jun 27 10:18:05 rossen-laptop vmnet-dhcpd: Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
Jun 27 10:18:05 rossen-laptop vmnet-dhcpd: All rights reserved.
Jun 27 10:18:05 rossen-laptop vmnet-dhcpd: 
Jun 27 10:18:05 rossen-laptop vmnet-dhcpd: Please contribute if you find this software useful.
Jun 27 10:18:05 rossen-laptop vmnet-dhcpd: For info, please visit http://www.isc.org/dhcp-contrib.html
Jun 27 10:18:05 rossen-laptop vmnet-dhcpd: 
Jun 27 10:18:05 rossen-laptop vmnet-dhcpd: Configured subnet: 192.168.208.0
Jun 27 10:18:05 rossen-laptop vmnet-dhcpd: Setting vmnet-dhcp IP address: 192.168.208.254
Jun 27 10:18:05 rossen-laptop vmnet-dhcpd: Recving on     VNet/vmnet1/192.168.208.0
Jun 27 10:18:05 rossen-laptop vmnet-dhcpd: Sending on     VNet/vmnet1/192.168.208.0
Jun 27 10:18:05 rossen-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/vmnet1, iface: vmnet1)
Jun 27 10:18:05 rossen-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/vmnet1, iface: vmnet1): no ifupdown configuration found.
Jun 27 10:18:05 rossen-laptop NetworkManager: <WARN>  device_creator(): /sys/devices/virtual/net/vmnet1: couldn't determine device driver; ignoring...
Jun 27 10:18:05 rossen-laptop avahi-daemon[1018]: Joining mDNS multicast group on interface vmnet1.IPv4 with address 192.168.208.1.
Jun 27 10:18:05 rossen-laptop avahi-daemon[1018]: New relevant interface vmnet1.IPv4 for mDNS.
Jun 27 10:18:05 rossen-laptop avahi-daemon[1018]: Registering new address record for 192.168.208.1 on vmnet1.IPv4.
Jun 27 10:18:05 rossen-laptop vmnet-dhcpd: Internet Software Consortium DHCP Server 2.0
Jun 27 10:18:05 rossen-laptop vmnet-dhcpd: Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
Jun 27 10:18:05 rossen-laptop vmnet-dhcpd: All rights reserved.
Jun 27 10:18:05 rossen-laptop vmnet-dhcpd: 
Jun 27 10:18:05 rossen-laptop vmnet-dhcpd: Please contribute if you find this software useful.
Jun 27 10:18:05 rossen-laptop vmnet-dhcpd: For info, please visit http://www.isc.org/dhcp-contrib.html
Jun 27 10:18:05 rossen-laptop vmnet-dhcpd: 
Jun 27 10:18:05 rossen-laptop kernel: [   44.542627] /dev/vmnet: open called by PID 1630 (vmnet-dhcpd)
Jun 27 10:18:05 rossen-laptop kernel: [   44.542637] /dev/vmnet: hub 1 does not exist, allocating memory.
Jun 27 10:18:05 rossen-laptop kernel: [   44.542653] /dev/vmnet: port on hub 1 successfully opened
Jun 27 10:18:05 rossen-laptop kernel: [   44.544309] /dev/vmnet: open called by PID 1632 (vmnet-netifup)
Jun 27 10:18:05 rossen-laptop kernel: [   44.544316] /dev/vmnet: port on hub 1 successfully opened
Jun 27 10:18:05 rossen-laptop vmnet-dhcpd: Configured subnet: 192.168.98.0
Jun 27 10:18:05 rossen-laptop vmnet-dhcpd: Setting vmnet-dhcp IP address: 192.168.98.254
Jun 27 10:18:05 rossen-laptop vmnet-dhcpd: Recving on     VNet/vmnet8/192.168.98.0
Jun 27 10:18:05 rossen-laptop vmnet-dhcpd: Sending on     VNet/vmnet8/192.168.98.0
Jun 27 10:18:05 rossen-laptop kernel: [   44.554196] /dev/vmnet: open called by PID 1635 (vmnet-dhcpd)
Jun 27 10:18:05 rossen-laptop kernel: [   44.554205] /dev/vmnet: hub 8 does not exist, allocating memory.
Jun 27 10:18:05 rossen-laptop kernel: [   44.554221] /dev/vmnet: port on hub 8 successfully opened
Jun 27 10:18:05 rossen-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/vmnet8, iface: vmnet8)
Jun 27 10:18:05 rossen-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/vmnet8, iface: vmnet8): no ifupdown configuration found.
Jun 27 10:18:05 rossen-laptop NetworkManager: <WARN>  device_creator(): /sys/devices/virtual/net/vmnet8: couldn't determine device driver; ignoring...
Jun 27 10:18:05 rossen-laptop avahi-daemon[1018]: Joining mDNS multicast group on interface vmnet8.IPv4 with address 192.168.98.1.
Jun 27 10:18:05 rossen-laptop avahi-daemon[1018]: New relevant interface vmnet8.IPv4 for mDNS.
Jun 27 10:18:05 rossen-laptop avahi-daemon[1018]: Registering new address record for 192.168.98.1 on vmnet8.IPv4.
Jun 27 10:18:05 rossen-laptop kernel: [   44.564735] /dev/vmnet: open called by PID 1640 (vmnet-natd)
Jun 27 10:18:05 rossen-laptop kernel: [   44.564744] /dev/vmnet: port on hub 8 successfully opened
Jun 27 10:18:05 rossen-laptop kernel: [   44.566265] /dev/vmnet: open called by PID 1641 (vmnet-netifup)
Jun 27 10:18:05 rossen-laptop kernel: [   44.566272] /dev/vmnet: port on hub 8 successfully opened
Jun 27 10:18:05 rossen-laptop vmnet-detect[1646]: NetDetectDaemonInit: No host policy file found. Not initializing filter.
Jun 27 10:18:05 rossen-laptop vmnet-detect[1646]: Unable to initialize the daemon
Jun 27 10:18:05 rossen-laptop init: plymouth-stop pre-start process (1653) terminated with status 1
Jun 27 10:18:06 rossen-laptop wpa_supplicant[1152]: WPS-AP-AVAILABLE 
Jun 27 10:18:07 rossen-laptop avahi-daemon[1018]: Registering new address record for fe80::250:56ff:fec0:8 on vmnet8.*.
Jun 27 10:18:07 rossen-laptop avahi-daemon[1018]: Registering new address record for fe80::250:56ff:fec0:1 on vmnet1.*.
Jun 27 10:18:16 rossen-laptop kernel: [   54.870205] vmnet8: no IPv6 routers present
Jun 27 10:18:16 rossen-laptop kernel: [   55.040203] vmnet1: no IPv6 routers present

```

---

### Post by rstoya05-lx on 2010-06-30
I'm getting pretty desperate on this issue!!! 

Every time I boot I get a screen that says Ubuntu (with dots below it) and it just hangs there. My workaround has been to toggle the WiFi radio killswitch + restart has worked a number of times but I hate workarounds I don't understand and it's starting to wear off. Now I have to reboot several times till I get one boot. This is debilitating.

I've spent an hour going over the syslog but I don't have a clue what I'm looking for.

Does no one have any clues based on this behavior -- hangs on screen that says Ubuntu (before login screen), caps light indicator does not come on, responds to power down button by shutting down?

I've attached a complete set of log messages from syslog from first boot to the point of hanging.

Where else can I look?

---

### Post by rstoya05-lx on 2010-06-30
I don't see my attachment so I'm going to paste the syslog output in here:

```
Jun 30 12:50:00 rossen-laptop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jun 30 12:50:00 rossen-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="998" x-info="http://www.rsyslog.com"] (re)start
Jun 30 12:50:00 rossen-laptop rsyslogd: rsyslogd's groupid changed to 102
Jun 30 12:50:00 rossen-laptop rsyslogd: rsyslogd's userid changed to 101
Jun 30 12:50:00 rossen-laptop rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] Linux version 2.6.32-22-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 (Ubuntu 2.6.32-22.36-generic 2.6.32.11+drm33.2)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] Command line: root=UUID=ef2e926d-4f55-4bc6-b439-966023979d00 ro quiet splash 
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] KERNEL supported cpus:
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]   Intel GenuineIntel
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]   AMD AuthenticAMD
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]   Centaur CentaurHauls
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009bc00 (usable)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]  BIOS-e820: 000000000009bc00 - 00000000000a0000 (reserved)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000df44d400 (usable)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]  BIOS-e820: 00000000df44f400 - 00000000e0000000 (reserved)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]  BIOS-e820: 00000000ffe60000 - 0000000100000000 (reserved)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]  BIOS-e820: 0000000100002000 - 0000000120000000 (usable)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] DMI 2.4 present.
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] last_pfn = 0x120000 max_arch_pfn = 0x400000000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] MTRR default type: uncachable
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] MTRR fixed ranges enabled:
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]   00000-9FFFF write-back
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]   A0000-BFFFF uncachable
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]   C0000-D3FFF write-protect
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]   D4000-EFFFF uncachable
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]   F0000-FFFFF write-protect
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] MTRR variable ranges enabled:
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]   0 base 000000000 mask 800000000 write-back
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]   1 base 0E0000000 mask FE0000000 uncachable
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]   2 disabled
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]   3 disabled
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]   4 disabled
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]   5 disabled
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]   6 disabled
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] e820 update range: 00000000e0000000 - 0000000100000000 (usable) ==> (reserved)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] last_pfn = 0xdf44d max_arch_pfn = 0x400000000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] Scanning 1 areas for low memory corruption
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] modified physical RAM map:
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]  modified: 0000000000006000 - 000000000009bc00 (usable)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]  modified: 000000000009bc00 - 00000000000a0000 (reserved)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]  modified: 0000000000100000 - 00000000df44d400 (usable)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]  modified: 00000000df44f400 - 00000000e0000000 (reserved)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]  modified: 00000000fed18000 - 00000000fed1c000 (reserved)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]  modified: 00000000feda0000 - 00000000feda6000 (reserved)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee10000 (reserved)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]  modified: 00000000ffe60000 - 0000000100000000 (reserved)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]  modified: 0000000100002000 - 0000000120000000 (usable)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] initial memory mapped : 0 - 20000000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000df44d000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] NX (Execute Disable) protection: active
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]  0000000000 - 00df400000 page 2M
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]  00df400000 - 00df44d000 page 4k
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] kernel direct mapping tables up to df44d000 @ 8000-e000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000120000000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] NX (Execute Disable) protection: active
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]  0100000000 - 0120000000 page 2M
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] kernel direct mapping tables up to 120000000 @ c000-12000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] RAMDISK: 377fe000 - 37feff79
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] ACPI: RSDP 00000000000fb9c0 00024 (v02 DELL  )
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] ACPI: XSDT 00000000df451e00 0006C (v01 DELL    M09     27D90508 ASL  00000061)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] ACPI: FACP 00000000df451c9c 000F4 (v04 DELL    M09     27D90508 ASL  00000061)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] ACPI: DSDT 00000000df452400 06AB6 (v02 INT430 SYSFexxx 00001001 INTL 20050624)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] ACPI: FACS 00000000df460c00 00040
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] ACPI: HPET 00000000df451f00 00038 (v01 DELL    M09     00000001 ASL  00000061)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] ACPI: ____ 00000000df460400 00030 (v01 DELL    M09     27D90508 ASL  00000061)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] ACPI: APIC 00000000df452000 00068 (v01 DELL    M09     27D90508 ASL  00000047)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] ACPI: ASF! 00000000df451c00 0006A (v32 DELL    M09     27D90508 ASL  00000061)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] ACPI: MCFG 00000000df451fc0 0003E (v16 DELL    M09     27D90508 ASL  00000061)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] ACPI: TCPA 00000000df452300 00032 (v01                 00000000 ASL  00000000)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] ACPI: SLIC 00000000df45209c 00176 (v01 DELL    M09     27D90508 ASL  00000061)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] ACPI: SSDT 00000000df4502eb 0066C (v01  PmRef    CpuPm 00003000 INTL 20050624)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] No NUMA configuration found
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] Faking a node at 0000000000000000-0000000120000000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000120000000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]   NODE_DATA [000000000000d000 - 0000000000011fff]
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]   bootmap [0000000000012000 -  0000000000035fff] pages 24
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0120000000]
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]   #2 [0001000000 - 0001a29e64]    TEXT DATA BSS ==> [0001000000 - 0001a29e64]
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]   #3 [00377fe000 - 0037feff79]          RAMDISK ==> [00377fe000 - 0037feff79]
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]   #4 [000009bc00 - 0000100000]    BIOS reserved ==> [000009bc00 - 0000100000]
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]   #5 [0001a2a000 - 0001a2a1e8]              BRK ==> [0001a2a000 - 0001a2a1e8]
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]   #6 [0000008000 - 000000c000]          PGTABLE ==> [0000008000 - 000000c000]
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]   #7 [000000c000 - 000000d000]          PGTABLE ==> [000000c000 - 000000d000]
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]  [ffffea0000000000-ffffea0003ffffff] PMD -> [ffff880028600000-ffff88002bffffff] on node 0
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] Zone PFN ranges:
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]   Normal   0x00100000 -> 0x00120000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] Movable zone start PFN for each node
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] early_node_map[4] active PFN ranges
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]     0: 0x00000000 -> 0x00000001
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]     0: 0x00000006 -> 0x0000009b
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]     0: 0x00000100 -> 0x000df44d
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]     0: 0x00100002 -> 0x00120000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] On node 0 totalpages: 1045473
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]   DMA zone: 108 pages reserved
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]   DMA zone: 3826 pages, LIFO batch:0
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]   DMA32 zone: 14280 pages used for memmap
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]   DMA32 zone: 896133 pages, LIFO batch:31
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]   Normal zone: 1792 pages used for memmap
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000]   Normal zone: 129278 pages, LIFO batch:31
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] ACPI: IRQ0 used by override.
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] ACPI: IRQ2 used by override.
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] ACPI: IRQ9 used by override.
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] nr_irqs_gsi: 24
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000df44d000 - 00000000df450000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000df450000 - 00000000e0000000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f8000000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec10000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fed18000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000fed18000 - 00000000fed1c000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed90000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000fed90000 - 00000000feda0000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000feda0000 - 00000000feda6000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000feda6000 - 00000000fee00000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee10000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000fee10000 - 00000000ffe60000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000ffe60000 - 0000000100000000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] PM: Registered nosave memory: 0000000100000000 - 0000000100002000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] Allocating PCI resources starting at e0000000 (gap: e0000000:18000000)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u1048576
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] pcpu-alloc: s91544 r8192 d23144 u1048576 alloc=1*2097152
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] pcpu-alloc: [0] 0 1 
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1029237
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] Policy zone: Normal
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] Kernel command line: root=UUID=ef2e926d-4f55-4bc6-b439-966023979d00 ro quiet splash 
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] Initializing CPU#0
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] Checking aperture...
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] No AGP bridge found
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] Memory: 4037508k/4718592k available (5409k kernel code, 536700k absent, 144384k reserved, 2976k data, 876k init)
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] Hierarchical RCU implementation.
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] NR_IRQS:4352 nr_irqs:424
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] Extended CMOS year: 2000
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] Console: colour VGA+ 80x25
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] console [tty0] enabled
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] allocated 41943040 bytes of page_cgroup
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] hpet clockevent registered
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] Fast TSC calibration using PIT
Jun 30 12:50:00 rossen-laptop kernel: [    0.000000] Detected 2659.835 MHz processor.
Jun 30 12:50:00 rossen-laptop kernel: [    0.010011] Calibrating delay loop (skipped), value calculated using timer frequency.. 5319.67 BogoMIPS (lpj=26598350)
Jun 30 12:50:00 rossen-laptop kernel: [    0.010073] Security Framework initialized
Jun 30 12:50:00 rossen-laptop kernel: [    0.010113] AppArmor: AppArmor initialized
Jun 30 12:50:00 rossen-laptop kernel: [    0.011073] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jun 30 12:50:00 rossen-laptop kernel: [    0.020627] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jun 30 12:50:00 rossen-laptop kernel: [    0.022387] Mount-cache hash table entries: 256
Jun 30 12:50:00 rossen-laptop kernel: [    0.022682] Initializing cgroup subsys ns
Jun 30 12:50:00 rossen-laptop kernel: [    0.022691] Initializing cgroup subsys cpuacct
Jun 30 12:50:00 rossen-laptop kernel: [    0.022700] Initializing cgroup subsys memory
Jun 30 12:50:00 rossen-laptop kernel: [    0.022717] Initializing cgroup subsys devices
Jun 30 12:50:00 rossen-laptop kernel: [    0.022722] Initializing cgroup subsys freezer
Jun 30 12:50:00 rossen-laptop kernel: [    0.022727] Initializing cgroup subsys net_cls
Jun 30 12:50:00 rossen-laptop kernel: [    0.022772] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun 30 12:50:00 rossen-laptop kernel: [    0.022778] CPU: L2 cache: 6144K
Jun 30 12:50:00 rossen-laptop kernel: [    0.022785] CPU 0/0x0 -> Node 0
Jun 30 12:50:00 rossen-laptop kernel: [    0.022791] CPU: Physical Processor ID: 0
Jun 30 12:50:00 rossen-laptop kernel: [    0.022794] CPU: Processor Core ID: 0
Jun 30 12:50:00 rossen-laptop kernel: [    0.022802] mce: CPU supports 6 MCE banks
Jun 30 12:50:00 rossen-laptop kernel: [    0.022820] CPU0: Thermal monitoring enabled (TM2)
Jun 30 12:50:00 rossen-laptop kernel: [    0.022828] using mwait in idle threads.
Jun 30 12:50:00 rossen-laptop kernel: [    0.022832] Performance Events: Core2 events, Intel PMU driver.
Jun 30 12:50:00 rossen-laptop kernel: [    0.022845] ... version:                2
Jun 30 12:50:00 rossen-laptop kernel: [    0.022849] ... bit width:              40
Jun 30 12:50:00 rossen-laptop kernel: [    0.022853] ... generic registers:      2
Jun 30 12:50:00 rossen-laptop kernel: [    0.022857] ... value mask:             000000ffffffffff
Jun 30 12:50:00 rossen-laptop kernel: [    0.022861] ... max period:             000000007fffffff
Jun 30 12:50:00 rossen-laptop kernel: [    0.022865] ... fixed-purpose events:   3
Jun 30 12:50:00 rossen-laptop kernel: [    0.022869] ... event mask:             0000000700000003
Jun 30 12:50:00 rossen-laptop kernel: [    0.031801] ACPI: Core revision 20090903
Jun 30 12:50:00 rossen-laptop kernel: [    0.060017] ftrace: converting mcount calls to 0f 1f 44 00 00
Jun 30 12:50:00 rossen-laptop kernel: [    0.060030] ftrace: allocating 22518 entries in 89 pages
Jun 30 12:50:00 rossen-laptop kernel: [    0.070095] Setting APIC routing to flat
Jun 30 12:50:00 rossen-laptop kernel: [    0.070520] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jun 30 12:50:00 rossen-laptop kernel: [    0.179236] CPU0: Intel(R) Core(TM)2 Duo CPU     T9550  @ 2.66GHz stepping 0a
Jun 30 12:50:00 rossen-laptop kernel: [    0.180000] Booting processor 1 APIC 0x1 ip 0x6000
Jun 30 12:50:00 rossen-laptop kernel: [    0.020000] Initializing CPU#1
Jun 30 12:50:00 rossen-laptop kernel: [    0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun 30 12:50:00 rossen-laptop kernel: [    0.020000] CPU: L2 cache: 6144K
Jun 30 12:50:00 rossen-laptop kernel: [    0.020000] CPU 1/0x1 -> Node 0
Jun 30 12:50:00 rossen-laptop kernel: [    0.020000] CPU: Physical Processor ID: 0
Jun 30 12:50:00 rossen-laptop kernel: [    0.020000] CPU: Processor Core ID: 1
Jun 30 12:50:00 rossen-laptop kernel: [    0.020000] CPU1: Thermal monitoring enabled (TM2)
Jun 30 12:50:00 rossen-laptop kernel: [    0.330145] CPU1: Intel(R) Core(TM)2 Duo CPU     T9550  @ 2.66GHz stepping 0a
Jun 30 12:50:00 rossen-laptop kernel: [    0.330161] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Jun 30 12:50:00 rossen-laptop kernel: [    0.340033] Brought up 2 CPUs
Jun 30 12:50:00 rossen-laptop kernel: [    0.340039] Total of 2 processors activated (10639.75 BogoMIPS).
Jun 30 12:50:00 rossen-laptop kernel: [    0.344527] CPU0 attaching sched-domain:
Jun 30 12:50:00 rossen-laptop kernel: [    0.344534]  domain 0: span 0-1 level MC
Jun 30 12:50:00 rossen-laptop kernel: [    0.344540]   groups: 0 1
Jun 30 12:50:00 rossen-laptop kernel: [    0.344554] CPU1 attaching sched-domain:
Jun 30 12:50:00 rossen-laptop kernel: [    0.344559]  domain 0: span 0-1 level MC
Jun 30 12:50:00 rossen-laptop kernel: [    0.344565]   groups: 1 0
Jun 30 12:50:00 rossen-laptop kernel: [    0.344747] devtmpfs: initialized
Jun 30 12:50:00 rossen-laptop kernel: [    0.344747] regulator: core version 0.5
Jun 30 12:50:00 rossen-laptop kernel: [    0.344747] Time: 11:49:20  Date: 06/30/10
Jun 30 12:50:00 rossen-laptop kernel: [    0.344747] NET: Registered protocol family 16
Jun 30 12:50:00 rossen-laptop kernel: [    0.344747] Trying to unpack rootfs image as initramfs...
Jun 30 12:50:00 rossen-laptop kernel: [    0.344747] ACPI: bus type pci registered
Jun 30 12:50:00 rossen-laptop kernel: [    0.344747] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
Jun 30 12:50:00 rossen-laptop kernel: [    0.344747] PCI: MCFG area at f8000000 reserved in E820
Jun 30 12:50:00 rossen-laptop kernel: [    0.351451] PCI: Using MMCONFIG at f8000000 - fbffffff
Jun 30 12:50:00 rossen-laptop kernel: [    0.351456] PCI: Using configuration type 1 for base access
Jun 30 12:50:00 rossen-laptop kernel: [    0.360200] bio: create slab <bio-0> at 0
Jun 30 12:50:00 rossen-laptop kernel: [    0.362272] ACPI: EC: Look up EC in DSDT
Jun 30 12:50:00 rossen-laptop kernel: [    0.362835] ACPI: BIOS _OSI(Linux) query ignored
Jun 30 12:50:00 rossen-laptop kernel: [    0.491520] ACPI: Interpreter enabled
Jun 30 12:50:00 rossen-laptop kernel: [    0.491520] ACPI: (supports S0 S3 S4 S5)
Jun 30 12:50:00 rossen-laptop kernel: [    0.491520] ACPI: Using IOAPIC for interrupt routing
Jun 30 12:50:00 rossen-laptop kernel: [    0.722744] ACPI: EC: GPE = 0x11, I/O: command/status = 0x934, data = 0x930
Jun 30 12:50:00 rossen-laptop kernel: [    0.727169] ACPI: No dock devices found.
Jun 30 12:50:00 rossen-laptop kernel: [    0.773507] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jun 30 12:50:00 rossen-laptop kernel: [    0.773772] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Jun 30 12:50:00 rossen-laptop kernel: [    0.773781] pci 0000:00:01.0: PME# disabled
Jun 30 12:50:00 rossen-laptop kernel: [    0.773934] pci 0000:00:19.0: reg 10 32bit mmio: [0xf6fe0000-0xf6ffffff]
Jun 30 12:50:00 rossen-laptop kernel: [    0.773948] pci 0000:00:19.0: reg 14 32bit mmio: [0xf6fdb000-0xf6fdbfff]
Jun 30 12:50:00 rossen-laptop kernel: [    0.773963] pci 0000:00:19.0: reg 18 io port: [0xefe0-0xefff]
Jun 30 12:50:00 rossen-laptop kernel: [    0.774050] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
Jun 30 12:50:00 rossen-laptop kernel: [    0.774059] pci 0000:00:19.0: PME# disabled
Jun 30 12:50:00 rossen-laptop kernel: [    0.774164] pci 0000:00:1a.0: reg 20 io port: [0x6f60-0x6f7f]
Jun 30 12:50:00 rossen-laptop kernel: [    0.774309] pci 0000:00:1a.1: reg 20 io port: [0x6f80-0x6f9f]
Jun 30 12:50:00 rossen-laptop kernel: [    0.774456] pci 0000:00:1a.2: reg 20 io port: [0x6fa0-0x6fbf]
Jun 30 12:50:00 rossen-laptop kernel: [    0.774605] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfed1c400-0xfed1c7ff]
Jun 30 12:50:00 rossen-laptop kernel: [    0.774709] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Jun 30 12:50:00 rossen-laptop kernel: [    0.774719] pci 0000:00:1a.7: PME# disabled
Jun 30 12:50:00 rossen-laptop kernel: [    0.774810] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf6fdc000-0xf6fdffff]
Jun 30 12:50:00 rossen-laptop kernel: [    0.774904] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jun 30 12:50:00 rossen-laptop kernel: [    0.774913] pci 0000:00:1b.0: PME# disabled
Jun 30 12:50:00 rossen-laptop kernel: [    0.775063] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jun 30 12:50:00 rossen-laptop kernel: [    0.775072] pci 0000:00:1c.0: PME# disabled
Jun 30 12:50:00 rossen-laptop kernel: [    0.775221] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Jun 30 12:50:00 rossen-laptop kernel: [    0.775230] pci 0000:00:1c.1: PME# disabled
Jun 30 12:50:00 rossen-laptop kernel: [    0.775378] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Jun 30 12:50:00 rossen-laptop kernel: [    0.775387] pci 0000:00:1c.2: PME# disabled
Jun 30 12:50:00 rossen-laptop kernel: [    0.775534] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Jun 30 12:50:00 rossen-laptop kernel: [    0.775543] pci 0000:00:1c.3: PME# disabled
Jun 30 12:50:00 rossen-laptop kernel: [    0.775667] pci 0000:00:1d.0: reg 20 io port: [0x6f00-0x6f1f]
Jun 30 12:50:00 rossen-laptop kernel: [    0.775814] pci 0000:00:1d.1: reg 20 io port: [0x6f20-0x6f3f]
Jun 30 12:50:00 rossen-laptop kernel: [    0.775960] pci 0000:00:1d.2: reg 20 io port: [0x6f40-0x6f5f]
Jun 30 12:50:00 rossen-laptop kernel: [    0.776112] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfed1c000-0xfed1c3ff]
Jun 30 12:50:00 rossen-laptop kernel: [    0.776216] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Jun 30 12:50:00 rossen-laptop kernel: [    0.776226] pci 0000:00:1d.7: PME# disabled
Jun 30 12:50:00 rossen-laptop kernel: [    0.776618] pci 0000:00:1f.2: reg 10 io port: [0x6e70-0x6e77]
Jun 30 12:50:00 rossen-laptop kernel: [    0.776633] pci 0000:00:1f.2: reg 14 io port: [0x6e78-0x6e7b]
Jun 30 12:50:00 rossen-laptop kernel: [    0.776647] pci 0000:00:1f.2: reg 18 io port: [0x6e80-0x6e87]
Jun 30 12:50:00 rossen-laptop kernel: [    0.776661] pci 0000:00:1f.2: reg 1c io port: [0x6e88-0x6e8b]
Jun 30 12:50:00 rossen-laptop kernel: [    0.776675] pci 0000:00:1f.2: reg 20 io port: [0x6ea0-0x6ebf]
Jun 30 12:50:00 rossen-laptop kernel: [    0.776689] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfed1c800-0xfed1cfff]
Jun 30 12:50:00 rossen-laptop kernel: [    0.776764] pci 0000:00:1f.2: PME# supported from D3hot
Jun 30 12:50:00 rossen-laptop kernel: [    0.776773] pci 0000:00:1f.2: PME# disabled
Jun 30 12:50:00 rossen-laptop kernel: [    0.776839] pci 0000:00:1f.3: reg 10 64bit mmio: [0xf6fdaf00-0xf6fdafff]
Jun 30 12:50:00 rossen-laptop kernel: [    0.776870] pci 0000:00:1f.3: reg 20 io port: [0x1100-0x111f]
Jun 30 12:50:00 rossen-laptop kernel: [    0.777014] pci 0000:01:00.0: reg 10 32bit mmio: [0xf5000000-0xf5ffffff]
Jun 30 12:50:00 rossen-laptop kernel: [    0.777046] pci 0000:01:00.0: reg 14 64bit mmio pref: [0xe0000000-0xefffffff]
Jun 30 12:50:00 rossen-laptop kernel: [    0.777079] pci 0000:01:00.0: reg 1c 64bit mmio: [0xf2000000-0xf3ffffff]
Jun 30 12:50:00 rossen-laptop kernel: [    0.777101] pci 0000:01:00.0: reg 24 io port: [0xdf00-0xdf7f]
Jun 30 12:50:00 rossen-laptop kernel: [    0.777123] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
Jun 30 12:50:00 rossen-laptop kernel: [    0.777306] pci 0000:00:01.0: bridge io port: [0xd000-0xdfff]
Jun 30 12:50:00 rossen-laptop kernel: [    0.777314] pci 0000:00:01.0: bridge 32bit mmio: [0xf2000000-0xf6efffff]
Jun 30 12:50:00 rossen-laptop kernel: [    0.777325] pci 0000:00:01.0: bridge 64bit mmio pref: [0xe0000000-0xefffffff]
Jun 30 12:50:00 rossen-laptop kernel: [    0.777558] pci 0000:0c:00.0: reg 10 64bit mmio: [0xf1ffe000-0xf1ffffff]
Jun 30 12:50:00 rossen-laptop kernel: [    0.777709] pci 0000:0c:00.0: PME# supported from D0 D3hot D3cold
Jun 30 12:50:00 rossen-laptop kernel: [    0.777721] pci 0000:0c:00.0: PME# disabled
Jun 30 12:50:00 rossen-laptop kernel: [    0.777852] pci 0000:00:1c.1: bridge 32bit mmio: [0xf1f00000-0xf1ffffff]
Jun 30 12:50:00 rossen-laptop kernel: [    0.778071] pci 0000:00:1c.3: bridge io port: [0xc000-0xcfff]
Jun 30 12:50:00 rossen-laptop kernel: [    0.778080] pci 0000:00:1c.3: bridge 32bit mmio: [0xf1c00000-0xf1efffff]
Jun 30 12:50:00 rossen-laptop kernel: [    0.778094] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xf0000000-0xf01fffff]
Jun 30 12:50:00 rossen-laptop kernel: [    0.778166] pci 0000:03:01.0: reg 10 32bit mmio: [0xf1bff800-0xf1bfffff]
Jun 30 12:50:00 rossen-laptop kernel: [    0.778255] pci 0000:03:01.0: supports D1 D2
Jun 30 12:50:00 rossen-laptop kernel: [    0.778260] pci 0000:03:01.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun 30 12:50:00 rossen-laptop kernel: [    0.778270] pci 0000:03:01.0: PME# disabled
Jun 30 12:50:00 rossen-laptop kernel: [    0.778335] pci 0000:03:01.1: reg 10 32bit mmio: [0xf1bff600-0xf1bff6ff]
Jun 30 12:50:00 rossen-laptop kernel: [    0.778424] pci 0000:03:01.1: supports D1 D2
Jun 30 12:50:00 rossen-laptop kernel: [    0.778430] pci 0000:03:01.1: PME# supported from D0 D1 D2 D3hot D3cold
Jun 30 12:50:00 rossen-laptop kernel: [    0.778439] pci 0000:03:01.1: PME# disabled
Jun 30 12:50:00 rossen-laptop kernel: [    0.778510] pci 0000:03:01.2: reg 10 32bit mmio: [0xf1bff700-0xf1bff7ff]
Jun 30 12:50:00 rossen-laptop kernel: [    0.778600] pci 0000:03:01.2: supports D1 D2
Jun 30 12:50:00 rossen-laptop kernel: [    0.778604] pci 0000:03:01.2: PME# supported from D0 D1 D2 D3hot D3cold
Jun 30 12:50:00 rossen-laptop kernel: [    0.778613] pci 0000:03:01.2: PME# disabled
Jun 30 12:50:00 rossen-laptop kernel: [    0.778728] pci 0000:00:1e.0: transparent bridge
Jun 30 12:50:00 rossen-laptop kernel: [    0.778742] pci 0000:00:1e.0: bridge 32bit mmio: [0xf1b00000-0xf1bfffff]
Jun 30 12:50:00 rossen-laptop kernel: [    0.778813] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jun 30 12:50:00 rossen-laptop kernel: [    0.779592] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
Jun 30 12:50:00 rossen-laptop kernel: [    0.779937] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Jun 30 12:50:00 rossen-laptop kernel: [    0.780150] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Jun 30 12:50:00 rossen-laptop kernel: [    0.780335] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
Jun 30 12:50:00 rossen-laptop kernel: [    0.780519] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
Jun 30 12:50:00 rossen-laptop kernel: [    0.780699] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
Jun 30 12:50:00 rossen-laptop kernel: [    0.817502] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *3
Jun 30 12:50:00 rossen-laptop kernel: [    0.817808] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
Jun 30 12:50:00 rossen-laptop kernel: [    0.818107] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 *11)
Jun 30 12:50:00 rossen-laptop kernel: [    0.818413] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 *10 11)
Jun 30 12:50:00 rossen-laptop kernel: [    0.818714] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Jun 30 12:50:00 rossen-laptop kernel: [    0.819019] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 10 11 12 14 15)
Jun 30 12:50:00 rossen-laptop kernel: [    0.819326] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Jun 30 12:50:00 rossen-laptop kernel: [    0.819599] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Jun 30 12:50:00 rossen-laptop kernel: [    0.819913] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Jun 30 12:50:00 rossen-laptop kernel: [    0.819925] vgaarb: loaded
Jun 30 12:50:00 rossen-laptop kernel: [    0.820219] SCSI subsystem initialized
Jun 30 12:50:00 rossen-laptop kernel: [    0.820392] libata version 3.00 loaded.
Jun 30 12:50:00 rossen-laptop kernel: [    0.820563] usbcore: registered new interface driver usbfs
Jun 30 12:50:00 rossen-laptop kernel: [    0.820597] usbcore: registered new interface driver hub
Jun 30 12:50:00 rossen-laptop kernel: [    0.820665] usbcore: registered new device driver usb
Jun 30 12:50:00 rossen-laptop kernel: [    0.821036] ACPI: WMI: Mapper loaded
Jun 30 12:50:00 rossen-laptop kernel: [    0.821040] PCI: Using ACPI for IRQ routing
Jun 30 12:50:00 rossen-laptop kernel: [    0.821450] NetLabel: Initializing
Jun 30 12:50:00 rossen-laptop kernel: [    0.821455] NetLabel:  domain hash size = 128
Jun 30 12:50:00 rossen-laptop kernel: [    0.821459] NetLabel:  protocols = UNLABELED CIPSOv4
Jun 30 12:50:00 rossen-laptop kernel: [    0.821491] NetLabel:  unlabeled traffic allowed by default
Jun 30 12:50:00 rossen-laptop kernel: [    0.821565] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Jun 30 12:50:00 rossen-laptop kernel: [    0.821578] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
Jun 30 12:50:00 rossen-laptop kernel: [    0.830544] Switching to clocksource tsc
Jun 30 12:50:00 rossen-laptop kernel: [    0.834212] AppArmor: AppArmor Filesystem Enabled
Jun 30 12:50:00 rossen-laptop kernel: [    0.834234] pnp: PnP ACPI init
Jun 30 12:50:00 rossen-laptop kernel: [    0.834255] ACPI: bus type pnp registered
Jun 30 12:50:00 rossen-laptop kernel: [    1.016117] pnp: PnP ACPI: found 14 devices
Jun 30 12:50:00 rossen-laptop kernel: [    1.016124] ACPI: ACPI bus type pnp unregistered
Jun 30 12:50:00 rossen-laptop kernel: [    1.016156] system 00:05: ioport range 0xc80-0xcaf has been reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016164] system 00:05: ioport range 0xcc0-0xcff could not be reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016184] system 00:08: iomem range 0xfed00000-0xfed003ff has been reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016199] system 00:0a: ioport range 0xcb0-0xcbb has been reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016207] system 00:0a: iomem range 0xfed40000-0xfed44fff has been reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016221] system 00:0b: ioport range 0x900-0x92f has been reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016228] system 00:0b: ioport range 0x931-0x933 has been reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016235] system 00:0b: ioport range 0x935-0x97f has been reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016242] system 00:0b: ioport range 0x4d0-0x4d1 has been reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016250] system 00:0b: ioport range 0x1000-0x1005 has been reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016257] system 00:0b: ioport range 0x1008-0x100f has been reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016272] system 00:0c: ioport range 0xf400-0xf4fe has been reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016279] system 00:0c: ioport range 0x1006-0x1007 has been reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016286] system 00:0c: ioport range 0x100a-0x1059 could not be reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016293] system 00:0c: ioport range 0x1060-0x107f has been reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016300] system 00:0c: ioport range 0x1080-0x10bf has been reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016307] system 00:0c: ioport range 0x1100-0x111f has been reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016313] system 00:0c: ioport range 0x1010-0x102f has been reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016321] system 00:0c: ioport range 0x809-0x809 has been reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016336] system 00:0d: iomem range 0x0-0x9efff could not be reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016344] system 00:0d: iomem range 0x9f000-0x9ffff could not be reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016351] system 00:0d: iomem range 0xc0000-0xd3fff has been reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016358] system 00:0d: iomem range 0xe0000-0xfffff has been reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016375] system 00:0d: iomem range 0x100000-0xdf44d3ff could not be reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016383] system 00:0d: iomem range 0xdf44d400-0xdfefffff could not be reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016390] system 00:0d: iomem range 0xdff00000-0xdfffffff has been reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016399] system 00:0d: iomem range 0xffe00000-0xffffffff could not be reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016406] system 00:0d: iomem range 0xffa00000-0xffbfffff has been reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016414] system 00:0d: iomem range 0xfec00000-0xfec0ffff could not be reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016422] system 00:0d: iomem range 0xfee00000-0xfee0ffff has been reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016430] system 00:0d: iomem range 0xfed20000-0xfed3ffff has been reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016437] system 00:0d: iomem range 0xfed45000-0xfed8ffff has been reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016444] system 00:0d: iomem range 0xfeda0000-0xfeda3fff has been reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016452] system 00:0d: iomem range 0xfeda4000-0xfeda4fff has been reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016459] system 00:0d: iomem range 0xfeda5000-0xfeda5fff has been reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016467] system 00:0d: iomem range 0xfeda6000-0xfeda6fff has been reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016474] system 00:0d: iomem range 0xfed1c800-0xfed1cfff has been reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016482] system 00:0d: iomem range 0xfed18000-0xfed1bfff has been reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.016494] system 00:0d: iomem range 0xf8000000-0xfbffffff has been reserved
Jun 30 12:50:00 rossen-laptop kernel: [    1.021605] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Jun 30 12:50:00 rossen-laptop kernel: [    1.021613] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
Jun 30 12:50:00 rossen-laptop kernel: [    1.021622] pci 0000:00:01.0:   MEM window: 0xf2000000-0xf6efffff
Jun 30 12:50:00 rossen-laptop kernel: [    1.021631] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
Jun 30 12:50:00 rossen-laptop kernel: [    1.021642] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b
Jun 30 12:50:00 rossen-laptop kernel: [    1.021649] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
Jun 30 12:50:00 rossen-laptop kernel: [    1.021661] pci 0000:00:1c.0:   MEM window: 0xf0200000-0xf03fffff
Jun 30 12:50:00 rossen-laptop kernel: [    1.021670] pci 0000:00:1c.0:   PREFETCH window: 0x000000f0400000-0x000000f05fffff
Jun 30 12:50:00 rossen-laptop kernel: [    1.021685] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0c
Jun 30 12:50:00 rossen-laptop kernel: [    1.021692] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
Jun 30 12:50:00 rossen-laptop kernel: [    1.021703] pci 0000:00:1c.1:   MEM window: 0xf1f00000-0xf1ffffff
Jun 30 12:50:00 rossen-laptop kernel: [    1.021712] pci 0000:00:1c.1:   PREFETCH window: 0x000000f0600000-0x000000f07fffff
Jun 30 12:50:00 rossen-laptop kernel: [    1.021726] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:0d
Jun 30 12:50:00 rossen-laptop kernel: [    1.021734] pci 0000:00:1c.2:   IO window: 0x4000-0x4fff
Jun 30 12:50:00 rossen-laptop kernel: [    1.021745] pci 0000:00:1c.2:   MEM window: 0xf0800000-0xf09fffff
Jun 30 12:50:00 rossen-laptop kernel: [    1.021755] pci 0000:00:1c.2:   PREFETCH window: 0x000000f0a00000-0x000000f0bfffff
Jun 30 12:50:00 rossen-laptop kernel: [    1.021768] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:0e
Jun 30 12:50:00 rossen-laptop kernel: [    1.021776] pci 0000:00:1c.3:   IO window: 0xc000-0xcfff
Jun 30 12:50:00 rossen-laptop kernel: [    1.021787] pci 0000:00:1c.3:   MEM window: 0xf1c00000-0xf1efffff
Jun 30 12:50:00 rossen-laptop kernel: [    1.021796] pci 0000:00:1c.3:   PREFETCH window: 0x000000f0000000-0x000000f01fffff
Jun 30 12:50:00 rossen-laptop kernel: [    1.021811] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
Jun 30 12:50:00 rossen-laptop kernel: [    1.021815] pci 0000:00:1e.0:   IO window: disabled
Jun 30 12:50:00 rossen-laptop kernel: [    1.021827] pci 0000:00:1e.0:   MEM window: 0xf1b00000-0xf1bfffff
Jun 30 12:50:00 rossen-laptop kernel: [    1.021836] pci 0000:00:1e.0:   PREFETCH window: disabled
Jun 30 12:50:00 rossen-laptop kernel: [    1.021864]   alloc irq_desc for 16 on node -1
Jun 30 12:50:00 rossen-laptop kernel: [    1.021869]   alloc kstat_irqs on node -1
Jun 30 12:50:00 rossen-laptop kernel: [    1.021883] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 30 12:50:00 rossen-laptop kernel: [    1.021892] pci 0000:00:01.0: setting latency timer to 64
Jun 30 12:50:00 rossen-laptop kernel: [    1.021910] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 30 12:50:00 rossen-laptop kernel: [    1.021920] pci 0000:00:1c.0: setting latency timer to 64
Jun 30 12:50:00 rossen-laptop kernel: [    1.021938]   alloc irq_desc for 17 on node -1
Jun 30 12:50:00 rossen-laptop kernel: [    1.021942]   alloc kstat_irqs on node -1
Jun 30 12:50:00 rossen-laptop kernel: [    1.021950] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 30 12:50:00 rossen-laptop kernel: [    1.021959] pci 0000:00:1c.1: setting latency timer to 64
Jun 30 12:50:00 rossen-laptop kernel: [    1.021976]   alloc irq_desc for 18 on node -1
Jun 30 12:50:00 rossen-laptop kernel: [    1.021980]   alloc kstat_irqs on node -1
Jun 30 12:50:00 rossen-laptop kernel: [    1.021988] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jun 30 12:50:00 rossen-laptop kernel: [    1.021997] pci 0000:00:1c.2: setting latency timer to 64
Jun 30 12:50:00 rossen-laptop kernel: [    1.022015]   alloc irq_desc for 19 on node -1
Jun 30 12:50:00 rossen-laptop kernel: [    1.022019]   alloc kstat_irqs on node -1
Jun 30 12:50:00 rossen-laptop kernel: [    1.022026] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Jun 30 12:50:00 rossen-laptop kernel: [    1.022036] pci 0000:00:1c.3: setting latency timer to 64
Jun 30 12:50:00 rossen-laptop kernel: [    1.022050] pci 0000:00:1e.0: setting latency timer to 64
Jun 30 12:50:00 rossen-laptop kernel: [    1.022060] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Jun 30 12:50:00 rossen-laptop kernel: [    1.022066] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
Jun 30 12:50:00 rossen-laptop kernel: [    1.022073] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
Jun 30 12:50:00 rossen-laptop kernel: [    1.022079] pci_bus 0000:01: resource 1 mem: [0xf2000000-0xf6efffff]
Jun 30 12:50:00 rossen-laptop kernel: [    1.022085] pci_bus 0000:01: resource 2 pref mem [0xe0000000-0xefffffff]
Jun 30 12:50:00 rossen-laptop kernel: [    1.022091] pci_bus 0000:0b: resource 0 io:  [0x2000-0x2fff]
Jun 30 12:50:00 rossen-laptop kernel: [    1.022097] pci_bus 0000:0b: resource 1 mem: [0xf0200000-0xf03fffff]
Jun 30 12:50:00 rossen-laptop kernel: [    1.022102] pci_bus 0000:0b: resource 2 pref mem [0xf0400000-0xf05fffff]
Jun 30 12:50:00 rossen-laptop kernel: [    1.022108] pci_bus 0000:0c: resource 0 io:  [0x3000-0x3fff]
Jun 30 12:50:00 rossen-laptop kernel: [    1.022114] pci_bus 0000:0c: resource 1 mem: [0xf1f00000-0xf1ffffff]
Jun 30 12:50:00 rossen-laptop kernel: [    1.022120] pci_bus 0000:0c: resource 2 pref mem [0xf0600000-0xf07fffff]
Jun 30 12:50:00 rossen-laptop kernel: [    1.022126] pci_bus 0000:0d: resource 0 io:  [0x4000-0x4fff]
Jun 30 12:50:00 rossen-laptop kernel: [    1.022131] pci_bus 0000:0d: resource 1 mem: [0xf0800000-0xf09fffff]
Jun 30 12:50:00 rossen-laptop kernel: [    1.022137] pci_bus 0000:0d: resource 2 pref mem [0xf0a00000-0xf0bfffff]
Jun 30 12:50:00 rossen-laptop kernel: [    1.022143] pci_bus 0000:0e: resource 0 io:  [0xc000-0xcfff]
Jun 30 12:50:00 rossen-laptop kernel: [    1.022148] pci_bus 0000:0e: resource 1 mem: [0xf1c00000-0xf1efffff]
Jun 30 12:50:00 rossen-laptop kernel: [    1.022154] pci_bus 0000:0e: resource 2 pref mem [0xf0000000-0xf01fffff]
Jun 30 12:50:00 rossen-laptop kernel: [    1.022160] pci_bus 0000:03: resource 1 mem: [0xf1b00000-0xf1bfffff]
Jun 30 12:50:00 rossen-laptop kernel: [    1.022166] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
Jun 30 12:50:00 rossen-laptop kernel: [    1.022172] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffffffffffff]
Jun 30 12:50:00 rossen-laptop kernel: [    1.022247] NET: Registered protocol family 2
Jun 30 12:50:00 rossen-laptop kernel: [    1.022651] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Jun 30 12:50:00 rossen-laptop kernel: [    1.025476] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Jun 30 12:50:00 rossen-laptop kernel: [    1.032213] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jun 30 12:50:00 rossen-laptop kernel: [    1.033110] TCP: Hash tables configured (established 524288 bind 65536)
Jun 30 12:50:00 rossen-laptop kernel: [    1.033116] TCP reno registered
Jun 30 12:50:00 rossen-laptop kernel: [    1.033335] NET: Registered protocol family 1
Jun 30 12:50:00 rossen-laptop kernel: [    1.033666] pci 0000:01:00.0: Boot video device
Jun 30 12:50:00 rossen-laptop kernel: [    1.034231] Scanning for low memory corruption every 60 seconds
Jun 30 12:50:00 rossen-laptop kernel: [    1.034548] audit: initializing netlink socket (disabled)
Jun 30 12:50:00 rossen-laptop kernel: [    1.034569] type=2000 audit(1277898561.030:1): initialized
Jun 30 12:50:00 rossen-laptop kernel: [    1.058947] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jun 30 12:50:00 rossen-laptop kernel: [    1.062442] VFS: Disk quotas dquot_6.5.2
Jun 30 12:50:00 rossen-laptop kernel: [    1.062570] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jun 30 12:50:00 rossen-laptop kernel: [    1.063986] fuse init (API version 7.13)
Jun 30 12:50:00 rossen-laptop kernel: [    1.064196] msgmni has been set to 7885
Jun 30 12:50:00 rossen-laptop kernel: [    1.064682] alg: No test for stdrng (krng)
Jun 30 12:50:00 rossen-laptop kernel: [    1.064801] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jun 30 12:50:00 rossen-laptop kernel: [    1.064808] io scheduler noop registered
Jun 30 12:50:00 rossen-laptop kernel: [    1.064813] io scheduler anticipatory registered
Jun 30 12:50:00 rossen-laptop kernel: [    1.064817] io scheduler deadline registered
Jun 30 12:50:00 rossen-laptop kernel: [    1.064910] io scheduler cfq registered (default)
Jun 30 12:50:00 rossen-laptop kernel: [    1.065226]   alloc irq_desc for 24 on node -1
Jun 30 12:50:00 rossen-laptop kernel: [    1.065232]   alloc kstat_irqs on node -1
Jun 30 12:50:00 rossen-laptop kernel: [    1.065249] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
Jun 30 12:50:00 rossen-laptop kernel: [    1.065264] pcieport 0000:00:01.0: setting latency timer to 64
Jun 30 12:50:00 rossen-laptop kernel: [    1.065521]   alloc irq_desc for 25 on node -1
Jun 30 12:50:00 rossen-laptop kernel: [    1.065526]   alloc kstat_irqs on node -1
Jun 30 12:50:00 rossen-laptop kernel: [    1.065541] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
Jun 30 12:50:00 rossen-laptop kernel: [    1.065559] pcieport 0000:00:1c.0: setting latency timer to 64
Jun 30 12:50:00 rossen-laptop kernel: [    1.065815]   alloc irq_desc for 26 on node -1
Jun 30 12:50:00 rossen-laptop kernel: [    1.065820]   alloc kstat_irqs on node -1
Jun 30 12:50:00 rossen-laptop kernel: [    1.065836] pcieport 0000:00:1c.1: irq 26 for MSI/MSI-X
Jun 30 12:50:00 rossen-laptop kernel: [    1.065853] pcieport 0000:00:1c.1: setting latency timer to 64
Jun 30 12:50:00 rossen-laptop kernel: [    1.066108]   alloc irq_desc for 27 on node -1
Jun 30 12:50:00 rossen-laptop kernel: [    1.066113]   alloc kstat_irqs on node -1
Jun 30 12:50:00 rossen-laptop kernel: [    1.066129] pcieport 0000:00:1c.2: irq 27 for MSI/MSI-X
Jun 30 12:50:00 rossen-laptop kernel: [    1.066146] pcieport 0000:00:1c.2: setting latency timer to 64
Jun 30 12:50:00 rossen-laptop kernel: [    1.066416]   alloc irq_desc for 28 on node -1
Jun 30 12:50:00 rossen-laptop kernel: [    1.066420]   alloc kstat_irqs on node -1
Jun 30 12:50:00 rossen-laptop kernel: [    1.066436] pcieport 0000:00:1c.3: irq 28 for MSI/MSI-X
Jun 30 12:50:00 rossen-laptop kernel: [    1.066454] pcieport 0000:00:1c.3: setting latency timer to 64
Jun 30 12:50:00 rossen-laptop kernel: [    1.066655] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 30 12:50:00 rossen-laptop kernel: [    1.067006] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jun 30 12:50:00 rossen-laptop kernel: [    1.067327] ACPI: AC Adapter [AC] (off-line)
Jun 30 12:50:00 rossen-laptop kernel: [    1.067546] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
Jun 30 12:50:00 rossen-laptop kernel: [    1.069992] ACPI: Lid Switch [LID]
Jun 30 12:50:00 rossen-laptop kernel: [    1.070124] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
Jun 30 12:50:00 rossen-laptop kernel: [    1.070136] ACPI: Power Button [PBTN]
Jun 30 12:50:00 rossen-laptop kernel: [    1.070247] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
Jun 30 12:50:00 rossen-laptop kernel: [    1.070253] ACPI: Sleep Button [SBTN]
Jun 30 12:50:00 rossen-laptop kernel: [    1.072126] ACPI: SSDT 00000000df450957 002C3 (v01  PmRef   BspIst 00003000 INTL 20050624)
Jun 30 12:50:00 rossen-laptop kernel: [    1.075170] ACPI: SSDT 00000000df450df1 005C6 (v01  PmRef   BspCst 00003001 INTL 20050624)
Jun 30 12:50:00 rossen-laptop kernel: [    1.076005] Monitor-Mwait will be used to enter C-1 state
Jun 30 12:50:00 rossen-laptop kernel: [    1.076067] Monitor-Mwait will be used to enter C-2 state
Jun 30 12:50:00 rossen-laptop kernel: [    1.076126] Monitor-Mwait will be used to enter C-3 state
Jun 30 12:50:00 rossen-laptop kernel: [    1.076140] Marking TSC unstable due to TSC halts in idle
Jun 30 12:50:00 rossen-laptop kernel: [    1.076231] processor LNXCPU:00: registered as cooling_device0
Jun 30 12:50:00 rossen-laptop kernel: [    1.077292] ACPI: SSDT 00000000df450c1a 001D7 (v01  PmRef    ApIst 00003000 INTL 20050624)
Jun 30 12:50:00 rossen-laptop kernel: [    1.078134] ACPI: SSDT 00000000df4513b7 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
Jun 30 12:50:00 rossen-laptop kernel: [    1.080496] Switching to clocksource hpet
Jun 30 12:50:00 rossen-laptop kernel: [    1.082342] processor LNXCPU:01: registered as cooling_device1
Jun 30 12:50:00 rossen-laptop kernel: [    1.150150] thermal LNXTHERM:01: registered as thermal_zone0
Jun 30 12:50:00 rossen-laptop kernel: [    1.150169] ACPI: Thermal Zone [THM] (45 C)
Jun 30 12:50:00 rossen-laptop kernel: [    1.153627] Linux agpgart interface v0.103
Jun 30 12:50:00 rossen-laptop kernel: [    1.153702] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Jun 30 12:50:00 rossen-laptop kernel: [    1.153939] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Jun 30 12:50:00 rossen-laptop kernel: [    1.154618] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Jun 30 12:50:00 rossen-laptop kernel: [    1.157108] brd: module loaded
Jun 30 12:50:00 rossen-laptop kernel: [    1.158229] loop: module loaded
Jun 30 12:50:00 rossen-laptop kernel: [    1.158415] input: Macintosh mouse button emulation as /devices/virtual/input/input3
Jun 30 12:50:00 rossen-laptop kernel: [    1.159361] Fixed MDIO Bus: probed
Jun 30 12:50:00 rossen-laptop kernel: [    1.159436] PPP generic driver version 2.4.2
Jun 30 12:50:00 rossen-laptop kernel: [    1.159520] tun: Universal TUN/TAP device driver, 1.6
Jun 30 12:50:00 rossen-laptop kernel: [    1.159525] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jun 30 12:50:00 rossen-laptop kernel: [    1.159708] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jun 30 12:50:00 rossen-laptop kernel: [    1.159751]   alloc irq_desc for 22 on node -1
Jun 30 12:50:00 rossen-laptop kernel: [    1.159756]   alloc kstat_irqs on node -1
Jun 30 12:50:00 rossen-laptop kernel: [    1.159769] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Jun 30 12:50:00 rossen-laptop kernel: [    1.159805] ehci_hcd 0000:00:1a.7: setting latency timer to 64
Jun 30 12:50:00 rossen-laptop kernel: [    1.159812] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Jun 30 12:50:00 rossen-laptop kernel: [    1.159884] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Jun 30 12:50:00 rossen-laptop kernel: [    1.159945] ehci_hcd 0000:00:1a.7: debug port 1
Jun 30 12:50:00 rossen-laptop kernel: [    1.163846] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
Jun 30 12:50:00 rossen-laptop kernel: [    1.163896] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
Jun 30 12:50:00 rossen-laptop kernel: [    1.168374] ACPI: Battery Slot [BAT1] (battery absent)
Jun 30 12:50:00 rossen-laptop kernel: [    1.180326] Freeing initrd memory: 8135k freed
Jun 30 12:50:00 rossen-laptop kernel: [    1.182538] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Jun 30 12:50:00 rossen-laptop kernel: [    1.182841] usb usb1: configuration #1 chosen from 1 choice
Jun 30 12:50:00 rossen-laptop kernel: [    1.182920] hub 1-0:1.0: USB hub found
Jun 30 12:50:00 rossen-laptop kernel: [    1.182946] hub 1-0:1.0: 6 ports detected
Jun 30 12:50:00 rossen-laptop kernel: [    1.183127]   alloc irq_desc for 20 on node -1
Jun 30 12:50:00 rossen-laptop kernel: [    1.183132]   alloc kstat_irqs on node -1
Jun 30 12:50:00 rossen-laptop kernel: [    1.183150] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Jun 30 12:50:00 rossen-laptop kernel: [    1.183202] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Jun 30 12:50:00 rossen-laptop kernel: [    1.183209] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jun 30 12:50:00 rossen-laptop kernel: [    1.183331] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Jun 30 12:50:00 rossen-laptop kernel: [    1.183399] ehci_hcd 0000:00:1d.7: debug port 1
Jun 30 12:50:00 rossen-laptop kernel: [    1.187275] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Jun 30 12:50:00 rossen-laptop kernel: [    1.187315] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
Jun 30 12:50:00 rossen-laptop kernel: [    1.212526] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Jun 30 12:50:00 rossen-laptop kernel: [    1.212721] usb usb2: configuration #1 chosen from 1 choice
Jun 30 12:50:00 rossen-laptop kernel: [    1.212783] hub 2-0:1.0: USB hub found
Jun 30 12:50:00 rossen-laptop kernel: [    1.212800] hub 2-0:1.0: 6 ports detected
Jun 30 12:50:00 rossen-laptop kernel: [    1.212984] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jun 30 12:50:00 rossen-laptop kernel: [    1.213023] uhci_hcd: USB Universal Host Controller Interface driver
Jun 30 12:50:00 rossen-laptop kernel: [    1.213100] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Jun 30 12:50:00 rossen-laptop kernel: [    1.213117] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Jun 30 12:50:00 rossen-laptop kernel: [    1.213124] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Jun 30 12:50:00 rossen-laptop kernel: [    1.213201] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Jun 30 12:50:00 rossen-laptop kernel: [    1.213244] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f60
Jun 30 12:50:00 rossen-laptop kernel: [    1.213449] usb usb3: configuration #1 chosen from 1 choice
Jun 30 12:50:00 rossen-laptop kernel: [    1.213508] hub 3-0:1.0: USB hub found
Jun 30 12:50:00 rossen-laptop kernel: [    1.213524] hub 3-0:1.0: 2 ports detected
Jun 30 12:50:00 rossen-laptop kernel: [    1.213628]   alloc irq_desc for 21 on node -1
Jun 30 12:50:00 rossen-laptop kernel: [    1.213633]   alloc kstat_irqs on node -1
Jun 30 12:50:00 rossen-laptop kernel: [    1.213645] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Jun 30 12:50:00 rossen-laptop kernel: [    1.213664] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Jun 30 12:50:00 rossen-laptop kernel: [    1.213672] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Jun 30 12:50:00 rossen-laptop kernel: [    1.213773] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Jun 30 12:50:00 rossen-laptop kernel: [    1.213826] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f80
Jun 30 12:50:00 rossen-laptop kernel: [    1.214025] usb usb4: configuration #1 chosen from 1 choice
Jun 30 12:50:00 rossen-laptop kernel: [    1.214084] hub 4-0:1.0: USB hub found
Jun 30 12:50:00 rossen-laptop kernel: [    1.214100] hub 4-0:1.0: 2 ports detected
Jun 30 12:50:00 rossen-laptop kernel: [    1.214254] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Jun 30 12:50:00 rossen-laptop kernel: [    1.214267] uhci_hcd 0000:00:1a.2: setting latency timer to 64
Jun 30 12:50:00 rossen-laptop kernel: [    1.214275] uhci_hcd 0000:00:1a.2: UHCI Host Controller
Jun 30 12:50:00 rossen-laptop kernel: [    1.214364] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
Jun 30 12:50:00 rossen-laptop kernel: [    1.214406] uhci_hcd 0000:00:1a.2: irq 22, io base 0x00006fa0
Jun 30 12:50:00 rossen-laptop kernel: [    1.214605] usb usb5: configuration #1 chosen from 1 choice
Jun 30 12:50:00 rossen-laptop kernel: [    1.214664] hub 5-0:1.0: USB hub found
Jun 30 12:50:00 rossen-laptop kernel: [    1.214679] hub 5-0:1.0: 2 ports detected
Jun 30 12:50:00 rossen-laptop kernel: [    1.214780] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Jun 30 12:50:00 rossen-laptop kernel: [    1.214793] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Jun 30 12:50:00 rossen-laptop kernel: [    1.214800] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jun 30 12:50:00 rossen-laptop kernel: [    1.214872] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
Jun 30 12:50:00 rossen-laptop kernel: [    1.214956] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f00
Jun 30 12:50:00 rossen-laptop kernel: [    1.215145] usb usb6: configuration #1 chosen from 1 choice
Jun 30 12:50:00 rossen-laptop kernel: [    1.215210] hub 6-0:1.0: USB hub found
Jun 30 12:50:00 rossen-laptop kernel: [    1.215225] hub 6-0:1.0: 2 ports detected
Jun 30 12:50:00 rossen-laptop kernel: [    1.215324] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Jun 30 12:50:00 rossen-laptop kernel: [    1.215337] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Jun 30 12:50:00 rossen-laptop kernel: [    1.215344] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jun 30 12:50:00 rossen-laptop kernel: [    1.215425] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
Jun 30 12:50:00 rossen-laptop kernel: [    1.215466] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f20
Jun 30 12:50:00 rossen-laptop kernel: [    1.215657] usb usb7: configuration #1 chosen from 1 choice
Jun 30 12:50:00 rossen-laptop kernel: [    1.215723] hub 7-0:1.0: USB hub found
Jun 30 12:50:00 rossen-laptop kernel: [    1.215738] hub 7-0:1.0: 2 ports detected
Jun 30 12:50:00 rossen-laptop kernel: [    1.215831] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Jun 30 12:50:00 rossen-laptop kernel: [    1.215844] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Jun 30 12:50:00 rossen-laptop kernel: [    1.215851] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jun 30 12:50:00 rossen-laptop kernel: [    1.215927] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
Jun 30 12:50:00 rossen-laptop kernel: [    1.215967] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
Jun 30 12:50:00 rossen-laptop kernel: [    1.216167] usb usb8: configuration #1 chosen from 1 choice
Jun 30 12:50:00 rossen-laptop kernel: [    1.216227] hub 8-0:1.0: USB hub found
Jun 30 12:50:00 rossen-laptop kernel: [    1.216246] hub 8-0:1.0: 2 ports detected
Jun 30 12:50:00 rossen-laptop kernel: [    1.216466] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jun 30 12:50:00 rossen-laptop kernel: [    1.217153] i8042.c: Warning: Keylock active.
Jun 30 12:50:00 rossen-laptop kernel: [    1.221994] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun 30 12:50:00 rossen-laptop kernel: [    1.222008] serio: i8042 AUX port at 0x60,0x64 irq 12
Jun 30 12:50:00 rossen-laptop kernel: [    1.222206] mice: PS/2 mouse device common for all mice
Jun 30 12:50:00 rossen-laptop kernel: [    1.222479] rtc_cmos 00:03: RTC can wake from S4
Jun 30 12:50:00 rossen-laptop kernel: [    1.222618] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Jun 30 12:50:00 rossen-laptop kernel: [    1.222662] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Jun 30 12:50:00 rossen-laptop kernel: [    1.222963] device-mapper: uevent: version 1.0.3
Jun 30 12:50:00 rossen-laptop kernel: [    1.223253] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Jun 30 12:50:00 rossen-laptop kernel: [    1.223423] device-mapper: multipath: version 1.1.0 loaded
Jun 30 12:50:00 rossen-laptop kernel: [    1.223429] device-mapper: multipath round-robin: version 1.0.0 loaded
Jun 30 12:50:00 rossen-laptop kernel: [    1.223950] cpuidle: using governor ladder
Jun 30 12:50:00 rossen-laptop kernel: [    1.224221] cpuidle: using governor menu
Jun 30 12:50:00 rossen-laptop kernel: [    1.224817] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Jun 30 12:50:00 rossen-laptop kernel: [    1.225060] TCP cubic registered
Jun 30 12:50:00 rossen-laptop kernel: [    1.225347] NET: Registered protocol family 10
Jun 30 12:50:00 rossen-laptop kernel: [    1.226363] lo: Disabled Privacy Extensions
Jun 30 12:50:00 rossen-laptop kernel: [    1.227029] NET: Registered protocol family 17
Jun 30 12:50:00 rossen-laptop kernel: [    1.228783] PM: Resume from disk failed.
Jun 30 12:50:00 rossen-laptop kernel: [    1.228794] registered taskstats version 1
Jun 30 12:50:00 rossen-laptop kernel: [    1.229278]   Magic number: 14:208:834
Jun 30 12:50:00 rossen-laptop kernel: [    1.229393] rtc_cmos 00:03: setting system clock to 2010-06-30 11:49:21 UTC (1277898561)
Jun 30 12:50:00 rossen-laptop kernel: [    1.229396] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun 30 12:50:00 rossen-laptop kernel: [    1.229397] EDD information not available.
Jun 30 12:50:00 rossen-laptop kernel: [    1.229444] Freeing unused kernel memory: 876k freed
Jun 30 12:50:00 rossen-laptop kernel: [    1.229770] Write protecting the kernel read-only data: 7680k
Jun 30 12:50:00 rossen-laptop kernel: [    1.242241] udev: starting version 151
Jun 30 12:50:00 rossen-laptop kernel: [    1.259245] ACPI: Battery Slot [BAT0] (battery present)
Jun 30 12:50:00 rossen-laptop kernel: [    1.341104] ahci 0000:00:1f.2: version 3.0
Jun 30 12:50:00 rossen-laptop kernel: [    1.341125] ahci 0000:00:1f.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Jun 30 12:50:00 rossen-laptop kernel: [    1.341180]   alloc irq_desc for 29 on node -1
Jun 30 12:50:00 rossen-laptop kernel: [    1.341182]   alloc kstat_irqs on node -1
Jun 30 12:50:00 rossen-laptop kernel: [    1.341193] ahci 0000:00:1f.2: irq 29 for MSI/MSI-X
Jun 30 12:50:00 rossen-laptop kernel: [    1.341244] ahci: SSS flag set, parallel bus scan disabled
Jun 30 12:50:00 rossen-laptop kernel: [    1.341276] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl RAID mode
Jun 30 12:50:00 rossen-laptop kernel: [    1.341279] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ccc ems sxs 
Jun 30 12:50:00 rossen-laptop kernel: [    1.341283] ahci 0000:00:1f.2: setting latency timer to 64
Jun 30 12:50:00 rossen-laptop kernel: [    1.341886] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
Jun 30 12:50:00 rossen-laptop kernel: [    1.341888] e1000e: Copyright (c) 1999-2008 Intel Corporation.
Jun 30 12:50:00 rossen-laptop kernel: [    1.349730] ohci1394 0000:03:01.0: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 30 12:50:00 rossen-laptop kernel: [    1.400151] scsi0 : ahci
Jun 30 12:50:00 rossen-laptop kernel: [    1.400270] scsi1 : ahci
Jun 30 12:50:00 rossen-laptop kernel: [    1.400313] scsi2 : ahci
Jun 30 12:50:00 rossen-laptop kernel: [    1.400356] scsi3 : ahci
Jun 30 12:50:00 rossen-laptop kernel: [    1.400400] scsi4 : ahci
Jun 30 12:50:00 rossen-laptop kernel: [    1.400443] scsi5 : ahci
Jun 30 12:50:00 rossen-laptop kernel: [    1.400803] ata1: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1c900 irq 29
Jun 30 12:50:00 rossen-laptop kernel: [    1.400806] ata2: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1c980 irq 29
Jun 30 12:50:00 rossen-laptop kernel: [    1.400807] ata3: DUMMY
Jun 30 12:50:00 rossen-laptop kernel: [    1.400808] ata4: DUMMY
Jun 30 12:50:00 rossen-laptop kernel: [    1.400811] ata5: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1cb00 irq 29
Jun 30 12:50:00 rossen-laptop kernel: [    1.400813] ata6: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1cb80 irq 29
Jun 30 12:50:00 rossen-laptop kernel: [    1.400876] e1000e 0000:00:19.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jun 30 12:50:00 rossen-laptop kernel: [    1.400883] e1000e 0000:00:19.0: setting latency timer to 64
Jun 30 12:50:00 rossen-laptop kernel: [    1.400974]   alloc irq_desc for 30 on node -1
Jun 30 12:50:00 rossen-laptop kernel: [    1.400975]   alloc kstat_irqs on node -1
Jun 30 12:50:00 rossen-laptop kernel: [    1.400984] e1000e 0000:00:19.0: irq 30 for MSI/MSI-X
Jun 30 12:50:00 rossen-laptop kernel: [    1.412067] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[f1bff800-f1bfffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Jun 30 12:50:00 rossen-laptop kernel: [    1.542525] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:24:e8:aa:de:97
Jun 30 12:50:00 rossen-laptop kernel: [    1.542528] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
Jun 30 12:50:00 rossen-laptop kernel: [    1.542552] 0000:00:19.0: eth0: MAC: 7, PHY: 8, PBA No: 6002ff-0ff
Jun 30 12:50:00 rossen-laptop kernel: [    1.620050] usb 1-6: new high speed USB device using ehci_hcd and address 3
Jun 30 12:50:00 rossen-laptop kernel: [    1.846565] usb 1-6: configuration #1 chosen from 1 choice
Jun 30 12:50:00 rossen-laptop kernel: [    1.930046] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 30 12:50:00 rossen-laptop kernel: [    1.931563] ata1.00: ATA-8: WDC WD2500BJKT-75F4T0, 11.01A11, max UDMA/133
Jun 30 12:50:00 rossen-laptop kernel: [    1.931566] ata1.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Jun 30 12:50:00 rossen-laptop kernel: [    1.933165] ata1.00: configured for UDMA/133
Jun 30 12:50:00 rossen-laptop kernel: [    1.950159] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BJKT-7 11.0 PQ: 0 ANSI: 5
Jun 30 12:50:00 rossen-laptop kernel: [    1.950297] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jun 30 12:50:00 rossen-laptop kernel: [    1.950335] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
Jun 30 12:50:00 rossen-laptop kernel: [    1.950389] sd 0:0:0:0: [sda] Write Protect is off
Jun 30 12:50:00 rossen-laptop kernel: [    1.950391] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jun 30 12:50:00 rossen-laptop kernel: [    1.950409] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 30 12:50:00 rossen-laptop kernel: [    1.950511]  sda: sda1 sda2 < sda5 > sda3 sda4
Jun 30 12:50:00 rossen-laptop kernel: [    2.006915] sd 0:0:0:0: [sda] Attached SCSI disk
Jun 30 12:50:00 rossen-laptop kernel: [    2.120047] usb 5-1: new full speed USB device using uhci_hcd and address 2
Jun 30 12:50:00 rossen-laptop kernel: [    2.300563] usb 5-1: configuration #0 chosen from 1 choice
Jun 30 12:50:00 rossen-laptop kernel: [    2.300565] usb 5-1: config 0 descriptor??
Jun 30 12:50:00 rossen-laptop kernel: [    2.730835] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[344fc000069e3490]
Jun 30 12:50:00 rossen-laptop kernel: [    2.880224] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 30 12:50:00 rossen-laptop kernel: [    2.882181] ata2.00: ATAPI: MATSHITA DVD+/-RW UJ862A, 1.02, max UDMA/33
Jun 30 12:50:00 rossen-laptop kernel: [    2.887668] ata2.00: configured for UDMA/33
Jun 30 12:50:00 rossen-laptop kernel: [    2.903690] scsi 1:0:0:0: CD-ROM            MATSHITA DVD+-RW UJ862A   1.02 PQ: 0 ANSI: 5
Jun 30 12:50:00 rossen-laptop kernel: [    2.918687] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Jun 30 12:50:00 rossen-laptop kernel: [    2.918690] Uniform CD-ROM driver Revision: 3.20
Jun 30 12:50:00 rossen-laptop kernel: [    2.918784] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jun 30 12:50:00 rossen-laptop kernel: [    2.918838] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jun 30 12:50:00 rossen-laptop kernel: [    3.260224] ata5: SATA link down (SStatus 0 SControl 300)
Jun 30 12:50:00 rossen-laptop kernel: [    3.630262] ata6: SATA link down (SStatus 0 SControl 300)
Jun 30 12:50:00 rossen-laptop kernel: [    3.973952] EXT3-fs: INFO: recovery required on readonly filesystem.
Jun 30 12:50:00 rossen-laptop kernel: [    3.973955] EXT3-fs: write access will be enabled during recovery.
Jun 30 12:50:00 rossen-laptop kernel: [    4.189784] kjournald starting.  Commit interval 5 seconds
Jun 30 12:50:00 rossen-laptop kernel: [    4.189795] EXT3-fs: recovery complete.
Jun 30 12:50:00 rossen-laptop kernel: [    4.190210] EXT3-fs: mounted filesystem with ordered data mode.
Jun 30 12:50:00 rossen-laptop kernel: [   37.874481] udev: starting version 151
Jun 30 12:50:00 rossen-laptop kernel: [   37.916157] lp: driver loaded but no devices found
Jun 30 12:50:00 rossen-laptop kernel: [   37.952619] Adding 9936160k swap on /dev/sda5.  Priority:-1 extents:1 across:9936160k 
Jun 30 12:50:00 rossen-laptop kernel: [   38.121957] acpi device:35: registered as cooling_device2
Jun 30 12:50:00 rossen-laptop kernel: [   38.124232] sdhci: Secure Digital Host Controller Interface driver
Jun 30 12:50:00 rossen-laptop kernel: [   38.124234] sdhci: Copyright(c) Pierre Ossman
Jun 30 12:50:00 rossen-laptop kernel: [   38.125149] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 21)
Jun 30 12:50:00 rossen-laptop kernel: [   38.125166] sdhci-pci 0000:03:01.1: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jun 30 12:50:00 rossen-laptop kernel: [   38.127238] Registered led device: mmc0::
Jun 30 12:50:00 rossen-laptop kernel: [   38.128264] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
Jun 30 12:50:00 rossen-laptop kernel: [   38.128663] ricoh-mmc: Ricoh MMC Controller disabling driver
Jun 30 12:50:00 rossen-laptop kernel: [   38.128665] ricoh-mmc: Copyright(c) Philip Langdale
Jun 30 12:50:00 rossen-laptop kernel: [   38.128677] ricoh-mmc: Ricoh MMC controller found at 0000:03:01.2 [1180:0843] (rev 11)
Jun 30 12:50:00 rossen-laptop kernel: [   38.128690] ricoh-mmc: Controller is now disabled.
Jun 30 12:50:00 rossen-laptop kernel: [   38.129472] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Jun 30 12:50:00 rossen-laptop kernel: [   38.129970] input: Dell WMI hotkeys as /devices/virtual/input/input5
Jun 30 12:50:00 rossen-laptop kernel: [   38.130623] [drm] Initialized drm 1.1.0 20060810
Jun 30 12:50:00 rossen-laptop kernel: [   38.137654] cfg80211: Calling CRDA to update world regulatory domain
Jun 30 12:50:00 rossen-laptop kernel: [   38.141196] Linux video capture interface: v2.00
Jun 30 12:50:00 rossen-laptop kernel: [   38.146506] uvcvideo: Found UVC 1.00 device Integrated_Webcam_2M (0c45:63f1)
Jun 30 12:50:00 rossen-laptop kernel: [   38.154766] input: Integrated_Webcam_2M as /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input6
Jun 30 12:50:00 rossen-laptop kernel: [   38.154811] usbcore: registered new interface driver uvcvideo
Jun 30 12:50:00 rossen-laptop kernel: [   38.154813] USB Video Class driver (v0.1.0)
Jun 30 12:50:00 rossen-laptop kernel: [   38.190056] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:33/LNXVIDEO:00/input/input7
Jun 30 12:50:00 rossen-laptop kernel: [   38.193257] type=1505 audit(1277898598.460:2):  operation="profile_load" pid=771 name="/sbin/dhclient3"
Jun 30 12:50:00 rossen-laptop kernel: [   38.193756] type=1505 audit(1277898598.460:3):  operation="profile_load" pid=771 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jun 30 12:50:00 rossen-laptop kernel: [   38.194025] type=1505 audit(1277898598.460:4):  operation="profile_load" pid=771 name="/usr/lib/connman/scripts/dhclient-script"
Jun 30 12:50:00 rossen-laptop kernel: [   38.196299] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Jun 30 12:50:00 rossen-laptop kernel: [   38.199890] cfg80211: World regulatory domain updated:
Jun 30 12:50:00 rossen-laptop kernel: [   38.199893] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun 30 12:50:00 rossen-laptop kernel: [   38.199895] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 12:50:00 rossen-laptop kernel: [   38.199897] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 30 12:50:00 rossen-laptop kernel: [   38.199899] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 30 12:50:00 rossen-laptop kernel: [   38.199901] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 12:50:00 rossen-laptop kernel: [   38.199903] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 12:50:00 rossen-laptop kernel: [   38.220917] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Jun 30 12:50:00 rossen-laptop kernel: [   38.220919] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Jun 30 12:50:00 rossen-laptop kernel: [   38.220981] iwlagn 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 30 12:50:00 rossen-laptop kernel: [   38.220989] iwlagn 0000:0c:00.0: setting latency timer to 64
Jun 30 12:50:00 rossen-laptop kernel: [   38.221044] iwlagn 0000:0c:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Jun 30 12:50:00 rossen-laptop kernel: [   38.245117] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 30 12:50:00 rossen-laptop kernel: [   38.245147] nouveau 0000:01:00.0: setting latency timer to 64
Jun 30 12:50:00 rossen-laptop kernel: [   38.246905] [drm] nouveau 0000:01:00.0: failed to evaluate _DSM: 5
Jun 30 12:50:00 rossen-laptop kernel: [   38.258724] iwlagn 0000:0c:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Jun 30 12:50:00 rossen-laptop kernel: [   38.258787]   alloc irq_desc for 31 on node -1
Jun 30 12:50:00 rossen-laptop kernel: [   38.258789]   alloc kstat_irqs on node -1
Jun 30 12:50:00 rossen-laptop kernel: [   38.258807] iwlagn 0000:0c:00.0: irq 31 for MSI/MSI-X
Jun 30 12:50:00 rossen-laptop kernel: [   38.259306] [drm] nouveau 0000:01:00.0: Detected an NV50 generation card (0x298d80a2)
Jun 30 12:50:00 rossen-laptop kernel: [   38.260090] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
Jun 30 12:50:00 rossen-laptop kernel: [   38.308000] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Jun 30 12:50:00 rossen-laptop kernel: [   38.308055] HDA Intel 0000:00:1b.0: setting latency timer to 64
Jun 30 12:50:00 rossen-laptop kernel: [   38.311797] phy0: Selected rate control algorithm 'iwl-agn-rs'
Jun 30 12:50:00 rossen-laptop kernel: [   38.365155] [drm] nouveau 0000:01:00.0: ... appears to be valid
Jun 30 12:50:00 rossen-laptop kernel: [   38.365159] [drm] nouveau 0000:01:00.0: BIT BIOS found
Jun 30 12:50:00 rossen-laptop kernel: [   38.365161] [drm] nouveau 0000:01:00.0: Bios version 62.98.43.00
Jun 30 12:50:00 rossen-laptop kernel: [   38.365164] [drm] nouveau 0000:01:00.0: TMDS table revision 2.0 not currently supported
Jun 30 12:50:00 rossen-laptop kernel: [   38.365166] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 4.0
Jun 30 12:50:00 rossen-laptop kernel: [   38.365169] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x40 5 16 4
Jun 30 12:50:00 rossen-laptop kernel: [   38.365171] [drm] nouveau 0000:01:00.0:   0: 0x00000041: type 0x41 idx 0 tag 0xff
Jun 30 12:50:00 rossen-laptop kernel: [   38.365173] [drm] nouveau 0000:01:00.0:   1: 0x00000100: type 0x00 idx 1 tag 0xff
Jun 30 12:50:00 rossen-laptop kernel: [   38.365175] [drm] nouveau 0000:01:00.0:   2: 0x00005246: type 0x46 idx 2 tag 0x07
Jun 30 12:50:00 rossen-laptop kernel: [   38.365177] [drm] nouveau 0000:01:00.0:   3: 0x0000a346: type 0x46 idx 3 tag 0x08
Jun 30 12:50:00 rossen-laptop kernel: [   38.365179] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 01000323 00010034
Jun 30 12:50:00 rossen-laptop kernel: [   38.365181] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 02011300 00000028
Jun 30 12:50:00 rossen-laptop kernel: [   38.365182] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 02022386 0f200010
Jun 30 12:50:00 rossen-laptop kernel: [   38.365184] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 02022332 00020010
Jun 30 12:50:00 rossen-laptop kernel: [   38.365185] [drm] nouveau 0000:01:00.0: Raw DCB entry 4: 040333a6 0f200010
Jun 30 12:50:00 rossen-laptop kernel: [   38.365187] [drm] nouveau 0000:01:00.0: Raw DCB entry 5: 04033312 00020010
Jun 30 12:50:00 rossen-laptop kernel: [   38.365188] [drm] nouveau 0000:01:00.0: Raw DCB entry 6: 0000000e 00000000
Jun 30 12:50:00 rossen-laptop kernel: [   38.365204] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xD70A
Jun 30 12:50:00 rossen-laptop kernel: [   38.426468] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
Jun 30 12:50:00 rossen-laptop kernel: [   38.453681] input: HDA Intel Mic at Sep Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
Jun 30 12:50:00 rossen-laptop kernel: [   38.453821] input: HDA Intel Mic at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
Jun 30 12:50:00 rossen-laptop kernel: [   38.453908] input: HDA Intel Line Out at Sep Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
Jun 30 12:50:00 rossen-laptop kernel: [   38.453991] input: HDA Intel HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
Jun 30 12:50:00 rossen-laptop kernel: [   38.460165] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xDABC
Jun 30 12:50:00 rossen-laptop kernel: [   38.520063] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xE36B
Jun 30 12:50:00 rossen-laptop kernel: [   38.520084] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xE45D
Jun 30 12:50:00 rossen-laptop kernel: [   38.540145] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xE66D
Jun 30 12:50:00 rossen-laptop kernel: [   38.540158] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table at offset 0xE6D2
Jun 30 12:50:00 rossen-laptop kernel: [   38.570088] [drm] nouveau 0000:01:00.0: 0xE6D2: Condition still not met after 20ms, skipping following opcodes
Jun 30 12:50:00 rossen-laptop kernel: [   38.570107] [drm] nouveau 0000:01:00.0: 0xC2BA: parsing output script 0
Jun 30 12:50:00 rossen-laptop kernel: [   38.570111] [drm] nouveau 0000:01:00.0: 0xC8F6: parsing output script 0
Jun 30 12:50:00 rossen-laptop kernel: [   38.570115] [drm] nouveau 0000:01:00.0: 0xC6DE: parsing output script 0
Jun 30 12:50:00 rossen-laptop kernel: [   38.570129] [drm] nouveau 0000:01:00.0: 0xC8F6: parsing output script 0
Jun 30 12:50:00 rossen-laptop kernel: [   38.570132] [drm] nouveau 0000:01:00.0: 0xC6DE: parsing output script 0
Jun 30 12:50:00 rossen-laptop kernel: [   38.730369] [TTM] Zone  kernel: Available graphics memory: 2023260 kiB.
Jun 30 12:50:00 rossen-laptop kernel: [   38.730386] [drm] nouveau 0000:01:00.0: 256 MiB VRAM
Jun 30 12:50:00 rossen-laptop kernel: [   38.754450] [drm] nouveau 0000:01:00.0: 512 MiB GART (aperture)
Jun 30 12:50:00 rossen-laptop kernel: [   38.754458] mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining
Jun 30 12:50:00 rossen-laptop kernel: [   38.754782] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1
Jun 30 12:50:00 rossen-laptop kernel: [   38.760018] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1
Jun 30 12:50:00 rossen-laptop kernel: [   38.761019] [drm] nouveau 0000:01:00.0: Detected a LVDS output
Jun 30 12:50:00 rossen-laptop kernel: [   38.761030] [drm] nouveau 0000:01:00.0: Detected a DAC output
Jun 30 12:50:00 rossen-laptop kernel: [   38.761032] [drm] nouveau 0000:01:00.0: Detected a DP output
Jun 30 12:50:00 rossen-laptop kernel: [   38.761033] [drm] nouveau 0000:01:00.0: Detected a TMDS output
Jun 30 12:50:00 rossen-laptop kernel: [   38.761036] [drm] nouveau 0000:01:00.0: Detected a DP output
Jun 30 12:50:00 rossen-laptop kernel: [   38.761038] [drm] nouveau 0000:01:00.0: Detected a TMDS output
Jun 30 12:50:00 rossen-laptop kernel: [   38.761040] [drm] nouveau 0000:01:00.0: Detected a LVDS connector
Jun 30 12:50:00 rossen-laptop kernel: [   38.800663] EXT3 FS on sda1, internal journal
Jun 30 12:50:00 rossen-laptop kernel: [   38.832362] input: DualPoint Stick as /devices/platform/i8042/serio1/input/input13
Jun 30 12:50:00 rossen-laptop kernel: [   38.849738] input: AlpsPS/2 ALPS DualPoint TouchPad as /devices/platform/i8042/serio1/input/input14
Jun 30 12:50:00 rossen-laptop kernel: [   38.876209] [drm] nouveau 0000:01:00.0: Detected a VGA connector
Jun 30 12:50:00 rossen-laptop kernel: [   38.876281] [drm] nouveau 0000:01:00.0: Detected a DisplayPort connector
Jun 30 12:50:00 rossen-laptop kernel: [   38.876339] [drm] nouveau 0000:01:00.0: Detected a DisplayPort connector
Jun 30 12:50:00 rossen-laptop kernel: [   39.958914] dell-wmi: Unknown key ffd0 pressed
Jun 30 12:50:00 rossen-laptop kernel: [   40.001248] [drm] nouveau 0000:01:00.0: allocated 1440x900 fb: 0x40250000, bo ffff88010323a600
Jun 30 12:50:00 rossen-laptop kernel: [   40.001328] fb0: nouveaufb frame buffer device
Jun 30 12:50:00 rossen-laptop kernel: [   40.001329] registered panic notifier
Jun 30 12:50:00 rossen-laptop kernel: [   40.001334] [drm] Initialized nouveau 0.0.15 20090420 for 0000:01:00.0 on minor 0
Jun 30 12:50:00 rossen-laptop kernel: [   40.002979] vga16fb: initializing
Jun 30 12:50:00 rossen-laptop kernel: [   40.002981] vga16fb: mapped to 0xffff8800000a0000
Jun 30 12:50:00 rossen-laptop kernel: [   40.002984] vga16fb: not registering due to another framebuffer present
Jun 30 12:50:00 rossen-laptop kernel: [   40.011846] [drm] nouveau 0000:01:00.0: 0xC2BE: parsing output script 1
Jun 30 12:50:00 rossen-laptop kernel: [   40.011882] [drm] nouveau 0000:01:00.0: 0xC175: parsing clock script 0
Jun 30 12:50:00 rossen-laptop kernel: [   40.012934] Console: switching to colour frame buffer device 180x56
Jun 30 12:50:00 rossen-laptop kernel: [   40.280860] [drm] nouveau 0000:01:00.0: 0xC2B5: parsing clock script 1
Jun 30 12:50:00 rossen-laptop kernel: [   40.319860] dell-wmi: Unknown key ffd1 pressed
Jun 30 12:50:00 rossen-laptop kernel: [   40.376273] kjournald starting.  Commit interval 5 seconds
Jun 30 12:50:00 rossen-laptop kernel: [   40.376279] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
Jun 30 12:50:00 rossen-laptop kernel: [   40.376462] EXT3 FS on sda3, internal journal
Jun 30 12:50:00 rossen-laptop kernel: [   40.376466] EXT3-fs: mounted filesystem with ordered data mode.
Jun 30 12:50:00 rossen-laptop NetworkManager: <info>  starting...
Jun 30 12:50:00 rossen-laptop NetworkManager: <info>  Trying to start the modem-manager...
Jun 30 12:50:00 rossen-laptop NetworkManager:    SCPlugin-Ifupdown: init!
Jun 30 12:50:00 rossen-laptop NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Jun 30 12:50:00 rossen-laptop NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Jun 30 12:50:00 rossen-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:19.0/net/eth0, iface: eth0)
Jun 30 12:50:00 rossen-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:19.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jun 30 12:50:00 rossen-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/wlan0, iface: wlan0)
Jun 30 12:50:00 rossen-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun 30 12:50:00 rossen-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jun 30 12:50:00 rossen-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jun 30 12:50:00 rossen-laptop NetworkManager:    SCPlugin-Ifupdown: end _init.
Jun 30 12:50:00 rossen-laptop NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jun 30 12:50:00 rossen-laptop NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jun 30 12:50:00 rossen-laptop NetworkManager: <info>  Found wlan radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/ieee80211/phy0/rfkill0) (driver <unknown>)
Jun 30 12:50:00 rossen-laptop NetworkManager: <info>  WiFi disabled by radio killswitch; disabled by state file
Jun 30 12:50:00 rossen-laptop NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
Jun 30 12:50:00 rossen-laptop NetworkManager:    SCPlugin-Ifupdown: (18324768) ... get_connections.
Jun 30 12:50:00 rossen-laptop NetworkManager:    SCPlugin-Ifupdown: (18324768) ... get_connections (managed=false): return empty list.
Jun 30 12:50:00 rossen-laptop avahi-daemon[1026]: Found user 'avahi' (UID 110) and group 'avahi' (GID 119).
Jun 30 12:50:00 rossen-laptop avahi-daemon[1026]: Successfully dropped root privileges.
Jun 30 12:50:00 rossen-laptop avahi-daemon[1026]: avahi-daemon 0.6.25 starting up.
Jun 30 12:50:00 rossen-laptop avahi-daemon[1026]: Successfully called chroot().
Jun 30 12:50:00 rossen-laptop avahi-daemon[1026]: Successfully dropped remaining capabilities.
Jun 30 12:50:00 rossen-laptop modem-manager: Loaded plugin Huawei
Jun 30 12:50:00 rossen-laptop modem-manager: Loaded plugin Novatel
Jun 30 12:50:00 rossen-laptop modem-manager: Loaded plugin Ericsson MBM
Jun 30 12:50:00 rossen-laptop modem-manager: Loaded plugin AnyData
Jun 30 12:50:00 rossen-laptop modem-manager: Loaded plugin Gobi
Jun 30 12:50:00 rossen-laptop modem-manager: Loaded plugin Sierra
Jun 30 12:50:00 rossen-laptop modem-manager: Loaded plugin ZTE
Jun 30 12:50:00 rossen-laptop modem-manager: Loaded plugin MotoC
Jun 30 12:50:00 rossen-laptop modem-manager: Loaded plugin Longcheer
Jun 30 12:50:00 rossen-laptop modem-manager: Loaded plugin Option
Jun 30 12:50:00 rossen-laptop modem-manager: Loaded plugin Option High-Speed
Jun 30 12:50:00 rossen-laptop modem-manager: Loaded plugin Generic
Jun 30 12:50:00 rossen-laptop modem-manager: Loaded plugin Nokia
Jun 30 12:50:00 rossen-laptop kernel: [   40.426343] type=1505 audit(1277898600.690:5):  operation="profile_load" pid=1043 name="/usr/share/gdm/guest-session/Xsession"
Jun 30 12:50:00 rossen-laptop kernel: [   40.427530] type=1505 audit(1277898600.690:6):  operation="profile_replace" pid=1044 name="/sbin/dhclient3"
Jun 30 12:50:00 rossen-laptop kernel: [   40.428035] type=1505 audit(1277898600.690:7):  operation="profile_replace" pid=1044 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jun 30 12:50:00 rossen-laptop kernel: [   40.428308] type=1505 audit(1277898600.690:8):  operation="profile_replace" pid=1044 name="/usr/lib/connman/scripts/dhclient-script"
Jun 30 12:50:00 rossen-laptop kernel: [   40.430511] type=1505 audit(1277898600.700:9):  operation="profile_load" pid=1045 name="/usr/bin/evince"
Jun 30 12:50:00 rossen-laptop avahi-daemon[1026]: No service file found in /etc/avahi/services.
Jun 30 12:50:00 rossen-laptop kernel: [   40.436730] type=1505 audit(1277898600.700:10):  operation="profile_load" pid=1045 name="/usr/bin/evince-previewer"
Jun 30 12:50:00 rossen-laptop kernel: [   40.440658] type=1505 audit(1277898600.710:11):  operation="profile_load" pid=1045 name="/usr/bin/evince-thumbnailer"
Jun 30 12:50:00 rossen-laptop avahi-daemon[1026]: Network interface enumeration completed.
Jun 30 12:50:00 rossen-laptop avahi-daemon[1026]: Registering HINFO record with values 'X86_64'/'LINUX'.
Jun 30 12:50:00 rossen-laptop avahi-daemon[1026]: Server startup complete. Host name is rossen-laptop.local. Local service cookie is 3126311024.
Jun 30 12:50:00 rossen-laptop gdm-binary[1010]: WARNING: Unable to find users: no seat-id found
Jun 30 12:50:00 rossen-laptop NetworkManager:    Ifupdown: get unmanaged devices count: 0
Jun 30 12:50:00 rossen-laptop NetworkManager: <info>  (eth0): carrier is OFF
Jun 30 12:50:00 rossen-laptop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'e1000e')
Jun 30 12:50:00 rossen-laptop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jun 30 12:50:00 rossen-laptop NetworkManager: <info>  (eth0): now managed
Jun 30 12:50:00 rossen-laptop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Jun 30 12:50:00 rossen-laptop NetworkManager: <info>  (eth0): bringing up device.
Jun 30 12:50:00 rossen-laptop kernel: [   40.590477] e1000e 0000:00:19.0: irq 30 for MSI/MSI-X
Jun 30 12:50:00 rossen-laptop NetworkManager: <info>  (eth0): preparing device.
Jun 30 12:50:00 rossen-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Jun 30 12:50:00 rossen-laptop NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:19.0/net/eth0
Jun 30 12:50:00 rossen-laptop NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01).
Jun 30 12:50:00 rossen-laptop NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'iwlagn')
Jun 30 12:50:00 rossen-laptop NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jun 30 12:50:00 rossen-laptop NetworkManager: <info>  (wlan0): now managed
Jun 30 12:50:00 rossen-laptop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Jun 30 12:50:00 rossen-laptop NetworkManager: <info>  (wlan0): bringing up device.
Jun 30 12:50:00 rossen-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Jun 30 12:50:00 rossen-laptop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jun 30 12:50:00 rossen-laptop NetworkManager: <info>  modem-manager is now available
Jun 30 12:50:00 rossen-laptop NetworkManager: <info>  Trying to start the supplicant...
Jun 30 12:50:00 rossen-laptop NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle
Jun 30 12:50:00 rossen-laptop kernel: [   40.650120] e1000e 0000:00:19.0: irq 30 for MSI/MSI-X
Jun 30 12:50:00 rossen-laptop kernel: [   40.650626] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 30 12:50:01 rossen-laptop gdm-binary[1010]: WARNING: GdmDisplay: display lasted 0.323914 seconds
Jun 30 12:50:01 rossen-laptop init: apport pre-start process (1180) terminated with status 1
Jun 30 12:50:01 rossen-laptop cron[1189]: (CRON) INFO (pidfile fd = 3)
Jun 30 12:50:01 rossen-laptop acpid: starting up with proc fs
Jun 30 12:50:01 rossen-laptop acpid: 36 rules loaded
Jun 30 12:50:01 rossen-laptop acpid: waiting for events: event logging is off
Jun 30 12:50:01 rossen-laptop anacron[1212]: Anacron 2.3 started on 2010-06-30
Jun 30 12:50:01 rossen-laptop init: apport post-stop process (1198) terminated with status 1
Jun 30 12:50:01 rossen-laptop cron[1239]: (CRON) STARTUP (fork ok)
Jun 30 12:50:01 rossen-laptop cron[1239]: (CRON) INFO (Running @reboot jobs)
Jun 30 12:50:01 rossen-laptop anacron[1212]: Normal exit (0 jobs run)
Jun 30 12:50:01 rossen-laptop kernel: [   41.117228] ppdev: user-space parallel port driver
Jun 30 12:50:01 rossen-laptop mysqld_safe[1419]: started
Jun 30 12:50:02 rossen-laptop /etc/mysql/debian-start[1458]: Upgrading MySQL tables if necessary.
Jun 30 12:50:02 rossen-laptop /etc/mysql/debian-start[1463]: Looking for 'mysql' as: /usr/bin/mysql
Jun 30 12:50:02 rossen-laptop /etc/mysql/debian-start[1463]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
Jun 30 12:50:02 rossen-laptop /etc/mysql/debian-start[1463]: This installation of MySQL is already upgraded to 5.0.83, use --force if you still need to run mysql_upgrade
Jun 30 12:50:02 rossen-laptop /etc/mysql/debian-start[1479]: Checking for insecure root accounts.
Jun 30 12:50:02 rossen-laptop /etc/mysql/debian-start[1490]: Triggering myisam-recover for all MyISAM tables
Jun 30 12:50:02 rossen-laptop kernel: [   42.538353] /dev/vmmon[1522]: Module vmmon: registered with major=10 minor=165
Jun 30 12:50:02 rossen-laptop kernel: [   42.538363] /dev/vmmon[1522]: Initial HV check: anyNotCapable=0 anyUnlocked=0 anyEnabled=0 anyDisabled=1
Jun 30 12:50:02 rossen-laptop kernel: [   42.538367] /dev/vmmon[1522]: HV check: anyNotCapable=0 anyUnlocked=0 anyEnabled=0 anyDisabled=1
Jun 30 12:50:02 rossen-laptop kernel: [   42.538369] /dev/vmmon[1522]: Module vmmon: initialized
Jun 30 12:50:02 rossen-laptop kernel: [   42.545288] /dev/vmci[1532]: VMCI: Driver initialized.
Jun 30 12:50:02 rossen-laptop kernel: [   42.545560] /dev/vmci[1532]: Module vmci: registered with major=10 minor=55
Jun 30 12:50:02 rossen-laptop kernel: [   42.545562] /dev/vmci[1532]: Module vmci: initialized
Jun 30 12:50:02 rossen-laptop vmnetBridge: Daemon created.
Jun 30 12:50:03 rossen-laptop vmnet-dhcpd: Internet Software Consortium DHCP Server 2.0
Jun 30 12:50:03 rossen-laptop vmnet-dhcpd: Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
Jun 30 12:50:03 rossen-laptop vmnet-dhcpd: All rights reserved.
Jun 30 12:50:03 rossen-laptop vmnet-dhcpd: 
Jun 30 12:50:03 rossen-laptop vmnet-dhcpd: Please contribute if you find this software useful.
Jun 30 12:50:03 rossen-laptop vmnet-dhcpd: For info, please visit http://www.isc.org/dhcp-contrib.html
Jun 30 12:50:03 rossen-laptop vmnet-dhcpd: 
Jun 30 12:50:03 rossen-laptop vmnet-dhcpd: Configured subnet: 192.168.208.0
Jun 30 12:50:03 rossen-laptop vmnet-dhcpd: Setting vmnet-dhcp IP address: 192.168.208.254
Jun 30 12:50:03 rossen-laptop vmnet-dhcpd: Recving on     VNet/vmnet1/192.168.208.0
Jun 30 12:50:03 rossen-laptop vmnet-dhcpd: Sending on     VNet/vmnet1/192.168.208.0
Jun 30 12:50:03 rossen-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/vmnet1, iface: vmnet1)
Jun 30 12:50:03 rossen-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/vmnet1, iface: vmnet1): no ifupdown configuration found.
Jun 30 12:50:03 rossen-laptop NetworkManager: <WARN>  device_creator(): /sys/devices/virtual/net/vmnet1: couldn't determine device driver; ignoring...
Jun 30 12:50:03 rossen-laptop avahi-daemon[1026]: Joining mDNS multicast group on interface vmnet1.IPv4 with address 192.168.208.1.
Jun 30 12:50:03 rossen-laptop avahi-daemon[1026]: New relevant interface vmnet1.IPv4 for mDNS.
Jun 30 12:50:03 rossen-laptop avahi-daemon[1026]: Registering new address record for 192.168.208.1 on vmnet1.IPv4.
Jun 30 12:50:03 rossen-laptop vmnet-dhcpd: Internet Software Consortium DHCP Server 2.0
Jun 30 12:50:03 rossen-laptop vmnet-dhcpd: Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
Jun 30 12:50:03 rossen-laptop vmnet-dhcpd: All rights reserved.
Jun 30 12:50:03 rossen-laptop vmnet-dhcpd: 
Jun 30 12:50:03 rossen-laptop vmnet-dhcpd: Please contribute if you find this software useful.
Jun 30 12:50:03 rossen-laptop vmnet-dhcpd: For info, please visit http://www.isc.org/dhcp-contrib.html
Jun 30 12:50:03 rossen-laptop vmnet-dhcpd: 
Jun 30 12:50:03 rossen-laptop kernel: [   43.282675] /dev/vmnet: open called by PID 1621 (vmnet-dhcpd)
Jun 30 12:50:03 rossen-laptop kernel: [   43.282683] /dev/vmnet: hub 1 does not exist, allocating memory.
Jun 30 12:50:03 rossen-laptop kernel: [   43.282699] /dev/vmnet: port on hub 1 successfully opened
Jun 30 12:50:03 rossen-laptop kernel: [   43.284232] /dev/vmnet: open called by PID 1623 (vmnet-netifup)
Jun 30 12:50:03 rossen-laptop kernel: [   43.284239] /dev/vmnet: port on hub 1 successfully opened
Jun 30 12:50:03 rossen-laptop vmnet-dhcpd: Configured subnet: 192.168.98.0
Jun 30 12:50:03 rossen-laptop vmnet-dhcpd: Setting vmnet-dhcp IP address: 192.168.98.254
Jun 30 12:50:03 rossen-laptop vmnet-dhcpd: Recving on     VNet/vmnet8/192.168.98.0
Jun 30 12:50:03 rossen-laptop vmnet-dhcpd: Sending on     VNet/vmnet8/192.168.98.0
Jun 30 12:50:03 rossen-laptop kernel: [   43.335111] /dev/vmnet: open called by PID 1626 (vmnet-dhcpd)
Jun 30 12:50:03 rossen-laptop kernel: [   43.335121] /dev/vmnet: hub 8 does not exist, allocating memory.
Jun 30 12:50:03 rossen-laptop kernel: [   43.335138] /dev/vmnet: port on hub 8 successfully opened
Jun 30 12:50:03 rossen-laptop kernel: [   43.338154] /dev/vmnet: open called by PID 1631 (vmnet-natd)
Jun 30 12:50:03 rossen-laptop kernel: [   43.338162] /dev/vmnet: port on hub 8 successfully opened
Jun 30 12:50:03 rossen-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/vmnet8, iface: vmnet8)
Jun 30 12:50:03 rossen-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/vmnet8, iface: vmnet8): no ifupdown configuration found.
Jun 30 12:50:03 rossen-laptop NetworkManager: <WARN>  device_creator(): /sys/devices/virtual/net/vmnet8: couldn't determine device driver; ignoring...
Jun 30 12:50:03 rossen-laptop avahi-daemon[1026]: Joining mDNS multicast group on interface vmnet8.IPv4 with address 192.168.98.1.
Jun 30 12:50:03 rossen-laptop avahi-daemon[1026]: New relevant interface vmnet8.IPv4 for mDNS.
Jun 30 12:50:03 rossen-laptop avahi-daemon[1026]: Registering new address record for 192.168.98.1 on vmnet8.IPv4.
Jun 30 12:50:03 rossen-laptop kernel: [   43.346145] /dev/vmnet: open called by PID 1632 (vmnet-netifup)
Jun 30 12:50:03 rossen-laptop kernel: [   43.346153] /dev/vmnet: port on hub 8 successfully opened
Jun 30 12:50:03 rossen-laptop vmnet-detect[1637]: NetDetectDaemonInit: No host policy file found. Not initializing filter.
Jun 30 12:50:03 rossen-laptop vmnet-detect[1637]: Unable to initialize the daemon
Jun 30 12:50:03 rossen-laptop init: plymouth-stop pre-start process (1644) terminated with status 1
Jun 30 12:50:04 rossen-laptop avahi-daemon[1026]: Registering new address record for fe80::250:56ff:fec0:1 on vmnet1.*.
Jun 30 12:50:04 rossen-laptop avahi-daemon[1026]: Registering new address record for fe80::250:56ff:fec0:8 on vmnet8.*.
Jun 30 12:50:13 rossen-laptop kernel: [   53.510241] vmnet1: no IPv6 routers present
Jun 30 12:50:13 rossen-laptop kernel: [   53.590203] vmnet8: no IPv6 routers present
```

---

### Post by rstoya05-lx on 2010-07-02
This really sucks! I'm continuing to have this problem.

I've been using Ubuntu for over 3 years now and it's moments like these when I wish I could pay for some kind of support incident. This is crazy. Imagine I show up at a client and I'm rebooting several times till I can get my laptop to come up successfully. It gives Windoze users a reason to feel smug.

---

### Post by bloodorange on 2010-07-03
Just to say, I'm getting the same problem - random hangs (at the "Ubuntu dots" screen) at startup.  This started happening after the last kernel update to 2.6.32-23.

I'm on a Dell XPS M1530.  I've hardly had any problems with Ubuntu and this laptop up until now.

---

### Post by DrMajorMcCheese on 2010-07-07
I have been experiencing the same problems with Lucid Lynx on my Dell XPS M1530 with kernel 2.6.32-23.  As a workaround I've started booting from 2.6.32-22.

---

### Post by pogz on 2010-07-25
ive used webmin to configure my dhcp to static and ubuntu throws this error on the network interface. 

network-interface (eth0) pre-start process (494) terminated with status 1
network-interface (eth0) post-stop process (518) terminated with status 1 ..

seriously, i think 10.04 would be better.. but now i think im better off with my old 8.x installation.

---

### Post by rstoya05-lx on 2010-08-03
I'm continuing to experience this on a regular basis, every 3rd or 4th boot or so. Unfortunately suspend has not been working for me since 9.04 so that doesn't help much as I'm forced to boot every time.

The only thing else I can add is I've observed there is nothing I need to do, just try more than once and usually by the 3rd time it manages to get to the login screen. 

I get either a blank screen or a screen with colours that says "Ubuntu" with dots below it. I press power once and it boots down promptly. Then I press power again to start.

---

### Post by aduxas on 2010-10-24
I am seeing the same issue with Kubuntu.  It hangs on the blue screen with the five dots, but will start normally the next time.  I am running 2.6.32-25.  It is not systematic; i.e. often it boots OK the first time.

---

### Post by marbss on 2010-10-24
what video card does your setup use?

I know for my old IBM X40 thinkpad laptop I have had Intel video issues -- which Ubuntu 10.xx that require modifications -- which I why I have not upgraded that laptop from 9.XX.

---

### Post by aduxas on 2010-10-24
> **marbss said:**
> what video card does your setup use?
nVidia Corporation NV11GL [Quadro2 MXR/EX/Go] (rev b2)

Actually, the blue screen with the five dots is already full graphics; I doubt that has anything to do with it.

---

### Post by Gerald here on 2010-11-26
Hi there, 

   I got the same problem and I got ATI graphics and Ubuntu 10.10 (Maverick) 64-bit. 
My notebook hangs about every 2nd or 3rd boot on a black screen (no ubuntu or dots, but at the boot stage, at which the ubuntu dots should normally come). I got this since installing 10.10 2 months ago or so. Before I had 10.04 and as far as I remember it didn't happen there (But the computer is only 2 or 3 months old, so can't remember for sure). Any Ideas ?

---

### Post by mardop on 2010-11-30
I believe, this is not a matter of displaydriver or so. When the ubuntu screen with the dots is there, press ESC, then you will see where your computer hangs. You probably have cif or nfs mounts in your /etc/fstab and the mounts are not available, the moment, you boot your desktop, say the server from where you try to mount is not running or so. If the server is running, you can boot. If it is not, ubuntu hangs at that dot-screen...
If you comment out the cifs (or nfs) mounts in fstab then you can boot, even if the referenced device is not there, say the server - or whatever you try to mount - is not running.
This was so in 10.4 and is still so in 10.10. I wonder, if ubuntu will ever solve this issue. Even hard to find anything in the forums or by googling...

Edit: I just found a solution. If your problem was related to what I described, hang on! Add nobootwait to the lines in your fstab (......,nobootwait 0 0).
See also:
[https://bugs.launchpad.net/ubuntu-release-notes/+bug/510415](https://bugs.launchpad.net/ubuntu-release-notes/+bug/510415) and maybe
[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/571444](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/571444)

---

### Post by Gerald here on 2010-12-09
Now I finally found a solution and it definitively fixed my problem ! It's something with the splash screen; Changing it to the Solar theme as described in this thread worked for me: [http://ubuntuforums.org/showthread.php?t=1503509&page=2](http://ubuntuforums.org/showthread.php?t=1503509&page=2)

Btw. thanks for your reply mardop. I haven't tried your solution, as I don't need to anymore :) Anyway, before editing files, I'd advice others with the same problem to change the splash screen first and see if this works, as I think the chance of breaking anything is lower here.

---

### Post by uncoolbob on 2010-12-20
Just want to say, I get this intermittent hanging on boot also.  UNR 10.04 on an eee pc 1008HA - seems to happen more when there's no network available, and usually the next boot is fine (only ctrl-alt-delete will interrupt the hanging).  On this machine it hangs at the blank screen with a small cursor top left.  It seems to be a larger cursor when booting properly.

Anyway, I'll investigate the solutions later.  Just adding this reply to help me find it later.

---

### Post by rstoya05-lx on 2010-12-21
I have "Nvidia Quadro FX 370M 256MB dedicated video card" (from the specs for Dell Precision M2400). I'm using the Open Source Nouveau driver. 

I've noticed that if I don't connect to an external monitor this happens a lot less. I usually use gnome-display-properties to disconnect when I'm done. Maybe some settings remain if I don't do that.

---

