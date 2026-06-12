---
title: "Natty: Fujitsu Lifebook S6410 won't hibernate or suspend"
date: 2011-08-01
forum: Hardware
---

### Post by samsanchez on 2011-08-01
My Fujitsu Lifebook S6410 running Ubuntu 11.04 won't suspend or hibernate.

When I suspend, the screen goes blank but is still on, some lights flash, and it won't come alive again. In the end I have to hold down the off button to force it to shut down.

Same 'symptoms' with hibernate, except there is a blinking cursor in the top left corner of the black screen.

Does anyone know why this is happening? Can I fix it?

---

### Post by lex0r on 2011-08-11
Same symptoms on Fujitsu Lifebook AH350 with the same Ubuntu version.
There may be a solution for this, but the thread has been dead for a week,.. :(

---

### Post by Toz on 2011-08-11
Let's start with the basics. Can you post back the contents of these two files:
- /var/log/pm-suspend.log
- /var/log/syslog

And the results of running this command from a terminal:
```
cat /var/log/dmesg | grep "PM:"
```

---

### Post by samsanchez on 2011-08-11
/var/log/pm-suspend.log doesn't have anything in it.

cat /var/log/dmesg | grep "PM:"

```
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    1.018378] PM: Hibernation image not present or could not be loaded.
```

---

### Post by samsanchez on 2011-08-11
I'll have to post /var/log/syslog in two parts because its too big.

Part 1:

```
Aug 10 21:53:25 sam-LIFEBOOK-S6410 rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="762" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Aug 10 21:54:09 sam-LIFEBOOK-S6410 anacron[2754]: Job `cron.daily' terminated
Aug 10 21:54:09 sam-LIFEBOOK-S6410 anacron[2754]: Normal exit (1 job run)
Aug 10 22:17:01 sam-LIFEBOOK-S6410 CRON[3380]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 10 22:50:04 sam-LIFEBOOK-S6410 AptDaemon: INFO: Initializing daemon
Aug 10 22:50:05 sam-LIFEBOOK-S6410 AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'flashplugin-installer')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s'))
Aug 10 22:50:05 sam-LIFEBOOK-S6410 AptDaemon.Trans: INFO: Queuing transaction /org/debian/apt/transaction/ea0fb67a1f83417fbae7d4a1eccef58c
Aug 10 22:56:05 sam-LIFEBOOK-S6410 AptDaemon: INFO: Quitting due to inactivity
Aug 10 22:56:05 sam-LIFEBOOK-S6410 AptDaemon: INFO: Shutdown was requested
Aug 10 22:56:17 sam-LIFEBOOK-S6410 AptDaemon: INFO: Initializing daemon
Aug 10 22:56:18 sam-LIFEBOOK-S6410 AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'flashplugin-installer')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s'))
Aug 10 22:56:18 sam-LIFEBOOK-S6410 AptDaemon.Trans: INFO: Queuing transaction /org/debian/apt/transaction/e2aa02e14d8841fd95c79a475ada69c8
Aug 10 22:56:39 sam-LIFEBOOK-S6410 AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/e2aa02e14d8841fd95c79a475ada69c8
Aug 10 22:56:42 sam-LIFEBOOK-S6410 AptDaemon.Worker: INFO: Committing packages: dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'flashplugin-installer')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Aug 10 22:56:43 sam-LIFEBOOK-S6410 AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/e2aa02e14d8841fd95c79a475ada69c8
Aug 10 22:56:43 sam-LIFEBOOK-S6410 AptDaemon.Worker: INFO: Committing packages: dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'flashplugin-installer')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Aug 10 22:57:30 sam-LIFEBOOK-S6410 AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/e2aa02e14d8841fd95c79a475ada69c8
Aug 10 23:03:18 sam-LIFEBOOK-S6410 AptDaemon: INFO: Quitting due to inactivity
Aug 10 23:03:18 sam-LIFEBOOK-S6410 AptDaemon: INFO: Shutdown was requested
Aug 10 23:17:02 sam-LIFEBOOK-S6410 CRON[3923]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 10 23:35:49 sam-LIFEBOOK-S6410 kernel: [10514.541287] show_signal_msg: 24 callbacks suppressed
Aug 10 23:35:49 sam-LIFEBOOK-S6410 kernel: [10514.541293] polkit-gnome-au[1924]: segfault at 24 ip 00861eb7 sp bfa2a350 error 4 in libglib-2.0.so.0.2800.6[83e000+d5000]
Aug 10 23:35:56 sam-LIFEBOOK-S6410 kernel: [10521.737804] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
Aug 10 23:35:59 sam-LIFEBOOK-S6410 kernel: Kernel logging (proc) stopped.
Aug 10 23:35:59 sam-LIFEBOOK-S6410 rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="762" x-info="http://www.rsyslog.com"] exiting on signal 15.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: imklog 4.6.4, log source = /proc/kmsg started.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="661" x-info="http://www.rsyslog.com"] (re)start
Aug 11 06:11:37 sam-LIFEBOOK-S6410 rsyslogd: rsyslogd's groupid changed to 103
Aug 11 06:11:37 sam-LIFEBOOK-S6410 rsyslogd: rsyslogd's userid changed to 101
Aug 11 06:11:37 sam-LIFEBOOK-S6410 rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 avahi-daemon[722]: Found user 'avahi' (UID 104) and group 'avahi' (GID 109).
Aug 11 06:11:37 sam-LIFEBOOK-S6410 avahi-daemon[722]: Successfully dropped root privileges.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 avahi-daemon[722]: avahi-daemon 0.6.30 starting up.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 avahi-daemon[722]: Successfully called chroot().
Aug 11 06:11:37 sam-LIFEBOOK-S6410 avahi-daemon[722]: Successfully dropped remaining capabilities.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 avahi-daemon[722]: Loading service file /services/udisks.service.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 gdm-binary[719]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Aug 11 06:11:37 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> NetworkManager (version 0.8.3.998) is starting...
Aug 11 06:11:37 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Aug 11 06:11:37 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Aug 11 06:11:37 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> trying to start the modem manager...
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] Linux version 2.6.38-10-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 (Ubuntu 2.6.38-10.46-generic 2.6.38.7)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007f6d0000 (usable)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]  BIOS-e820: 000000007f6d0000 - 000000007f6df000 (ACPI data)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]  BIOS-e820: 000000007f6df000 - 000000007f6e3000 (ACPI NVS)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]  BIOS-e820: 000000007f6e3000 - 0000000080000000 (reserved)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] DMI 2.4 present.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] DMI: FUJITSU SIEMENS LIFEBOOK S6410/FJNB1D3, BIOS Version 1.21  01/17/2008
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] last_pfn = 0x7f6d0 max_arch_pfn = 0x100000
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] MTRR default type: uncachable
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] MTRR fixed ranges enabled:
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]   00000-9FFFF write-back
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]   A0000-BFFFF uncachable
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]   C0000-D3FFF write-protect
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]   D4000-DFFFF uncachable
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]   E0000-FFFFF write-protect
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] MTRR variable ranges enabled:
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]   0 base 000000000 mask F80000000 write-back
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]   1 base 07F700000 mask FFFF00000 uncachable
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]   2 base 07F800000 mask FFF800000 uncachable
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]   3 disabled
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]   4 disabled
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]   5 disabled
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]   6 disabled
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]   7 disabled
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] initial memory mapped : 0 - 01c00000
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] RAMDISK: 35d30000 - 36e90000
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: RSDP 000f61f0 00024 (v02 FUJ   )
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: XSDT 7f6d4957 0007C (v01 FSC    PC       01210000 FUJ  00000100)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: SSDT 7f6dcde0 002D1 (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: FACP 7f6dd0b1 000F4 (v03 FSC    PC       01210000 FUJ  00000100)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: DSDT 7f6d49d3 0840D (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: FACS 7f6e2fc0 00040
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: HPET 7f6dd1a5 00038 (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: MCFG 7f6dd1dd 0003C (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: SSDT 7f6dd219 004EF (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: SSDT 7f6dd708 001CA (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: SSDT 7f6dd8d2 0106D (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: SSDT 7f6de93f 00447 (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: APIC 7f6ded86 00068 (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: BOOT 7f6dedee 00028 (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: SLIC 7f6dee16 00176 (v01 FSC    PC       01210000 FUJ  00000100)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] 1150MB HIGHMEM available.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] 887MB LOWMEM available.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]   low ram: 0 - 377fe000
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] Zone PFN ranges:
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]   HighMem  0x000377fe -> 0x0007f6d0
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] Movable zone start PFN for each node
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] early_node_map[2] active PFN ranges
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]     0: 0x00000010 -> 0x0000009e
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]     0: 0x00000100 -> 0x0007f6d0
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] On node 0 totalpages: 521822
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] free_area_init_node: node 0, pgdat c1784140, node_mem_map f4d40200
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]   DMA zone: 3950 pages, LIFO batch:0
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]   HighMem zone: 2302 pages used for memmap
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]   HighMem zone: 292308 pages, LIFO batch:31
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] Using APIC driver default
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] nr_irqs_gsi: 40
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e0000
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:78000000)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] PERCPU: Embedded 13 pages/cpu @f7000000 s28800 r0 d24448 u2097152
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] pcpu-alloc: s28800 r0 d24448 u2097152 alloc=1*4194304
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] pcpu-alloc: [0] 0 1
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517744
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic root=UUID=a0f75a36-c4e4-4260-ac89-a40fd602026b ro quiet splash vt.handoff=7
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] Initializing CPU#0
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] allocated 10438400 bytes of page_cgroup
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0007f6d0)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] Memory: 2032664k/2087744k available (5190k kernel code, 54624k reserved, 2539k data, 700k init, 1178440k highmem)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] virtual kernel memory layout:
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]       .data : 0xc1511841 - 0xc178c4c0   (2539 kB)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]       .text : 0xc1000000 - 0xc1511841   (5190 kB)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] Hierarchical RCU implementation.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000]     RCU-based detection of stalled CPUs is disabled.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] NR_IRQS:2304 nr_irqs:512 16
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] CPU 0 irqstacks, hard=f3c08000 soft=f3c0a000
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] Extended CMOS year: 2000
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] vt handoff: transparent VT on vt#7
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] Console: colour dummy device 80x25
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] console [tty0] enabled
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] hpet clockevent registered
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] Fast TSC calibration using PIT
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.000000] Detected 1995.258 MHz processor.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 3990.51 BogoMIPS (lpj=7981032)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.004012] pid_max: default: 32768 minimum: 301
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.004049] Security Framework initialized
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.004071] AppArmor: AppArmor initialized
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.004074] Yama: becoming mindful.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.004166] Mount-cache hash table entries: 512
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.004373] Initializing cgroup subsys ns
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.004379] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.004384] Initializing cgroup subsys cpuacct
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.004392] Initializing cgroup subsys memory
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.004406] Initializing cgroup subsys devices
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.004410] Initializing cgroup subsys freezer
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.004414] Initializing cgroup subsys net_cls
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.004418] Initializing cgroup subsys blkio
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.004475] CPU: Physical Processor ID: 0
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.004478] CPU: Processor Core ID: 0
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.004484] mce: CPU supports 6 MCE banks
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.004496] CPU0: Thermal monitoring enabled (TM2)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.004501] using mwait in idle threads.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.011445] ACPI: Core revision 20110112
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.024020] ftrace: allocating 23648 entries in 47 pages
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.028069] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.032204] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.071907] CPU0: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.072003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.072003] PEBS disabled due to CPU errata.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.072003] ... version:                2
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.072003] ... bit width:              40
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.072003] ... generic registers:      2
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.072003] ... value mask:             000000ffffffffff
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.072003] ... max period:             000000007fffffff
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.072003] ... fixed-purpose events:   3
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.072003] ... event mask:             0000000700000003
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.072003] CPU 1 irqstacks, hard=f3cca000 soft=f3ccc000
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.072003] Booting Node   0, Processors  #1 Ok.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.008000] Initializing CPU#1
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.160031] Brought up 2 CPUs
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.160036] Total of 2 processors activated (7980.53 BogoMIPS).
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.162087] devtmpfs: initialized
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.164698] print_constraints: dummy:
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.164739] Time:  5:11:21  Date: 08/11/11
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.164809] NET: Registered protocol family 16
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.164852] Trying to unpack rootfs image as initramfs...
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.165022] EISA bus registered
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.165035] ACPI: bus type pci registered
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.165164] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.165170] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.165173] PCI: Using MMCONFIG for extended config space
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.165176] PCI: Using configuration type 1 for base access
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.167119] bio: create slab <bio-0> at 0
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.170802] ACPI: EC: Look up EC in DSDT
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.177018] ACPI:      7f6e2a9f 003B7 (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.178183] ACPI: Dynamic OEM Table Load:
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.178190] ACPI:        (null) 003B7 (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.181710] ACPI: SSDT 7f6dfc19 0027A (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.182610] ACPI: Dynamic OEM Table Load:
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.182616] ACPI: SSDT   (null) 0027A (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.182915] ACPI: SSDT 7f6e0119 00627 (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.183779] ACPI: Dynamic OEM Table Load:
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.183786] ACPI: SSDT   (null) 00627 (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.208512] ACPI: SSDT 7f6e0061 000B8 (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.209401] ACPI: Dynamic OEM Table Load:
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.209407] ACPI: SSDT   (null) 000B8 (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.209624] ACPI: SSDT 7f6e0740 00047 (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.210490] ACPI: Dynamic OEM Table Load:
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.210496] ACPI: SSDT   (null) 00047 (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.211056] ACPI: Interpreter enabled
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.211068] ACPI: (supports S0 S3 S4 S5)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.211110] ACPI: Using IOAPIC for interrupt routing
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.261860] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.305673] ACPI: ACPI Dock Station Driver: 2 docks/bays found
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.305678] HEST: Table not found.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.305686] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.306312] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.307514] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.307520] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.307525] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.307531] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.307535] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.307540] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.307546] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xfebfffff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.307571] pci 0000:00:00.0: [8086:2a00] type 0 class 0x000600
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.307648] pci 0000:00:02.0: [8086:2a02] type 0 class 0x000300
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.307672] pci 0000:00:02.0: reg 10: [mem 0xfc000000-0xfc0fffff 64bit]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.307688] pci 0000:00:02.0: reg 18: [mem 0xe0000000-0xefffffff 64bit pref]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.307700] pci 0000:00:02.0: reg 20: [io  0x1800-0x1807]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.307757] pci 0000:00:02.1: [8086:2a03] type 0 class 0x000380
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.307778] pci 0000:00:02.1: reg 10: [mem 0xfc100000-0xfc1fffff 64bit]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.307905] pci 0000:00:1a.0: [8086:2834] type 0 class 0x000c03
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.307989] pci 0000:00:1a.0: reg 20: [io  0x1820-0x183f]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.308060] pci 0000:00:1a.1: [8086:2835] type 0 class 0x000c03
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.308128] pci 0000:00:1a.1: reg 20: [io  0x1840-0x185f]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.308201] pci 0000:00:1a.7: [8086:283a] type 0 class 0x000c03
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.308233] pci 0000:00:1a.7: reg 10: [mem 0xfc704800-0xfc704bff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.308348] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.308356] pci 0000:00:1a.7: PME# disabled
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.308394] pci 0000:00:1b.0: [8086:284b] type 0 class 0x000403
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.308422] pci 0000:00:1b.0: reg 10: [mem 0xfc700000-0xfc703fff 64bit]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.308521] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.308528] pci 0000:00:1b.0: PME# disabled
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.308564] pci 0000:00:1c.0: [8086:283f] type 1 class 0x000604
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.308666] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.308674] pci 0000:00:1c.0: PME# disabled
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.308713] pci 0000:00:1c.2: [8086:2843] type 1 class 0x000604
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.308814] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.308821] pci 0000:00:1c.2: PME# disabled
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.308866] pci 0000:00:1d.0: [8086:2830] type 0 class 0x000c03
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.308942] pci 0000:00:1d.0: reg 20: [io  0x1860-0x187f]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.309002] pci 0000:00:1d.1: [8086:2831] type 0 class 0x000c03
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.309071] pci 0000:00:1d.1: reg 20: [io  0x1880-0x189f]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.309122] pci 0000:00:1d.2: [8086:2832] type 0 class 0x000c03
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.309193] pci 0000:00:1d.2: reg 20: [io  0x18a0-0x18bf]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.309266] pci 0000:00:1d.7: [8086:2836] type 0 class 0x000c03
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.309299] pci 0000:00:1d.7: reg 10: [mem 0xfc704c00-0xfc704fff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.309415] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.309423] pci 0000:00:1d.7: PME# disabled
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.309454] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.309555] pci 0000:00:1f.0: [8086:2815] type 0 class 0x000601
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.309681] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.309690] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.309697] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at fd00 (mask 007f)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.309705] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 06e8 (mask 0007)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.309755] pci 0000:00:1f.1: [8086:2850] type 0 class 0x000101
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.309777] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.309794] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.309810] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.309825] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.309842] pci 0000:00:1f.1: reg 20: [io  0x1810-0x181f]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.309905] pci 0000:00:1f.2: [8086:2829] type 0 class 0x000106
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.309936] pci 0000:00:1f.2: reg 10: [io  0x1c00-0x1c07]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.309952] pci 0000:00:1f.2: reg 14: [io  0x18d4-0x18d7]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.309968] pci 0000:00:1f.2: reg 18: [io  0x18d8-0x18df]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.309984] pci 0000:00:1f.2: reg 1c: [io  0x18d0-0x18d3]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.310000] pci 0000:00:1f.2: reg 20: [io  0x18e0-0x18ff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.310016] pci 0000:00:1f.2: reg 24: [mem 0xfc704000-0xfc7047ff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.310072] pci 0000:00:1f.2: PME# supported from D3hot
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.310079] pci 0000:00:1f.2: PME# disabled
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.310107] pci 0000:00:1f.3: [8086:283e] type 0 class 0x000c05
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.310128] pci 0000:00:1f.3: reg 10: [mem 0x00000000-0x000000ff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.310178] pci 0000:00:1f.3: reg 20: [io  0x1c20-0x1c3f]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.310331] pci 0000:04:00.0: [11ab:4363] type 0 class 0x000200
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.310374] pci 0000:04:00.0: reg 10: [mem 0xfc200000-0xfc203fff 64bit]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.310398] pci 0000:04:00.0: reg 18: [io  0x2000-0x20ff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.310476] pci 0000:04:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.310550] pci 0000:04:00.0: supports D1 D2
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.310554] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.310563] pci 0000:04:00.0: PME# disabled
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.316049] pci 0000:00:1c.0: PCI bridge to [bus 04-07]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.316057] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.316066] pci 0000:00:1c.0:   bridge window [mem 0xfc200000-0xfc2fffff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.316077] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.316185] pci 0000:0c:00.0: [8086:4229] type 0 class 0x000280
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.316232] pci 0000:0c:00.0: reg 10: [mem 0xfc300000-0xfc301fff 64bit]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.316406] pci 0000:0c:00.0: PME# supported from D0 D3hot D3cold
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.316417] pci 0000:0c:00.0: PME# disabled
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324048] pci 0000:00:1c.2: PCI bridge to [bus 0c-0f]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324056] pci 0000:00:1c.2:   bridge window [io  0xf000-0x0000] (disabled)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324064] pci 0000:00:1c.2:   bridge window [mem 0xfc300000-0xfc3fffff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324075] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324142] pci 0000:1c:03.0: [1217:7136] type 2 class 0x000607
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324173] pci 0000:1c:03.0: reg 10: [mem 0x00000000-0x00000fff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324206] pci 0000:1c:03.0: supports D1 D2
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324210] pci 0000:1c:03.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324219] pci 0000:1c:03.0: PME# disabled
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324251] pci 0000:1c:03.2: [1217:7120] type 0 class 0x000805
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324281] pci 0000:1c:03.2: reg 10: [mem 0xfc402800-0xfc4028ff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324395] pci 0000:1c:03.2: supports D1 D2
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324399] pci 0000:1c:03.2: PME# supported from D0 D1 D2 D3hot D3cold
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324408] pci 0000:1c:03.2: PME# disabled
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324437] pci 0000:1c:03.3: [1217:7130] type 0 class 0x000180
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324466] pci 0000:1c:03.3: reg 10: [mem 0xfc400000-0xfc400fff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324578] pci 0000:1c:03.3: supports D1 D2
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324582] pci 0000:1c:03.3: PME# supported from D0 D1 D2 D3hot D3cold
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324590] pci 0000:1c:03.3: PME# disabled
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324621] pci 0000:1c:03.4: [1217:00f7] type 0 class 0x000c00
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324648] pci 0000:1c:03.4: reg 10: [mem 0xfc401000-0xfc401fff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324666] pci 0000:1c:03.4: reg 14: [mem 0xfc402000-0xfc4027ff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324760] pci 0000:1c:03.4: supports D1 D2
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324764] pci 0000:1c:03.4: PME# supported from D0 D1 D2 D3hot
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324772] pci 0000:1c:03.4: PME# disabled
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324848] pci 0000:00:1e.0: PCI bridge to [bus 1c-1d] (subtractive decode)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324856] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324865] pci 0000:00:1e.0:   bridge window [mem 0xfc400000-0xfc4fffff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324876] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324880] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324885] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324890] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324895] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324900] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324905] pci 0000:00:1e.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324910] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0xfebfffff] (subtractive decode)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.324973] pci_bus 0000:1d: [bus 1d-20] partially hidden behind transparent bridge 0000:1c [bus 1c-1d]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.325002] pci_bus 0000:00: on NUMA node 0
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.325011] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.325416] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.325537] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.325718] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.325802]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.336280] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.336385] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.336486] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.336585] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.336684] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.336783] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.336882] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.336980] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.337163] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.337195] vgaarb: loaded
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.337580] SCSI subsystem initialized
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.337670] libata version 3.00 loaded.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.337761] usbcore: registered new interface driver usbfs
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.337784] usbcore: registered new interface driver hub
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.337833] usbcore: registered new device driver usb
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.338044] wmi: Mapper loaded
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.338047] PCI: Using ACPI for IRQ routing
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.338052] PCI: pci_cache_line_size set to 64 bytes
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.338232] reserve RAM buffer: 000000000009e000 - 000000000009ffff
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.338237] reserve RAM buffer: 000000007f6d0000 - 000000007fffffff
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.338422] NetLabel: Initializing
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.338426] NetLabel:  domain hash size = 128
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.338429] NetLabel:  protocols = UNLABELED CIPSOv4
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.338448] NetLabel:  unlabeled traffic allowed by default
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.338520] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.338528] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.338538] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.344750] Switching to clocksource hpet
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.346449] Switched to NOHz mode on CPU #0
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.346601] Switched to NOHz mode on CPU #1
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.358383] AppArmor: AppArmor Filesystem Enabled
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.358426] pnp: PnP ACPI init
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.358456] ACPI: bus type pnp registered
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359094] pnp 00:00: [bus 00-ff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359100] pnp 00:00: [io  0x0000-0x0cf7 window]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359104] pnp 00:00: [io  0x0cf8-0x0cff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359109] pnp 00:00: [io  0x0d00-0xffff window]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359113] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359118] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359123] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359127] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359132] pnp 00:00: [mem 0x000cc000-0x000cffff window]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359136] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359141] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359145] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359150] pnp 00:00: [mem 0x000dc000-0x000dffff window]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359155] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359159] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359164] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359168] pnp 00:00: [mem 0x000ec000-0x000effff window]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359173] pnp 00:00: [mem 0x000f0000-0x000fffff window]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359178] pnp 00:00: [mem 0x80000000-0xfebfffff window]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359182] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359331] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359435] pnp 00:01: [io  0x0010-0x001f]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359439] pnp 00:01: [io  0x0024-0x0025]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359443] pnp 00:01: [io  0x0028-0x0029]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359447] pnp 00:01: [io  0x002c-0x002d]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359451] pnp 00:01: [io  0x002e-0x002f]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359454] pnp 00:01: [io  0x0030-0x0031]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359458] pnp 00:01: [io  0x0034-0x0035]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359462] pnp 00:01: [io  0x0038-0x0039]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359466] pnp 00:01: [io  0x003c-0x003d]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359473] pnp 00:01: [io  0x004e-0x004f]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359477] pnp 00:01: [io  0x0050-0x0053]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359480] pnp 00:01: [io  0x0061]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359484] pnp 00:01: [io  0x0063]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359488] pnp 00:01: [io  0x0065]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359491] pnp 00:01: [io  0x0067]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359495] pnp 00:01: [io  0x0072-0x0077]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359498] pnp 00:01: [io  0x0080]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359502] pnp 00:01: [io  0x0090-0x009f]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359506] pnp 00:01: [io  0x0092]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359509] pnp 00:01: [io  0x00a4-0x00a5]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359513] pnp 00:01: [io  0x00a8-0x00a9]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359517] pnp 00:01: [io  0x00ac-0x00ad]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359521] pnp 00:01: [io  0x00b0-0x00b1]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359524] pnp 00:01: [io  0x00b2-0x00b3]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359528] pnp 00:01: [io  0x00b4-0x00b5]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359532] pnp 00:01: [io  0x00b8-0x00b9]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359535] pnp 00:01: [io  0x00bc-0x00bd]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359539] pnp 00:01: [io  0x04d0-0x04d1]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359543] pnp 00:01: [io  0x0680-0x069f]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359546] pnp 00:01: [io  0x0800-0x080f]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359550] pnp 00:01: [io  0x1000-0x107f]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359554] pnp 00:01: [io  0x1080-0x10ff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359558] pnp 00:01: [io  0x1100-0x111f]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359561] pnp 00:01: [io  0x1180-0x11bf]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359565] pnp 00:01: [io  0x1640-0x164f]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359568] pnp 00:01: [io  0xf800-0xf87f]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359572] pnp 00:01: [io  0xf880-0xf8ff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359576] pnp 00:01: [io  0xfc00-0xfc7f]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359579] pnp 00:01: [io  0xfc80-0xfcff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359583] pnp 00:01: [io  0xfd00-0xfd7f]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359587] pnp 00:01: [io  0xfe00-0xfe03]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359798] system 00:01: [io  0x04d0-0x04d1] has been reserved
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359804] system 00:01: [io  0x0680-0x069f] has been reserved
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359809] system 00:01: [io  0x0800-0x080f] has been reserved
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359815] system 00:01: [io  0x1000-0x107f] has been reserved
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359820] system 00:01: [io  0x1080-0x10ff] has been reserved
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359825] system 00:01: [io  0x1100-0x111f] has been reserved
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359831] system 00:01: [io  0x1180-0x11bf] has been reserved
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359836] system 00:01: [io  0x1640-0x164f] has been reserved
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359842] system 00:01: [io  0xf800-0xf87f] has been reserved
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359847] system 00:01: [io  0xf880-0xf8ff] has been reserved
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359852] system 00:01: [io  0xfc00-0xfc7f] has been reserved
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359857] system 00:01: [io  0xfc80-0xfcff] has been reserved
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359863] system 00:01: [io  0xfd00-0xfd7f] has been reserved
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359868] system 00:01: [io  0xfe00-0xfe03] has been reserved
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.359875] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.360064] pnp 00:02: [mem 0xfed1c000-0xfed1ffff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.360069] pnp 00:02: [mem 0xfed14000-0xfed17fff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.360073] pnp 00:02: [mem 0xfed18000-0xfed18fff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.360077] pnp 00:02: [mem 0xfed19000-0xfed19fff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.360081] pnp 00:02: [mem 0xf8000000-0xfbffffff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.360086] pnp 00:02: [mem 0xfed20000-0xfed3ffff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.360090] pnp 00:02: [mem 0xfed40000-0xfed44fff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.360094] pnp 00:02: [mem 0xfed45000-0xfed8ffff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.360098] pnp 00:02: [mem 0xfef00000-0xfeffffff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.360200] system 00:02: [mem 0xfed1c000-0xfed1ffff] has been reserved
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.360206] system 00:02: [mem 0xfed14000-0xfed17fff] has been reserved
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.360211] system 00:02: [mem 0xfed18000-0xfed18fff] has been reserved
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.360217] system 00:02: [mem 0xfed19000-0xfed19fff] has been reserved
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.360222] system 00:02: [mem 0xf8000000-0xfbffffff] has been reserved
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.360227] system 00:02: [mem 0xfed20000-0xfed3ffff] has been reserved
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.360233] system 00:02: [mem 0xfed40000-0xfed44fff] has been reserved
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.360238] system 00:02: [mem 0xfed45000-0xfed8ffff] has been reserved
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.360244] system 00:02: [mem 0xfef00000-0xfeffffff] has been reserved
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.360250] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.360750] pnp 00:03: [io  0x0000-0x000f]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.360754] pnp 00:03: [io  0x0081-0x008f]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.360758] pnp 00:03: [io  0x00c0-0x00df]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.360763] pnp 00:03: [dma 4]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.360864] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.360895] pnp 00:04: [io  0x0060]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.360899] pnp 00:04: [io  0x0064]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.360916] pnp 00:04: [irq 1]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.361012] pnp 00:04: Plug and Play ACPI device, IDs PNP0303 (active)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.361043] pnp 00:05: [io  0x00f0-0x00fe]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.361053] pnp 00:05: [irq 13]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.361154] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.361202] pnp 00:06: [irq 12]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.361300] pnp 00:06: Plug and Play ACPI device, IDs PNP0f13 (active)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.361331] pnp 00:07: [io  0x0070-0x0071]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.361339] pnp 00:07: [irq 8]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.361441] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.361471] pnp 00:08: [io  0x0061]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.361571] pnp 00:08: Plug and Play ACPI device, IDs PNP0800 (active)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.361980] pnp 00:09: [io  0x03f8-0x03ff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.361991] pnp 00:09: [irq 4]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.362134] pnp 00:09: Plug and Play ACPI device, IDs PNP0501 (active)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.362803] pnp 00:0a: [io  0x02e8-0x02ef]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.362808] pnp 00:0a: [io  0x06e8-0x06ef]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.362817] pnp 00:0a: [irq 3]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.362821] pnp 00:0a: [dma 3]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.362974] pnp 00:0a: Plug and Play ACPI device, IDs SMCf010 (active)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.363507] pnp 00:0b: [io  0x0378-0x037f]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.363512] pnp 00:0b: [io  0x0778-0x077b]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.363521] pnp 00:0b: [irq 7]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.363689] pnp 00:0b: Plug and Play ACPI device, IDs PNP0400 (active)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.364191] pnp: PnP ACPI: found 12 devices
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.364195] ACPI: ACPI bus type pnp unregistered
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.364202] PnPBIOS: Disabled by ACPI PNP
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402308] pci 0000:00:1e.0: BAR 15: assigned [mem 0x80000000-0x83ffffff pref]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402318] pci 0000:00:1c.0: BAR 15: assigned [mem 0x84000000-0x841fffff pref]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402326] pci 0000:00:1c.2: BAR 15: assigned [mem 0x84200000-0x843fffff 64bit pref]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402334] pci 0000:00:1c.2: BAR 13: assigned [io  0x3000-0x3fff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402340] pci 0000:00:1e.0: BAR 13: assigned [io  0x4000-0x4fff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402347] pci 0000:00:1f.3: BAR 0: assigned [mem 0x84400000-0x844000ff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402356] pci 0000:00:1f.3: BAR 0: set to [mem 0x84400000-0x844000ff] (PCI address [0x84400000-0x844000ff])
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402363] pci 0000:04:00.0: BAR 6: assigned [mem 0x84000000-0x8401ffff pref]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402368] pci 0000:00:1c.0: PCI bridge to [bus 04-07]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402375] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402384] pci 0000:00:1c.0:   bridge window [mem 0xfc200000-0xfc2fffff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402392] pci 0000:00:1c.0:   bridge window [mem 0x84000000-0x841fffff pref]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402403] pci 0000:00:1c.2: PCI bridge to [bus 0c-0f]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402408] pci 0000:00:1c.2:   bridge window [io  0x3000-0x3fff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402418] pci 0000:00:1c.2:   bridge window [mem 0xfc300000-0xfc3fffff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402426] pci 0000:00:1c.2:   bridge window [mem 0x84200000-0x843fffff 64bit pref]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402439] pci 0000:1c:03.0: BAR 15: assigned [mem 0x80000000-0x83ffffff pref]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402448] pci 0000:1c:03.0: BAR 16: assigned [mem 0x88000000-0x8bffffff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402453] pci 0000:1c:03.0: BAR 0: assigned [mem 0xfc403000-0xfc403fff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402463] pci 0000:1c:03.0: BAR 0: set to [mem 0xfc403000-0xfc403fff] (PCI address [0xfc403000-0xfc403fff])
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402469] pci 0000:1c:03.0: BAR 13: assigned [io  0x4000-0x40ff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402473] pci 0000:1c:03.0: BAR 14: assigned [io  0x4400-0x44ff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402478] pci 0000:1c:03.0: CardBus bridge to [bus 1d-20]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402482] pci 0000:1c:03.0:   bridge window [io  0x4000-0x40ff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402491] pci 0000:1c:03.0:   bridge window [io  0x4400-0x44ff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402499] pci 0000:1c:03.0:   bridge window [mem 0x80000000-0x83ffffff pref]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402507] pci 0000:1c:03.0:   bridge window [mem 0x88000000-0x8bffffff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402515] pci 0000:00:1e.0: PCI bridge to [bus 1c-1d]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402521] pci 0000:00:1e.0:   bridge window [io  0x4000-0x4fff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402530] pci 0000:00:1e.0:   bridge window [mem 0xfc400000-0xfc4fffff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402538] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0x83ffffff pref]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402574] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402583] pci 0000:00:1c.0: setting latency timer to 64
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402601] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402608] pci 0000:00:1c.2: setting latency timer to 64
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402621] pci 0000:00:1e.0: setting latency timer to 64
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402633] pci 0000:1c:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402644] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402648] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402653] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402658] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402662] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402667] pci_bus 0000:00: resource 9 [mem 0x000dc000-0x000dffff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402671] pci_bus 0000:00: resource 10 [mem 0x80000000-0xfebfffff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402676] pci_bus 0000:04: resource 0 [io  0x2000-0x2fff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402681] pci_bus 0000:04: resource 1 [mem 0xfc200000-0xfc2fffff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402685] pci_bus 0000:04: resource 2 [mem 0x84000000-0x841fffff pref]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402690] pci_bus 0000:0c: resource 0 [io  0x3000-0x3fff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402695] pci_bus 0000:0c: resource 1 [mem 0xfc300000-0xfc3fffff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 modem-manager[730]: <info>  ModemManager (version 0.4) starting...
Aug 11 06:11:37 sam-LIFEBOOK-S6410 avahi-daemon[722]: Network interface enumeration completed.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 avahi-daemon[722]: Registering HINFO record with values 'I686'/'LINUX'.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 avahi-daemon[722]: Server startup complete. Host name is sam-LIFEBOOK-S6410.local. Local service cookie is 664792309.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 avahi-daemon[722]: Service "sam-LIFEBOOK-S6410" (/services/udisks.service) successfully established.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402700] pci_bus 0000:0c: resource 2 [mem 0x84200000-0x843fffff 64bit pref]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402704] pci_bus 0000:1c: resource 0 [io  0x4000-0x4fff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402709] pci_bus 0000:1c: resource 1 [mem 0xfc400000-0xfc4fffff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402714] pci_bus 0000:1c: resource 2 [mem 0x80000000-0x83ffffff pref]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402719] pci_bus 0000:1c: resource 4 [io  0x0000-0x0cf7]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402723] pci_bus 0000:1c: resource 5 [io  0x0d00-0xffff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402728] pci_bus 0000:1c: resource 6 [mem 0x000a0000-0x000bffff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402732] pci_bus 0000:1c: resource 7 [mem 0x000d4000-0x000d7fff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402737] pci_bus 0000:1c: resource 8 [mem 0x000d8000-0x000dbfff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402741] pci_bus 0000:1c: resource 9 [mem 0x000dc000-0x000dffff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402746] pci_bus 0000:1c: resource 10 [mem 0x80000000-0xfebfffff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402751] pci_bus 0000:1d: resource 0 [io  0x4000-0x40ff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402755] pci_bus 0000:1d: resource 1 [io  0x4400-0x44ff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402760] pci_bus 0000:1d: resource 2 [mem 0x80000000-0x83ffffff pref]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402764] pci_bus 0000:1d: resource 3 [mem 0x88000000-0x8bffffff]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402827] NET: Registered protocol family 2
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.402950] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.403357] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.403942] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.404247] TCP: Hash tables configured (established 131072 bind 65536)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.404251] TCP reno registered
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.404257] UDP hash table entries: 512 (order: 2, 16384 bytes)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.404269] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.404392] NET: Registered protocol family 1
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.404417] pci 0000:00:02.0: Boot video device
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.404651] PCI: CLS 64 bytes, default 64
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.404687] Simple Boot Flag at 0x7b set to 0x1
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.405020] cpufreq-nforce2: No nForce2 chipset.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.405244] audit: initializing netlink socket (disabled)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.405258] type=2000 audit(1313039481.400:1): initialized
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.422296] highmem bounce pool size: 64 pages
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.422305] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.425779] VFS: Disk quotas dquot_6.5.2
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.425891] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.427124] fuse init (API version 7.16)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.427299] msgmni has been set to 1668
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.427703] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.427753] io scheduler noop registered
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.427757] io scheduler deadline registered
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.427784] io scheduler cfq registered (default)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.428025] pcieport 0000:00:1c.0: setting latency timer to 64
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.428109] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.428233] pcieport 0000:00:1c.2: setting latency timer to 64
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.428309] pcieport 0000:00:1c.2: irq 41 for MSI/MSI-X
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.428476] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.428520] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.428690] intel_idle: MWAIT substates: 0x22220
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.428694] intel_idle: does not run on family 6 model 15
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.428845] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.428958] ACPI: AC Adapter [AC] (off-line)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.429103] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.488028] ACPI: Lid Switch [LID]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.488152] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.488161] ACPI: Power Button [PWRB]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.488250] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.488257] ACPI: Sleep Button [SLPB]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.488340] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.488346] ACPI: Power Button [PWRF]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.488728] ACPI: acpi_idle registered with cpuidle
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.489058] Monitor-Mwait will be used to enter C-1 state
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.489113] Monitor-Mwait will be used to enter C-2 state
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.489157] Monitor-Mwait will be used to enter C-3 state
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.489167] Marking TSC unstable due to TSC halts in idle
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.504781] thermal LNXTHERM:00: registered as thermal_zone0
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.504787] ACPI: Thermal Zone [TZ00] (27 C)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.505063] thermal LNXTHERM:01: registered as thermal_zone1
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.505068] ACPI: Thermal Zone [TZ01] (27 C)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.505173] ERST: Table is not found!
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.505299] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.526043] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.526270] isapnp: Scanning for PnP cards...
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.539874] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.539890] ACPI: Battery Slot [CMB1] (battery present)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.539936] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.539948] ACPI: Battery Slot [CMB2] (battery absent)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.881000] isapnp: No Plug & Play device found
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.885813] Freeing initrd memory: 17792k freed
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.936634] serial8250: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.960379] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.960827] Linux agpgart interface v0.103
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.961039] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.961183] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.963073] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.963239] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.965708] brd: module loaded
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.966863] loop: module loaded
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.967020] i2c-core: driver [adp5520] using legacy suspend method
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.967024] i2c-core: driver [adp5520] using legacy resume method
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.967195] ata_piix 0000:00:1f.1: version 2.13
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.967227] ata_piix 0000:00:1f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.967280] ata_piix 0000:00:1f.1: setting latency timer to 64
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.967906] scsi0 : ata_piix
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.968089] scsi1 : ata_piix
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.968870] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.968876] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.969594] Fixed MDIO Bus: probed
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.969668] PPP generic driver version 2.4.2
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.969744] tun: Universal TUN/TAP device driver, 1.6
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.969748] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.969906] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.969941] ehci_hcd 0000:00:1a.7: PCI INT B -> GSI 23 (level, low) -> IRQ 23
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.969963] ehci_hcd 0000:00:1a.7: setting latency timer to 64
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.969969] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.970037] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.970121] ehci_hcd 0000:00:1a.7: debug port 1
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.974010] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.974036] ehci_hcd 0000:00:1a.7: irq 23, io mem 0xfc704800
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.988025] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.988253] hub 1-0:1.0: USB hub found
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.988262] hub 1-0:1.0: 4 ports detected
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.988402] ehci_hcd 0000:00:1d.7: PCI INT B -> GSI 23 (level, low) -> IRQ 23
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.988420] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.988426] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.988502] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.988578] ehci_hcd 0000:00:1d.7: debug port 1
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.992476] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    0.992486] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfc704c00
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.008025] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.008249] hub 2-0:1.0: USB hub found
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.008257] hub 2-0:1.0: 6 ports detected
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.008409] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.008436] uhci_hcd: USB Universal Host Controller Interface driver
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.008482] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.008492] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.008499] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.008567] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.008647] uhci_hcd 0000:00:1a.0: irq 22, io base 0x00001820
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.008872] hub 3-0:1.0: USB hub found
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.008880] hub 3-0:1.0: 2 ports detected
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.009010] uhci_hcd 0000:00:1a.1: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.009021] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.009027] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.009096] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.009160] uhci_hcd 0000:00:1a.1: irq 22, io base 0x00001840
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.009387] hub 4-0:1.0: USB hub found
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.009394] hub 4-0:1.0: 2 ports detected
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.009531] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.009541] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.009547] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.009619] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.012068] uhci_hcd 0000:00:1d.0: irq 22, io base 0x00001860
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.012297] hub 5-0:1.0: USB hub found
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.012304] hub 5-0:1.0: 2 ports detected
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.012438] uhci_hcd 0000:00:1d.1: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.012448] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.012454] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.012531] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.012594] uhci_hcd 0000:00:1d.1: irq 22, io base 0x00001880
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.012826] hub 6-0:1.0: USB hub found
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.012833] hub 6-0:1.0: 2 ports detected
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.012967] uhci_hcd 0000:00:1d.2: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.012979] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.012986] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.013053] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.013116] uhci_hcd 0000:00:1d.2: irq 22, io base 0x000018a0
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.013336] hub 7-0:1.0: USB hub found
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.013344] hub 7-0:1.0: 2 ports detected
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.013590] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.015743] i8042: Detected active multiplexing controller, rev 1.1
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.017148] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.017158] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.017214] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.017268] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.017318] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.017537] mousedev: PS/2 mouse device common for all mice
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.017874] rtc_cmos 00:07: RTC can wake from S4
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.017975] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.018015] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.018155] device-mapper: uevent: version 1.0.3
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.018300] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.018399] device-mapper: multipath: version 1.2.0 loaded
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.018403] device-mapper: multipath round-robin: version 1.0.0 loaded
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.018530] EISA: Probing bus 0 at eisa.0
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.018534] EISA: Cannot allocate resource for mainboard
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.018539] Cannot allocate resource for EISA slot 1
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.018542] Cannot allocate resource for EISA slot 2
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.018546] Cannot allocate resource for EISA slot 3
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.018549] Cannot allocate resource for EISA slot 4
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.018552] Cannot allocate resource for EISA slot 5
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.018556] Cannot allocate resource for EISA slot 6
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.018559] Cannot allocate resource for EISA slot 7
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.018562] Cannot allocate resource for EISA slot 8
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.018566] EISA: Detected 0 cards.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.018775] cpuidle: using governor ladder
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.018968] cpuidle: using governor menu
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.019509] TCP cubic registered
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.019750] NET: Registered protocol family 10
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.020856] NET: Registered protocol family 17
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.020886] Registering the dns_resolver key type
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.021764] Using IPI No-Shortcut mode
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.021913] PM: Hibernation image not present or could not be loaded.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.021924] registered taskstats version 1
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.022278]   Magic number: 7:980:162
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.022315] acpi device:29: hash matches
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.022384] rtc_cmos 00:07: setting system clock to 2011-08-11 05:11:22 UTC (1313039482)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.022387] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.022389] EDD information not available.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.047894] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.136450] ata1.00: ATAPI: Optiarc  DVD RW AD-7910A, 1.50, max UDMA/33
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.152357] ata1.00: configured for UDMA/33
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.155016] scsi 0:0:0:0: CD-ROM            Optiarc  DVD RW AD-7910A  1.50 PQ: 0 ANSI: 5
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.160817] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.160820] cdrom: Uniform CD-ROM driver Revision: 3.20
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.160932] sr 0:0:0:0: Attached scsi CD-ROM sr0
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.160998] sr 0:0:0:0: Attached scsi generic sg0 type 5
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.161153] Freeing unused kernel memory: 700k freed
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.161432] Write protecting the kernel text: 5192k
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.161501] Write protecting the kernel read-only data: 2148k
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.185802] <30>udev[76]: starting version 167
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.279613] sdhci: Secure Digital Host Controller Interface driver
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.279616] sdhci: Copyright(c) Pierre Ossman
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.297437] sdhci-pci 0000:1c:03.2: SDHCI controller found [1217:7120] (rev 2)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.297457] sdhci-pci 0000:1c:03.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.297508] mmc0: no vmmc regulator found
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.297554] Registered led device: mmc0::
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.312132] mmc0: SDHCI controller on PCI [0000:1c:03.2] using PIO
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.329854] ahci 0000:00:1f.2: version 3.0
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.329871] ahci 0000:00:1f.2: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.329933] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.330006] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.330010] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.330016] ahci 0000:00:1f.2: setting latency timer to 64
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.337777] firewire_ohci 0000:1c:03.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.354107] scsi2 : ahci
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.354114] [drm] Initialized drm 1.1.0 20060810
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.354403] scsi3 : ahci
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.356119] scsi4 : ahci
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.356267] ata3: SATA max UDMA/133 abar m2048@0xfc704000 port 0xfc704100 irq 42
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.356271] ata4: SATA max UDMA/133 abar m2048@0xfc704000 port 0xfc704180 irq 42
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.356275] ata5: SATA max UDMA/133 abar m2048@0xfc704000 port 0xfc704200 irq 42
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.361104] sky2: driver version 1.28
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.361133] sky2 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.361147] sky2 0000:04:00.0: setting latency timer to 64
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.361178] sky2 0000:04:00.0: Yukon-2 EC Ultra chip revision 3
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.361331] sky2 0000:04:00.0: irq 43 for MSI/MSI-X
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.362077] sky2 0000:04:00.0: eth0: addr 00:17:42:74:cd:23
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.392180] firewire_ohci: Added fw-ohci device 0000:1c:03.4, OHCI v1.10, 8 IR + 8 IT contexts, quirks 0x0
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.412079] usb 1-3: new high speed USB device using ehci_hcd and address 3
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.676087] ata4: SATA link down (SStatus 0 SControl 300)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.676116] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.676950] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.676954] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.680070] ata5: SATA link down (SStatus 0 SControl 300)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.726374] ata3.00: ATA-8: ST9320325AS, 0001SDM1, max UDMA/133
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.726378] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.728173] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.728177] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.728538] ata3.00: configured for UDMA/133
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.728712] scsi 2:0:0:0: Direct-Access     ATA      ST9320325AS      0001 PQ: 0 ANSI: 5
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.728873] sd 2:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.728908] sd 2:0:0:0: Attached scsi generic sg1 type 0
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.728928] sd 2:0:0:0: [sda] Write Protect is off
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.728931] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.728956] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.770981]  sda: sda1 sda2 < sda5 >
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.771297] sd 2:0:0:0: [sda] Attached SCSI disk
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.793449] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.793456] i915 0000:00:02.0: setting latency timer to 64
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.810827] i915 0000:00:02.0: irq 44 for MSI/MSI-X
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.810834] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.810836] [drm] Driver supports precise vblank timestamp query.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.812056] usb 3-2: new full speed USB device using uhci_hcd and address 2
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.893037] firewire_core: created device fw0: GUID 00000e1003d43d25, S400
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.966985] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    1.967317] [drm] initialized overlay support
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    2.376087] usb 5-2: new full speed USB device using uhci_hcd and address 2
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    2.624503] fbcon: inteldrmfb (fb0) is primary device
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    2.624565] Console: switching to colour frame buffer device 160x50
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    2.624595] fb0: inteldrmfb frame buffer device
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    2.624597] drm: registered panic notifier
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    2.656572] acpi device:04: registered as cooling_device2
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    2.656827] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    2.656922] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    2.657131] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    3.274911] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [    4.656081] usb 7-1: new full speed USB device using uhci_hcd and address 2
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [   15.768180] <30>udev[349]: starting version 167
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [   15.791578] lp: driver loaded but no devices found
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [   15.866265] fujitsu-laptop: Identified laptop model 'Fujitsu Siemens S6410'.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [   15.866424] input: Fujitsu FUJ02B1 as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:38/FUJ02B1:00/input/input6
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [   15.866537] ACPI: Fujitsu FUJ02B1 [FJEX] (on)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [   15.869154] input: Fujitsu FUJ02E3 as /devices/LNXSYSTM:00/device:00/FUJ02E3:00/input/input7
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [   15.869538] ACPI: Fujitsu FUJ02E3 [FEXT] (on)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [   15.869941] fujitsu-laptop: BTNI: [0xff0101]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [   15.880847] EXT4-fs (sda1): warning: maximal mount count reached, running e2fsck is recommended
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [   15.889268] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [   15.920024] fujitsu-laptop: driver 0.6.0 successfully loaded.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [   16.020995] type=1400 audit(1313039497.494:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=600 comm="apparmor_parser"
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [   16.021958] type=1400 audit(1313039497.494:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=600 comm="apparmor_parser"
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [   16.022565] type=1400 audit(1313039497.494:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=600 comm="apparmor_parser"
Aug 11 06:11:37 sam-LIFEBOOK-S6410 polkitd[736]: started daemon version 0.101 using authority implementation `local' version `0.101'
Aug 11 06:11:37 sam-LIFEBOOK-S6410 modem-manager[730]: <info>  Loaded plugin Sierra
Aug 11 06:11:37 sam-LIFEBOOK-S6410 modem-manager[730]: <info>  Loaded plugin Gobi
Aug 11 06:11:37 sam-LIFEBOOK-S6410 modem-manager[730]: <info>  Loaded plugin Option High-Speed
Aug 11 06:11:37 sam-LIFEBOOK-S6410 modem-manager[730]: <info>  Loaded plugin X22X
Aug 11 06:11:37 sam-LIFEBOOK-S6410 modem-manager[730]: <info>  Loaded plugin Nokia
Aug 11 06:11:37 sam-LIFEBOOK-S6410 modem-manager[730]: <info>  Loaded plugin AnyData
Aug 11 06:11:37 sam-LIFEBOOK-S6410 modem-manager[730]: <info>  Loaded plugin SimTech
Aug 11 06:11:37 sam-LIFEBOOK-S6410 modem-manager[730]: <info>  Loaded plugin Linktop
Aug 11 06:11:37 sam-LIFEBOOK-S6410 modem-manager[730]: <info>  Loaded plugin Longcheer
Aug 11 06:11:37 sam-LIFEBOOK-S6410 modem-manager[730]: <info>  Loaded plugin Huawei
Aug 11 06:11:37 sam-LIFEBOOK-S6410 modem-manager[730]: <info>  Loaded plugin MotoC
Aug 11 06:11:37 sam-LIFEBOOK-S6410 modem-manager[730]: <info>  Loaded plugin Generic
Aug 11 06:11:37 sam-LIFEBOOK-S6410 modem-manager[730]: <info>  Loaded plugin Novatel
Aug 11 06:11:37 sam-LIFEBOOK-S6410 modem-manager[730]: <info>  Loaded plugin Ericsson MBM
Aug 11 06:11:37 sam-LIFEBOOK-S6410 modem-manager[730]: <info>  Loaded plugin Option
Aug 11 06:11:37 sam-LIFEBOOK-S6410 modem-manager[730]: <info>  Loaded plugin ZTE
Aug 11 06:11:37 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> monitoring kernel firmware directory '/lib/firmware'.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 NetworkManager[726]:    SCPlugin-Ifupdown: init!
Aug 11 06:11:37 sam-LIFEBOOK-S6410 NetworkManager[726]:    SCPlugin-Ifupdown: update_system_hostname
Aug 11 06:11:37 sam-LIFEBOOK-S6410 NetworkManager[726]:    SCPluginIfupdown: management mode: unmanaged
Aug 11 06:11:37 sam-LIFEBOOK-S6410 NetworkManager[726]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:04:00.0/net/eth0, iface: eth0)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 NetworkManager[726]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:04:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 NetworkManager[726]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 NetworkManager[726]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 NetworkManager[726]:    SCPlugin-Ifupdown: end _init.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 NetworkManager[726]:    Ifupdown: get unmanaged devices count: 0
Aug 11 06:11:37 sam-LIFEBOOK-S6410 NetworkManager[726]:    SCPlugin-Ifupdown: (151686688) ... get_connections.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 NetworkManager[726]:    SCPlugin-Ifupdown: (151686688) ... get_connections (managed=false): return empty list.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 NetworkManager[726]:    Ifupdown: get unmanaged devices count: 0
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [   16.391878] type=1400 audit(1313039497.862:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=879 comm="apparmor_parser"
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [   16.394468] type=1400 audit(1313039497.866:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=880 comm="apparmor_parser"
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [   16.396827] type=1400 audit(1313039497.870:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=880 comm="apparmor_parser"
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [   16.397436] type=1400 audit(1313039497.870:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=880 comm="apparmor_parser"
Aug 11 06:11:37 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> WiFi enabled by radio killswitch; enabled by state file
Aug 11 06:11:37 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> WWAN enabled by radio killswitch; enabled by state file
Aug 11 06:11:37 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> WiMAX enabled by radio killswitch; enabled by state file
Aug 11 06:11:37 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Networking is enabled by state file
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [   16.408240] type=1400 audit(1313039497.882:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=882 comm="apparmor_parser"
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [   16.415022] type=1400 audit(1313039497.886:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/freshclam" pid=888 comm="apparmor_parser"
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [   16.438851] type=1400 audit(1313039497.910:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=882 comm="apparmor_parser"
Aug 11 06:11:37 sam-LIFEBOOK-S6410 gdm-binary[719]: WARNING: Unable to find users: no seat-id found
Aug 11 06:11:37 sam-LIFEBOOK-S6410 gdm-simple-slave[892]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Aug 11 06:11:37 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (eth0): carrier is OFF
Aug 11 06:11:37 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (eth0): new Ethernet device (driver: 'sky2' ifindex: 2)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Aug 11 06:11:37 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (eth0): now managed
Aug 11 06:11:37 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Aug 11 06:11:37 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (eth0): bringing up device.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (eth0): preparing device.
Aug 11 06:11:37 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (eth0): deactivating device (reason: 2).
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [   16.498169] sky2 0000:04:00.0: eth0: enabling interface
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [   16.498532] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 11 06:11:37 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.0/0000:04:00.0/net/eth0
Aug 11 06:11:37 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> modem-manager is now available
Aug 11 06:11:37 sam-LIFEBOOK-S6410 NetworkManager[726]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Aug 11 06:11:37 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Trying to start the supplicant...
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [   16.507770] yenta_cardbus 0000:1c:03.0: CardBus bridge found [10cf:143d]
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [   16.507797] yenta_cardbus 0000:1c:03.0: O2: enabling read prefetch/write burst. If you experience problems or performance issues, use the yenta_socket parameter 'o2_speedup=off'
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [   16.509729] parport_pc 00:0b: reported by Plug and Play ACPI
Aug 11 06:11:37 sam-LIFEBOOK-S6410 kernel: [   16.509774] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.562571] cfg80211: Calling CRDA to update world regulatory domain
Aug 11 06:11:38 sam-LIFEBOOK-S6410 init: apport pre-start process (963) terminated with status 1
Aug 11 06:11:38 sam-LIFEBOOK-S6410 init: alsa-restore main process (978) terminated with status 19
Aug 11 06:11:38 sam-LIFEBOOK-S6410 anacron[1008]: Anacron 2.3 started on 2011-08-11
Aug 11 06:11:38 sam-LIFEBOOK-S6410 acpid: starting up with proc fs
Aug 11 06:11:38 sam-LIFEBOOK-S6410 acpid: 32 rules loaded
Aug 11 06:11:38 sam-LIFEBOOK-S6410 acpid: waiting for events: event logging is off
Aug 11 06:11:38 sam-LIFEBOOK-S6410 cron[979]: (CRON) INFO (pidfile fd = 3)
Aug 11 06:11:38 sam-LIFEBOOK-S6410 init: apport post-stop process (1022) terminated with status 1
Aug 11 06:11:38 sam-LIFEBOOK-S6410 cron[1029]: (CRON) STARTUP (fork ok)
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.633302] yenta_cardbus 0000:1c:03.0: ISA IRQ mask 0x0c38, PCI irq 16
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.633307] yenta_cardbus 0000:1c:03.0: Socket status: 30000006
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.633312] pci_bus 0000:1c: Raising subordinate bus# of parent bus (#1c) from #1d to #20
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.633321] yenta_cardbus 0000:1c:03.0: pcmcia: parent PCI bridge window: [io  0x4000-0x4fff]
Aug 11 06:11:38 sam-LIFEBOOK-S6410 cron[1029]: (CRON) INFO (Running @reboot jobs)
Aug 11 06:11:38 sam-LIFEBOOK-S6410 anacron[1008]: Will run job `cron.daily' in 5 min.
Aug 11 06:11:38 sam-LIFEBOOK-S6410 anacron[1008]: Jobs will be executed sequentially
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.633325] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x4000-0x4fff: excluding 0x4000-0x40ff 0x4400-0x44ff
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.706672] irda_init()
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.706685] NET: Registered protocol family 23
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.720380] found SMC SuperIO Chip (devid=0x7a rev=03 base=0x002e): LPC47N227
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.720405] smsc_superio_flat(): fir: 0x6e8, sir: 0x2e8, dma: 03, irq: 3, mode: 0x0e
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.720410] smsc_ircc_present: can't get sir_base of 0x2e8
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.726532]
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.726538] yenta_cardbus 0000:1c:03.0: pcmcia: parent PCI bridge window: [mem 0xfc400000-0xfc4fffff]
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.726543] pcmcia_socket pcmcia_socket0: cs: memory probe 0xfc400000-0xfc4fffff: excluding 0xfc400000-0xfc40ffff
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.726561] yenta_cardbus 0000:1c:03.0: pcmcia: parent PCI bridge window: [mem 0x80000000-0x83ffffff pref]
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.726564] pcmcia_socket pcmcia_socket0: cs: memory probe 0x80000000-0x83ffffff: excluding 0x80000000-0x83ffffff
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.728373] lp0: using parport0 (interrupt-driven).
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.753205] ppdev: user-space parallel port driver
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.778976] cfg80211: World regulatory domain updated:
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.778979] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.778983] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.778986] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.778989] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.778992] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.778995] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 11 06:11:38 sam-LIFEBOOK-S6410 udev-configure-printer: add /devices/pnp0/00:0b/printer/lp0
Aug 11 06:11:38 sam-LIFEBOOK-S6410 udev-configure-printer: Failed to get parent
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.847364] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x2e8-0x2ef 0x370-0x37f
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.850394] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3ff 0x4d0-0x4d7
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.851284] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.852504] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.853405] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xd3fff 0xe0000-0xfffff
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.853475] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.853545] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.853614] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.855654] Bluetooth: Core ver 2.15
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.855704] NET: Registered protocol family 31
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.855706] Bluetooth: HCI device and connection manager initialized
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.855709] Bluetooth: HCI socket layer initialized
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.867569] Bluetooth: Generic Bluetooth USB driver ver 0.6
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.872480] usbcore: registered new interface driver btusb
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.897868] Linux video capture interface: v2.00
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.899110] usbcore: registered new interface driver usbserial
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.899131] USB Serial support registered for generic
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.900305] usbcore: registered new interface driver usbserial_generic
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.900308] usbserial: USB Serial Driver core
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.904052] USB Serial support registered for Sierra USB modem
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.904735] sierra 7-1:1.0: Sierra USB modem converter detected
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.906288] usb 7-1: Sierra USB modem converter now attached to ttyUSB0
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.906467] usb 7-1: Sierra USB modem converter now attached to ttyUSB1
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.906645] usb 7-1: Sierra USB modem converter now attached to ttyUSB2
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.906715] usbcore: registered new interface driver sierra
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.906717] sierra: v.1.7.16:USB Driver for Sierra Wireless USB modems
Aug 11 06:11:38 sam-LIFEBOOK-S6410 bluetoothd[1237]: Bluetooth deamon 4.91
Aug 11 06:11:38 sam-LIFEBOOK-S6410 bluetoothd[1250]: Starting SDP server
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.925807] uvcvideo: Found UVC 1.00 device OEM Camera (046d:09b2)
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.929147] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.929150] iwlagn: Copyright(c) 2003-2010 Intel Corporation
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.929241] iwlagn 0000:0c:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.929251] iwlagn 0000:0c:00.0: setting latency timer to 64
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.929284] iwlagn 0000:0c:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.931945] input: OEM Camera as /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0/input/input8
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.932449] usbcore: registered new interface driver uvcvideo
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.932452] USB Video Class driver (v1.0.0)
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.967718] iwlagn 0000:0c:00.0: device EEPROM VER=0x36, CALIB=0x5
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.967722] iwlagn 0000:0c:00.0: Device SKU: 0Xb
Aug 11 06:11:38 sam-LIFEBOOK-S6410 modem-manager[730]: <info>  (ttyUSB1) opening serial port...
Aug 11 06:11:38 sam-LIFEBOOK-S6410 modem-manager[730]: <info>  (ttyUSB0) opening serial port...
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.998173] Bluetooth: L2CAP ver 2.15
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   16.998176] Bluetooth: L2CAP socket layer initialized
Aug 11 06:11:38 sam-LIFEBOOK-S6410 modem-manager[730]: <info>  (ttyUSB2) opening serial port...
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   17.021919] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   17.021922] Bluetooth: BNEP filters: protocol multicast
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   17.026838] iwlagn 0000:0c:00.0: Tunable channels: 13 802.11bg, 19 802.11a channels
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   17.026926] iwlagn 0000:0c:00.0: irq 45 for MSI/MSI-X
Aug 11 06:11:38 sam-LIFEBOOK-S6410 bluetoothd[1250]: Listening for HCI events on hci0
Aug 11 06:11:38 sam-LIFEBOOK-S6410 NetworkManager[726]: <warn> bluez error getting default adapter: No such adapter
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   17.037434] Bluetooth: SCO (Voice Link) ver 0.6
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   17.037436] Bluetooth: SCO socket layer initialized
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   17.042397] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   17.042403] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   17.042421] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   17.042486] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   17.042519] HDA Intel 0000:00:1b.0: setting latency timer to 64
Aug 11 06:11:38 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:1c.2/0000:0c:00.0/ieee80211/phy0/rfkill1) (driver <unknown>)
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   17.060139] iwlagn 0000:0c:00.0: loaded firmware version 228.61.2.24
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   17.060323] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   17.074318] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
Aug 11 06:11:38 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Aug 11 06:11:38 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlagn' ifindex: 3)
Aug 11 06:11:38 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Aug 11 06:11:38 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (wlan0): now managed
Aug 11 06:11:38 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Aug 11 06:11:38 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (wlan0): bringing up device.
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   17.172905] vboxdrv: Found 2 processor cores.
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   17.173127] vboxdrv: fAsync=0 offMin=0x208 offMax=0xa6e
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   17.173379] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   17.173382] vboxdrv: Successfully loaded version 4.1.0 (interface 0x00190000).
Aug 11 06:11:38 sam-LIFEBOOK-S6410 bluetoothd[1250]: HCI dev 0 up
Aug 11 06:11:38 sam-LIFEBOOK-S6410 bluetoothd[1250]: Adapter /org/bluez/1237/hci0 has been enabled
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   17.236457] Bluetooth: RFCOMM TTY layer initialized
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   17.236462] Bluetooth: RFCOMM socket layer initialized
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   17.236465] Bluetooth: RFCOMM ver 1.11
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   17.236837] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x202000/0x0
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   17.281763] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
Aug 11 06:11:38 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (wlan0): preparing device.
Aug 11 06:11:38 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (wlan0): deactivating device (reason: 2).
Aug 11 06:11:38 sam-LIFEBOOK-S6410 NetworkManager[726]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:0c:00.0/net/wlan0, iface: wlan0)
Aug 11 06:11:38 sam-LIFEBOOK-S6410 NetworkManager[726]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:0c:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   17.336977] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 11 06:11:38 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (wlan0): supplicant interface state:  starting -> ready
Aug 11 06:11:38 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (wlan0): device state change: 2 -> 3 (reason 42)
Aug 11 06:11:38 sam-LIFEBOOK-S6410 kernel: [   17.411587] vboxpci: IOMMU not found (not registered)
Aug 11 06:11:39 sam-LIFEBOOK-S6410 init: anacron main process (1008) killed by TERM signal
Aug 11 06:11:39 sam-LIFEBOOK-S6410 wpa_supplicant[933]: Failed to initiate AP scan.
Aug 11 06:11:40 sam-LIFEBOOK-S6410 kernel: [   19.361224] Intel AES-NI instructions are not detected.
Aug 11 06:11:40 sam-LIFEBOOK-S6410 kernel: [   19.385357] padlock_aes: VIA PadLock not detected.
Aug 11 06:11:40 sam-LIFEBOOK-S6410 kernel: [   19.407506] padlock_sha: VIA PadLock Hash Engine not detected.
Aug 11 06:11:40 sam-LIFEBOOK-S6410 modprobe: FATAL: Error inserting padlock_sha (/lib/modules/2.6.38-10-generic/kernel/drivers/crypto/padlock-sha.ko): No such device
Aug 11 06:11:41 sam-LIFEBOOK-S6410 kernel: [   20.477838] Adding 2086908k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:2086908k
Aug 11 06:11:42 sam-LIFEBOOK-S6410 gdm-session-worker[1665]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Aug 11 06:11:42 sam-LIFEBOOK-S6410 rtkit-daemon[1675]: Successfully called chroot.
Aug 11 06:11:42 sam-LIFEBOOK-S6410 rtkit-daemon[1675]: Successfully dropped privileges.
Aug 11 06:11:42 sam-LIFEBOOK-S6410 rtkit-daemon[1675]: Successfully limited resources.
Aug 11 06:11:42 sam-LIFEBOOK-S6410 rtkit-daemon[1675]: Running.
Aug 11 06:11:42 sam-LIFEBOOK-S6410 rtkit-daemon[1675]: Watchdog thread running.
Aug 11 06:11:42 sam-LIFEBOOK-S6410 rtkit-daemon[1675]: Canary thread running.
Aug 11 06:11:43 sam-LIFEBOOK-S6410 rtkit-daemon[1675]: Successfully made thread 1673 of process 1673 (n/a) owned by '106' high priority at nice level -11.
Aug 11 06:11:43 sam-LIFEBOOK-S6410 rtkit-daemon[1675]: Supervising 1 threads of 1 processes of 1 users.
Aug 11 06:11:43 sam-LIFEBOOK-S6410 rtkit-daemon[1675]: Successfully made thread 1695 of process 1673 (n/a) owned by '106' RT at priority 5.
Aug 11 06:11:43 sam-LIFEBOOK-S6410 rtkit-daemon[1675]: Supervising 2 threads of 1 processes of 1 users.
Aug 11 06:11:43 sam-LIFEBOOK-S6410 rtkit-daemon[1675]: Successfully made thread 1696 of process 1673 (n/a) owned by '106' RT at priority 5.
Aug 11 06:11:43 sam-LIFEBOOK-S6410 rtkit-daemon[1675]: Supervising 3 threads of 1 processes of 1 users.
Aug 11 06:11:43 sam-LIFEBOOK-S6410 gdm-simple-greeter[1664]: Gtk-WARNING: /build/buildd/gtk+2.0-2.24.4/gtk/gtkwidget.c:5687: widget not within a GtkWindow
Aug 11 06:11:44 sam-LIFEBOOK-S6410 kernel: [   23.114095] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
Aug 11 06:11:45 sam-LIFEBOOK-S6410 init: plymouth-stop pre-start process (1758) terminated with status 1
Aug 11 06:11:45 sam-LIFEBOOK-S6410 gdm-simple-greeter[1664]: WARNING: Unable to load CK history: no seat-id found
Aug 11 06:11:45 sam-LIFEBOOK-S6410 modem-manager[730]: <info>  (ttyUSB0) closing serial port...
Aug 11 06:11:45 sam-LIFEBOOK-S6410 modem-manager[730]: <info>  (ttyUSB0) serial port closed
Aug 11 06:11:45 sam-LIFEBOOK-S6410 modem-manager[730]: <info>  (Sierra): GSM modem /sys/devices/pci0000:00/0000:00:1d.2/usb7/7-1 claimed port ttyUSB0
Aug 11 06:11:45 sam-LIFEBOOK-S6410 modem-manager[730]: <info>  (ttyUSB2) closing serial port...
Aug 11 06:11:45 sam-LIFEBOOK-S6410 modem-manager[730]: <info>  (ttyUSB2) serial port closed
Aug 11 06:11:45 sam-LIFEBOOK-S6410 modem-manager[730]: <info>  (ttyUSB2) opening serial port...
Aug 11 06:11:45 sam-LIFEBOOK-S6410 modem-manager[730]: <info>  (Sierra): GSM modem /sys/devices/pci0000:00/0000:00:1d.2/usb7/7-1 claimed port ttyUSB2
Aug 11 06:11:52 sam-LIFEBOOK-S6410 modem-manager[730]: <info>  (ttyUSB1) closing serial port...
Aug 11 06:11:52 sam-LIFEBOOK-S6410 modem-manager[730]: <info>  (ttyUSB1) serial port closed
Aug 11 06:11:52 sam-LIFEBOOK-S6410 modem-manager[730]: <info>  (ttyUSB1) opening serial port...
Aug 11 06:11:53 sam-LIFEBOOK-S6410 modem-manager[730]: <info>  (ttyUSB2) closing serial port...
Aug 11 06:11:53 sam-LIFEBOOK-S6410 modem-manager[730]: <info>  (ttyUSB2) serial port closed
Aug 11 06:11:58 sam-LIFEBOOK-S6410 modem-manager[730]: <info>  (ttyUSB1) closing serial port...
Aug 11 06:11:58 sam-LIFEBOOK-S6410 modem-manager[730]: <info>  (ttyUSB1) serial port closed
Aug 11 06:11:58 sam-LIFEBOOK-S6410 NetworkManager[726]: <warn> (ttyUSB2): failed to look up interface index
Aug 11 06:11:58 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (ttyUSB2): new GSM device (driver: 'sierra' ifindex: -1)
Aug 11 06:11:58 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (ttyUSB2): exported as /org/freedesktop/NetworkManager/Devices/2
Aug 11 06:11:58 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (ttyUSB2): now managed
Aug 11 06:11:58 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (ttyUSB2): device state change: 1 -> 2 (reason 2)
Aug 11 06:11:58 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (ttyUSB2): deactivating device (reason: 2).
Aug 11 06:11:58 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (ttyUSB2): device state change: 2 -> 3 (reason 0)
Aug 11 06:12:08 sam-LIFEBOOK-S6410 gdm-session-worker[1665]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Aug 11 06:12:12 sam-LIFEBOOK-S6410 gdm-session-worker[1665]: pam_sm_authenticate: Called
Aug 11 06:12:12 sam-LIFEBOOK-S6410 gdm-session-worker[1665]: pam_sm_authenticate: username = [sam]
Aug 11 06:12:12 sam-LIFEBOOK-S6410 gdm-session-worker[1776]: Passphrase file wrapped
Aug 11 06:12:14 sam-LIFEBOOK-S6410 kernel: [   53.185064] ecryptfs_parse_options: eCryptfs: unrecognized option [ecryptfs_check_dev_ruid]
Aug 11 06:12:19 sam-LIFEBOOK-S6410 rtkit-daemon[1675]: Successfully made thread 1874 of process 1874 (n/a) owned by '1000' high priority at nice level -11.
Aug 11 06:12:19 sam-LIFEBOOK-S6410 rtkit-daemon[1675]: Supervising 4 threads of 2 processes of 2 users.
Aug 11 06:12:20 sam-LIFEBOOK-S6410 gnome-session[1806]: WARNING: Could not launch application 'tracker-miner-fs.desktop': Unable to start application: Failed to execute child process "/usr/lib/tracker/tracker-miner-fs" (No such file or directory)
Aug 11 06:12:20 sam-LIFEBOOK-S6410 gnome-session[1806]: WARNING: Could not launch application 'tracker-store.desktop': Unable to start application: Failed to execute child process "/usr/lib/tracker/tracker-store" (No such file or directory)
Aug 11 06:12:20 sam-LIFEBOOK-S6410 gnome-session[1806]: WARNING: Could not launch application 'mail-notification.desktop': Unable to start application: Failed to execute child process "mail-notification" (No such file or directory)
Aug 11 06:12:20 sam-LIFEBOOK-S6410 gnome-session[1806]: WARNING: Could not launch application 'gnome-do.desktop': Unable to start application: Failed to execute child process "gnome-do" (No such file or directory)
Aug 11 06:12:20 sam-LIFEBOOK-S6410 gnome-session[1806]: WARNING: Could not launch application 'Screenlets%20Daemon.desktop': Unable to start application: Failed to execute child process "/usr/share/screenlets-manager/screenlets-daemon.py" (No such file or directory)
Aug 11 06:12:20 sam-LIFEBOOK-S6410 gnome-session[1806]: WARNING: Could not launch application 'tracker-status-icon.desktop': Unable to start application: Failed to execute child process "tracker-status-icon" (No such file or directory)
Aug 11 06:12:20 sam-LIFEBOOK-S6410 rtkit-daemon[1675]: Successfully made thread 1922 of process 1874 (n/a) owned by '1000' RT at priority 5.
Aug 11 06:12:20 sam-LIFEBOOK-S6410 rtkit-daemon[1675]: Supervising 5 threads of 2 processes of 2 users.
Aug 11 06:12:20 sam-LIFEBOOK-S6410 rtkit-daemon[1675]: Successfully made thread 1923 of process 1874 (n/a) owned by '1000' RT at priority 5.
Aug 11 06:12:20 sam-LIFEBOOK-S6410 rtkit-daemon[1675]: Supervising 6 threads of 2 processes of 2 users.
Aug 11 06:12:23 sam-LIFEBOOK-S6410 rtkit-daemon[1675]: Successfully made thread 1955 of process 1955 (n/a) owned by '1000' high priority at nice level -11.
Aug 11 06:12:23 sam-LIFEBOOK-S6410 rtkit-daemon[1675]: Supervising 7 threads of 3 processes of 2 users.
Aug 11 06:12:23 sam-LIFEBOOK-S6410 pulseaudio[1955]: pid.c: Daemon already running.
Aug 11 06:12:25 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Activation (wlan0) starting connection 'Auto BTHomeHub-DFF5'
Aug 11 06:12:25 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Aug 11 06:12:25 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 11 06:12:25 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 11 06:12:25 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 11 06:12:25 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 11 06:12:25 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 11 06:12:25 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Aug 11 06:12:25 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Activation (wlan0/wireless): access point 'Auto BTHomeHub-DFF5' has security, but secrets are required.
Aug 11 06:12:25 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Aug 11 06:12:25 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 11 06:12:25 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 11 06:12:25 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 11 06:12:25 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Aug 11 06:12:25 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 11 06:12:25 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 11 06:12:25 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 11 06:12:25 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Aug 11 06:12:25 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Activation (wlan0/wireless): connection 'Auto BTHomeHub-DFF5' has security, and secrets exist.  No new secrets needed.
Aug 11 06:12:25 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Config: added 'ssid' value 'BTHomeHub-DFF5'
Aug 11 06:12:25 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Config: added 'scan_ssid' value '1'
Aug 11 06:12:25 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Config: added 'key_mgmt' value 'NONE'
Aug 11 06:12:25 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Config: added 'auth_alg' value 'OPEN'
Aug 11 06:12:25 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Config: added 'wep_key0' value '<omitted>'
Aug 11 06:12:25 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Config: added 'wep_tx_keyidx' value '0'
Aug 11 06:12:25 sam-LIFEBOOK-S6410 NetworkManager[726]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 11 06:12:25 sam-LIFEBOOK-S6410 NetworkManager[726]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 11 06:12:25 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 11 06:12:25 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Config: set interface ap_scan to 1
Aug 11 06:12:25 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (wlan0): supplicant connection state:  inactive -> scanning
Aug 11 06:12:27 sam-LIFEBOOK-S6410 wpa_supplicant[933]: Trying to associate with 00:18:f6:09:a7:4b (SSID='BTHomeHub-DFF5' freq=2442 MHz)
Aug 11 06:12:27 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (wlan0): supplicant connection state:  scanning -> associating
Aug 11 06:12:27 sam-LIFEBOOK-S6410 kernel: [   66.395635] wlan0: authenticate with 00:18:f6:09:a7:4b (try 1)
Aug 11 06:12:27 sam-LIFEBOOK-S6410 kernel: [   66.397465] wlan0: authenticated
Aug 11 06:12:27 sam-LIFEBOOK-S6410 kernel: [   66.397495] wlan0: associate with 00:18:f6:09:a7:4b (try 1)
Aug 11 06:12:27 sam-LIFEBOOK-S6410 kernel: [   66.399996] wlan0: RX AssocResp from 00:18:f6:09:a7:4b (capab=0x411 status=0 aid=3)
Aug 11 06:12:27 sam-LIFEBOOK-S6410 kernel: [   66.400016] wlan0: associated
Aug 11 06:12:27 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (wlan0): supplicant connection state:  associating -> associated
Aug 11 06:12:27 sam-LIFEBOOK-S6410 kernel: [   66.425948] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Aug 11 06:12:27 sam-LIFEBOOK-S6410 wpa_supplicant[933]: Associated with 00:18:f6:09:a7:4b
Aug 11 06:12:27 sam-LIFEBOOK-S6410 wpa_supplicant[933]: CTRL-EVENT-CONNECTED - Connection to 00:18:f6:09:a7:4b completed (auth) [id=0 id_str=]
Aug 11 06:12:27 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (wlan0): supplicant connection state:  associated -> completed
Aug 11 06:12:27 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'BTHomeHub-DFF5'.
Aug 11 06:12:27 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 11 06:12:27 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Aug 11 06:12:27 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
```

---

### Post by samsanchez on 2011-08-11
/var/log/syslog Part 2:

```
Aug 11 06:12:27 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Aug 11 06:12:27 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> dhclient started with pid 2005
Aug 11 06:12:27 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Aug 11 06:12:27 sam-LIFEBOOK-S6410 dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Aug 11 06:12:27 sam-LIFEBOOK-S6410 dhclient: Copyright 2004-2010 Internet Systems Consortium.
Aug 11 06:12:27 sam-LIFEBOOK-S6410 dhclient: All rights reserved.
Aug 11 06:12:27 sam-LIFEBOOK-S6410 dhclient: For info, please visit https://www.isc.org/software/dhcp/
Aug 11 06:12:27 sam-LIFEBOOK-S6410 dhclient:
Aug 11 06:12:28 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Aug 11 06:12:28 sam-LIFEBOOK-S6410 dhclient: Listening on LPF/wlan0/00:1d:e0:67:05:1d
Aug 11 06:12:28 sam-LIFEBOOK-S6410 dhclient: Sending on   LPF/wlan0/00:1d:e0:67:05:1d
Aug 11 06:12:28 sam-LIFEBOOK-S6410 dhclient: Sending on   Socket/fallback
Aug 11 06:12:28 sam-LIFEBOOK-S6410 dhclient: DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
Aug 11 06:12:28 sam-LIFEBOOK-S6410 dhclient: DHCPACK of 192.168.1.65 from 192.168.1.254
Aug 11 06:12:28 sam-LIFEBOOK-S6410 dhclient: bound to 192.168.1.65 -- renewal in 42487 seconds.
Aug 11 06:12:28 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Aug 11 06:12:28 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Aug 11 06:12:28 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Aug 11 06:12:28 sam-LIFEBOOK-S6410 NetworkManager[726]: <info>   address 192.168.1.65
Aug 11 06:12:28 sam-LIFEBOOK-S6410 NetworkManager[726]: <info>   prefix 24 (255.255.255.0)
Aug 11 06:12:28 sam-LIFEBOOK-S6410 NetworkManager[726]: <info>   gateway 192.168.1.254
Aug 11 06:12:28 sam-LIFEBOOK-S6410 NetworkManager[726]: <info>   nameserver '192.168.1.254'
Aug 11 06:12:28 sam-LIFEBOOK-S6410 NetworkManager[726]: <info>   domain name 'home'
Aug 11 06:12:28 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Scheduling stage 5
Aug 11 06:12:28 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Aug 11 06:12:28 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Done scheduling stage 5
Aug 11 06:12:28 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Aug 11 06:12:28 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Aug 11 06:12:28 sam-LIFEBOOK-S6410 avahi-daemon[722]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.65.
Aug 11 06:12:28 sam-LIFEBOOK-S6410 avahi-daemon[722]: New relevant interface wlan0.IPv4 for mDNS.
Aug 11 06:12:28 sam-LIFEBOOK-S6410 avahi-daemon[722]: Registering new address record for 192.168.1.65 on wlan0.IPv4.
Aug 11 06:12:29 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> (wlan0): device state change: 7 -> 8 (reason 0)
Aug 11 06:12:29 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Policy set 'Auto BTHomeHub-DFF5' (wlan0) as default for IPv4 routing and DNS.
Aug 11 06:12:29 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Activation (wlan0) successful, device activated.
Aug 11 06:12:29 sam-LIFEBOOK-S6410 NetworkManager[726]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Aug 11 06:12:29 sam-LIFEBOOK-S6410 avahi-daemon[722]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::21d:e0ff:fe67:51d.
Aug 11 06:12:29 sam-LIFEBOOK-S6410 avahi-daemon[722]: New relevant interface wlan0.IPv6 for mDNS.
Aug 11 06:12:29 sam-LIFEBOOK-S6410 avahi-daemon[722]: Registering new address record for fe80::21d:e0ff:fe67:51d on wlan0.*.
Aug 11 06:12:31 sam-LIFEBOOK-S6410 kernel: [   69.784879] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
Aug 11 06:12:37 sam-LIFEBOOK-S6410 ntpdate[2073]: adjust time server 91.189.94.4 offset 0.201233 sec
Aug 11 06:12:38 sam-LIFEBOOK-S6410 kernel: [   77.416049] wlan0: no IPv6 routers present
Aug 11 06:17:01 sam-LIFEBOOK-S6410 CRON[2375]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 11 06:25:01 sam-LIFEBOOK-S6410 CRON[2409]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
Aug 11 06:32:08 sam-LIFEBOOK-S6410 kernel: Kernel logging (proc) stopped.
Aug 11 06:32:08 sam-LIFEBOOK-S6410 rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="661" x-info="http://www.rsyslog.com"] exiting on signal 15.
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: imklog 4.6.4, log source = /proc/kmsg started.
Aug 11 22:40:45 sam-LIFEBOOK-S6410 rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="619" x-info="http://www.rsyslog.com"] (re)start
Aug 11 22:40:45 sam-LIFEBOOK-S6410 rsyslogd: rsyslogd's groupid changed to 103
Aug 11 22:40:45 sam-LIFEBOOK-S6410 rsyslogd: rsyslogd's userid changed to 101
Aug 11 22:40:45 sam-LIFEBOOK-S6410 rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 gdm-binary[649]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Aug 11 22:40:45 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> NetworkManager (version 0.8.3.998) is starting...
Aug 11 22:40:45 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] Linux version 2.6.38-10-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 (Ubuntu 2.6.38-10.46-generic 2.6.38.7)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007f6d0000 (usable)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]  BIOS-e820: 000000007f6d0000 - 000000007f6df000 (ACPI data)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]  BIOS-e820: 000000007f6df000 - 000000007f6e3000 (ACPI NVS)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]  BIOS-e820: 000000007f6e3000 - 0000000080000000 (reserved)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] DMI 2.4 present.
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] DMI: FUJITSU SIEMENS LIFEBOOK S6410/FJNB1D3, BIOS Version 1.21  01/17/2008
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] last_pfn = 0x7f6d0 max_arch_pfn = 0x100000
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] MTRR default type: uncachable
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] MTRR fixed ranges enabled:
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]   00000-9FFFF write-back
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]   A0000-BFFFF uncachable
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]   C0000-D3FFF write-protect
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]   D4000-DFFFF uncachable
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]   E0000-FFFFF write-protect
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] MTRR variable ranges enabled:
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]   0 base 000000000 mask F80000000 write-back
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]   1 base 07F700000 mask FFFF00000 uncachable
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]   2 base 07F800000 mask FFF800000 uncachable
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]   3 disabled
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]   4 disabled
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]   5 disabled
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]   6 disabled
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]   7 disabled
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] initial memory mapped : 0 - 01c00000
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] RAMDISK: 35d30000 - 36e90000
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: RSDP 000f61f0 00024 (v02 FUJ   )
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: XSDT 7f6d4957 0007C (v01 FSC    PC       01210000 FUJ  00000100)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: SSDT 7f6dcde0 002D1 (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: FACP 7f6dd0b1 000F4 (v03 FSC    PC       01210000 FUJ  00000100)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: DSDT 7f6d49d3 0840D (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: FACS 7f6e2fc0 00040
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: HPET 7f6dd1a5 00038 (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: MCFG 7f6dd1dd 0003C (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: SSDT 7f6dd219 004EF (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: SSDT 7f6dd708 001CA (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: SSDT 7f6dd8d2 0106D (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: SSDT 7f6de93f 00447 (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: APIC 7f6ded86 00068 (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: BOOT 7f6dedee 00028 (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: SLIC 7f6dee16 00176 (v01 FSC    PC       01210000 FUJ  00000100)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] 1150MB HIGHMEM available.
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] 887MB LOWMEM available.
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]   low ram: 0 - 377fe000
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] Zone PFN ranges:
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]   HighMem  0x000377fe -> 0x0007f6d0
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] Movable zone start PFN for each node
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] early_node_map[2] active PFN ranges
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]     0: 0x00000010 -> 0x0000009e
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]     0: 0x00000100 -> 0x0007f6d0
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] On node 0 totalpages: 521822
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] free_area_init_node: node 0, pgdat c1784140, node_mem_map f4d40200
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]   DMA zone: 3950 pages, LIFO batch:0
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]   HighMem zone: 2302 pages used for memmap
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]   HighMem zone: 292308 pages, LIFO batch:31
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] Using APIC driver default
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] nr_irqs_gsi: 40
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e0000
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:78000000)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] PERCPU: Embedded 13 pages/cpu @f7000000 s28800 r0 d24448 u2097152
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] pcpu-alloc: s28800 r0 d24448 u2097152 alloc=1*4194304
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] pcpu-alloc: [0] 0 1
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517744
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic root=UUID=a0f75a36-c4e4-4260-ac89-a40fd602026b ro quiet splash vt.handoff=7
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] Initializing CPU#0
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] allocated 10438400 bytes of page_cgroup
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0007f6d0)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] Memory: 2032664k/2087744k available (5190k kernel code, 54624k reserved, 2539k data, 700k init, 1178440k highmem)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] virtual kernel memory layout:
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]       .data : 0xc1511841 - 0xc178c4c0   (2539 kB)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]       .text : 0xc1000000 - 0xc1511841   (5190 kB)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] Hierarchical RCU implementation.
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000]     RCU-based detection of stalled CPUs is disabled.
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] NR_IRQS:2304 nr_irqs:512 16
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] CPU 0 irqstacks, hard=f3c08000 soft=f3c0a000
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] Extended CMOS year: 2000
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] vt handoff: transparent VT on vt#7
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] Console: colour dummy device 80x25
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] console [tty0] enabled
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] hpet clockevent registered
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] Fast TSC calibration using PIT
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.000000] Detected 1994.966 MHz processor.
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.93 BogoMIPS (lpj=7979864)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.004012] pid_max: default: 32768 minimum: 301
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.004049] Security Framework initialized
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.004072] AppArmor: AppArmor initialized
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.004075] Yama: becoming mindful.
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.004165] Mount-cache hash table entries: 512
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.004372] Initializing cgroup subsys ns
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.004378] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.004383] Initializing cgroup subsys cpuacct
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.004392] Initializing cgroup subsys memory
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.004406] Initializing cgroup subsys devices
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.004410] Initializing cgroup subsys freezer
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.004414] Initializing cgroup subsys net_cls
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.004418] Initializing cgroup subsys blkio
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.004474] CPU: Physical Processor ID: 0
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.004477] CPU: Processor Core ID: 0
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.004483] mce: CPU supports 6 MCE banks
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.004495] CPU0: Thermal monitoring enabled (TM2)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.004500] using mwait in idle threads.
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.010181] ACPI: Core revision 20110112
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.024020] ftrace: allocating 23648 entries in 47 pages
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.028070] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.028448] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.070618] CPU0: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.072003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.072003] PEBS disabled due to CPU errata.
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.072003] ... version:                2
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.072003] ... bit width:              40
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.072003] ... generic registers:      2
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.072003] ... value mask:             000000ffffffffff
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.072003] ... max period:             000000007fffffff
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.072003] ... fixed-purpose events:   3
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.072003] ... event mask:             0000000700000003
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.072003] CPU 1 irqstacks, hard=f3cca000 soft=f3ccc000
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.072003] Booting Node   0, Processors  #1 Ok.
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.008000] Initializing CPU#1
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.160031] Brought up 2 CPUs
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.160036] Total of 2 processors activated (7979.93 BogoMIPS).
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.162087] devtmpfs: initialized
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.164660] print_constraints: dummy:
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.164700] Time: 21:40:29  Date: 08/11/11
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.164771] NET: Registered protocol family 16
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.164814] Trying to unpack rootfs image as initramfs...
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.164984] EISA bus registered
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.164996] ACPI: bus type pci registered
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.165124] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.165130] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.165134] PCI: Using MMCONFIG for extended config space
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.165137] PCI: Using configuration type 1 for base access
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.167077] bio: create slab <bio-0> at 0
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.170758] ACPI: EC: Look up EC in DSDT
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.176973] ACPI:      7f6e2a9f 003B7 (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.178138] ACPI: Dynamic OEM Table Load:
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.178145] ACPI:        (null) 003B7 (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.181672] ACPI: SSDT 7f6dfc19 0027A (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.182572] ACPI: Dynamic OEM Table Load:
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.182578] ACPI: SSDT   (null) 0027A (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.182878] ACPI: SSDT 7f6e0119 00627 (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.183742] ACPI: Dynamic OEM Table Load:
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.183749] ACPI: SSDT   (null) 00627 (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.208514] ACPI: SSDT 7f6e0061 000B8 (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.209403] ACPI: Dynamic OEM Table Load:
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.209410] ACPI: SSDT   (null) 000B8 (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.209625] ACPI: SSDT 7f6e0740 00047 (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.210492] ACPI: Dynamic OEM Table Load:
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.210498] ACPI: SSDT   (null) 00047 (v01 FUJ    FJNB1D3  01210000 FUJ  00000100)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.211060] ACPI: Interpreter enabled
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.211072] ACPI: (supports S0 S3 S4 S5)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.211113] ACPI: Using IOAPIC for interrupt routing
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.261857] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.305668] ACPI: ACPI Dock Station Driver: 2 docks/bays found
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.305675] HEST: Table not found.
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.305682] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.306308] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.307515] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.307521] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.307526] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.307532] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.307536] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.307541] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.307547] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xfebfffff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.307572] pci 0000:00:00.0: [8086:2a00] type 0 class 0x000600
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.307650] pci 0000:00:02.0: [8086:2a02] type 0 class 0x000300
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.307674] pci 0000:00:02.0: reg 10: [mem 0xfc000000-0xfc0fffff 64bit]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.307690] pci 0000:00:02.0: reg 18: [mem 0xe0000000-0xefffffff 64bit pref]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.307702] pci 0000:00:02.0: reg 20: [io  0x1800-0x1807]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.307759] pci 0000:00:02.1: [8086:2a03] type 0 class 0x000380
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.307780] pci 0000:00:02.1: reg 10: [mem 0xfc100000-0xfc1fffff 64bit]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.307901] pci 0000:00:1a.0: [8086:2834] type 0 class 0x000c03
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.307990] pci 0000:00:1a.0: reg 20: [io  0x1820-0x183f]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.308060] pci 0000:00:1a.1: [8086:2835] type 0 class 0x000c03
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.308129] pci 0000:00:1a.1: reg 20: [io  0x1840-0x185f]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.308197] pci 0000:00:1a.7: [8086:283a] type 0 class 0x000c03
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.308230] pci 0000:00:1a.7: reg 10: [mem 0xfc704800-0xfc704bff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.308347] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.308356] pci 0000:00:1a.7: PME# disabled
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.308394] pci 0000:00:1b.0: [8086:284b] type 0 class 0x000403
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.308422] pci 0000:00:1b.0: reg 10: [mem 0xfc700000-0xfc703fff 64bit]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.308520] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.308527] pci 0000:00:1b.0: PME# disabled
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.308563] pci 0000:00:1c.0: [8086:283f] type 1 class 0x000604
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.308664] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.308671] pci 0000:00:1c.0: PME# disabled
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.308712] pci 0000:00:1c.2: [8086:2843] type 1 class 0x000604
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.308812] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.308819] pci 0000:00:1c.2: PME# disabled
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.308865] pci 0000:00:1d.0: [8086:2830] type 0 class 0x000c03
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.308950] pci 0000:00:1d.0: reg 20: [io  0x1860-0x187f]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.309006] pci 0000:00:1d.1: [8086:2831] type 0 class 0x000c03
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.309076] pci 0000:00:1d.1: reg 20: [io  0x1880-0x189f]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.309127] pci 0000:00:1d.2: [8086:2832] type 0 class 0x000c03
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.309194] pci 0000:00:1d.2: reg 20: [io  0x18a0-0x18bf]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.309264] pci 0000:00:1d.7: [8086:2836] type 0 class 0x000c03
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.309297] pci 0000:00:1d.7: reg 10: [mem 0xfc704c00-0xfc704fff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.309413] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.309420] pci 0000:00:1d.7: PME# disabled
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.309450] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.309554] pci 0000:00:1f.0: [8086:2815] type 0 class 0x000601
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.309678] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.309687] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.309694] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at fd00 (mask 007f)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.309704] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 06e8 (mask 0007)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.309755] pci 0000:00:1f.1: [8086:2850] type 0 class 0x000101
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.309778] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.309794] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.309809] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.309825] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.309841] pci 0000:00:1f.1: reg 20: [io  0x1810-0x181f]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.309906] pci 0000:00:1f.2: [8086:2829] type 0 class 0x000106
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.309938] pci 0000:00:1f.2: reg 10: [io  0x1c00-0x1c07]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.309954] pci 0000:00:1f.2: reg 14: [io  0x18d4-0x18d7]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.309969] pci 0000:00:1f.2: reg 18: [io  0x18d8-0x18df]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.309984] pci 0000:00:1f.2: reg 1c: [io  0x18d0-0x18d3]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.310000] pci 0000:00:1f.2: reg 20: [io  0x18e0-0x18ff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.310016] pci 0000:00:1f.2: reg 24: [mem 0xfc704000-0xfc7047ff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.310072] pci 0000:00:1f.2: PME# supported from D3hot
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.310080] pci 0000:00:1f.2: PME# disabled
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.310108] pci 0000:00:1f.3: [8086:283e] type 0 class 0x000c05
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.310129] pci 0000:00:1f.3: reg 10: [mem 0x00000000-0x000000ff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.310179] pci 0000:00:1f.3: reg 20: [io  0x1c20-0x1c3f]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.310334] pci 0000:04:00.0: [11ab:4363] type 0 class 0x000200
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.310377] pci 0000:04:00.0: reg 10: [mem 0xfc200000-0xfc203fff 64bit]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.310401] pci 0000:04:00.0: reg 18: [io  0x2000-0x20ff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.310481] pci 0000:04:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.310556] pci 0000:04:00.0: supports D1 D2
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.310560] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.310570] pci 0000:04:00.0: PME# disabled
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.316049] pci 0000:00:1c.0: PCI bridge to [bus 04-07]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.316058] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.316065] pci 0000:00:1c.0:   bridge window [mem 0xfc200000-0xfc2fffff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.316077] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.316186] pci 0000:0c:00.0: [8086:4229] type 0 class 0x000280
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.316233] pci 0000:0c:00.0: reg 10: [mem 0xfc300000-0xfc301fff 64bit]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.316407] pci 0000:0c:00.0: PME# supported from D0 D3hot D3cold
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.316417] pci 0000:0c:00.0: PME# disabled
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324047] pci 0000:00:1c.2: PCI bridge to [bus 0c-0f]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324056] pci 0000:00:1c.2:   bridge window [io  0xf000-0x0000] (disabled)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324064] pci 0000:00:1c.2:   bridge window [mem 0xfc300000-0xfc3fffff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324075] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324140] pci 0000:1c:03.0: [1217:7136] type 2 class 0x000607
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324170] pci 0000:1c:03.0: reg 10: [mem 0x00000000-0x00000fff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324203] pci 0000:1c:03.0: supports D1 D2
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324207] pci 0000:1c:03.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324215] pci 0000:1c:03.0: PME# disabled
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324247] pci 0000:1c:03.2: [1217:7120] type 0 class 0x000805
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324277] pci 0000:1c:03.2: reg 10: [mem 0xfc402800-0xfc4028ff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324388] pci 0000:1c:03.2: supports D1 D2
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324392] pci 0000:1c:03.2: PME# supported from D0 D1 D2 D3hot D3cold
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324400] pci 0000:1c:03.2: PME# disabled
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324430] pci 0000:1c:03.3: [1217:7130] type 0 class 0x000180
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324460] pci 0000:1c:03.3: reg 10: [mem 0xfc400000-0xfc400fff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324580] pci 0000:1c:03.3: supports D1 D2
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324584] pci 0000:1c:03.3: PME# supported from D0 D1 D2 D3hot D3cold
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324592] pci 0000:1c:03.3: PME# disabled
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324621] pci 0000:1c:03.4: [1217:00f7] type 0 class 0x000c00
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324649] pci 0000:1c:03.4: reg 10: [mem 0xfc401000-0xfc401fff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324667] pci 0000:1c:03.4: reg 14: [mem 0xfc402000-0xfc4027ff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324761] pci 0000:1c:03.4: supports D1 D2
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324765] pci 0000:1c:03.4: PME# supported from D0 D1 D2 D3hot
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324772] pci 0000:1c:03.4: PME# disabled
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324855] pci 0000:00:1e.0: PCI bridge to [bus 1c-1d] (subtractive decode)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324863] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324871] pci 0000:00:1e.0:   bridge window [mem 0xfc400000-0xfc4fffff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324882] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324887] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324892] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324897] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324902] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324907] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324912] pci 0000:00:1e.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324917] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0xfebfffff] (subtractive decode)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.324982] pci_bus 0000:1d: [bus 1d-20] partially hidden behind transparent bridge 0000:1c [bus 1c-1d]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.325012] pci_bus 0000:00: on NUMA node 0
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.325021] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.325427] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.325549] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.325730] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.325815]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.336288] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.336394] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.336495] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.336594] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.336694] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.336793] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.336891] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.336990] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.337173] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.337205] vgaarb: loaded
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.337588] SCSI subsystem initialized
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.337679] libata version 3.00 loaded.
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.337770] usbcore: registered new interface driver usbfs
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.337792] usbcore: registered new interface driver hub
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.337842] usbcore: registered new device driver usb
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.338052] wmi: Mapper loaded
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.338056] PCI: Using ACPI for IRQ routing
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.338060] PCI: pci_cache_line_size set to 64 bytes
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.338241] reserve RAM buffer: 000000000009e000 - 000000000009ffff
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.338246] reserve RAM buffer: 000000007f6d0000 - 000000007fffffff
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.338432] NetLabel: Initializing
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.338436] NetLabel:  domain hash size = 128
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.338439] NetLabel:  protocols = UNLABELED CIPSOv4
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.338458] NetLabel:  unlabeled traffic allowed by default
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.338529] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.338538] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.338547] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.344747] Switching to clocksource hpet
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.346487] Switched to NOHz mode on CPU #0
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.346603] Switched to NOHz mode on CPU #1
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.358395] AppArmor: AppArmor Filesystem Enabled
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.358437] pnp: PnP ACPI init
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.358467] ACPI: bus type pnp registered
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359106] pnp 00:00: [bus 00-ff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359112] pnp 00:00: [io  0x0000-0x0cf7 window]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359116] pnp 00:00: [io  0x0cf8-0x0cff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359120] pnp 00:00: [io  0x0d00-0xffff window]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359125] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359130] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359134] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359139] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359143] pnp 00:00: [mem 0x000cc000-0x000cffff window]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359148] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359152] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359157] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359161] pnp 00:00: [mem 0x000dc000-0x000dffff window]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359166] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359170] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359175] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359179] pnp 00:00: [mem 0x000ec000-0x000effff window]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359184] pnp 00:00: [mem 0x000f0000-0x000fffff window]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359189] pnp 00:00: [mem 0x80000000-0xfebfffff window]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359193] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359339] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359443] pnp 00:01: [io  0x0010-0x001f]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359448] pnp 00:01: [io  0x0024-0x0025]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359452] pnp 00:01: [io  0x0028-0x0029]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359456] pnp 00:01: [io  0x002c-0x002d]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359459] pnp 00:01: [io  0x002e-0x002f]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359463] pnp 00:01: [io  0x0030-0x0031]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359467] pnp 00:01: [io  0x0034-0x0035]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359471] pnp 00:01: [io  0x0038-0x0039]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359474] pnp 00:01: [io  0x003c-0x003d]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359483] pnp 00:01: [io  0x004e-0x004f]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359487] pnp 00:01: [io  0x0050-0x0053]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359490] pnp 00:01: [io  0x0061]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359494] pnp 00:01: [io  0x0063]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359497] pnp 00:01: [io  0x0065]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359501] pnp 00:01: [io  0x0067]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359504] pnp 00:01: [io  0x0072-0x0077]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359508] pnp 00:01: [io  0x0080]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359512] pnp 00:01: [io  0x0090-0x009f]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359515] pnp 00:01: [io  0x0092]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359519] pnp 00:01: [io  0x00a4-0x00a5]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359523] pnp 00:01: [io  0x00a8-0x00a9]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359527] pnp 00:01: [io  0x00ac-0x00ad]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359530] pnp 00:01: [io  0x00b0-0x00b1]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359534] pnp 00:01: [io  0x00b2-0x00b3]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359538] pnp 00:01: [io  0x00b4-0x00b5]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359541] pnp 00:01: [io  0x00b8-0x00b9]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359545] pnp 00:01: [io  0x00bc-0x00bd]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359548] pnp 00:01: [io  0x04d0-0x04d1]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359552] pnp 00:01: [io  0x0680-0x069f]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359556] pnp 00:01: [io  0x0800-0x080f]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359560] pnp 00:01: [io  0x1000-0x107f]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359563] pnp 00:01: [io  0x1080-0x10ff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359567] pnp 00:01: [io  0x1100-0x111f]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359571] pnp 00:01: [io  0x1180-0x11bf]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359574] pnp 00:01: [io  0x1640-0x164f]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359578] pnp 00:01: [io  0xf800-0xf87f]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359582] pnp 00:01: [io  0xf880-0xf8ff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359585] pnp 00:01: [io  0xfc00-0xfc7f]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359589] pnp 00:01: [io  0xfc80-0xfcff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359593] pnp 00:01: [io  0xfd00-0xfd7f]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359597] pnp 00:01: [io  0xfe00-0xfe03]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359809] system 00:01: [io  0x04d0-0x04d1] has been reserved
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359815] system 00:01: [io  0x0680-0x069f] has been reserved
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359821] system 00:01: [io  0x0800-0x080f] has been reserved
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359826] system 00:01: [io  0x1000-0x107f] has been reserved
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359831] system 00:01: [io  0x1080-0x10ff] has been reserved
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359837] system 00:01: [io  0x1100-0x111f] has been reserved
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359842] system 00:01: [io  0x1180-0x11bf] has been reserved
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359847] system 00:01: [io  0x1640-0x164f] has been reserved
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359852] system 00:01: [io  0xf800-0xf87f] has been reserved
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359858] system 00:01: [io  0xf880-0xf8ff] has been reserved
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359863] system 00:01: [io  0xfc00-0xfc7f] has been reserved
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359868] system 00:01: [io  0xfc80-0xfcff] has been reserved
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359873] system 00:01: [io  0xfd00-0xfd7f] has been reserved
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359878] system 00:01: [io  0xfe00-0xfe03] has been reserved
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.359885] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.360074] pnp 00:02: [mem 0xfed1c000-0xfed1ffff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.360079] pnp 00:02: [mem 0xfed14000-0xfed17fff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.360083] pnp 00:02: [mem 0xfed18000-0xfed18fff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.360087] pnp 00:02: [mem 0xfed19000-0xfed19fff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.360091] pnp 00:02: [mem 0xf8000000-0xfbffffff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.360095] pnp 00:02: [mem 0xfed20000-0xfed3ffff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.360099] pnp 00:02: [mem 0xfed40000-0xfed44fff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.360103] pnp 00:02: [mem 0xfed45000-0xfed8ffff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.360108] pnp 00:02: [mem 0xfef00000-0xfeffffff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.360209] system 00:02: [mem 0xfed1c000-0xfed1ffff] has been reserved
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.360215] system 00:02: [mem 0xfed14000-0xfed17fff] has been reserved
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.360221] system 00:02: [mem 0xfed18000-0xfed18fff] has been reserved
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.360226] system 00:02: [mem 0xfed19000-0xfed19fff] has been reserved
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.360232] system 00:02: [mem 0xf8000000-0xfbffffff] has been reserved
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.360237] system 00:02: [mem 0xfed20000-0xfed3ffff] has been reserved
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.360243] system 00:02: [mem 0xfed40000-0xfed44fff] has been reserved
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.360248] system 00:02: [mem 0xfed45000-0xfed8ffff] has been reserved
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.360254] system 00:02: [mem 0xfef00000-0xfeffffff] has been reserved
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.360260] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.360760] pnp 00:03: [io  0x0000-0x000f]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.360765] pnp 00:03: [io  0x0081-0x008f]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.360769] pnp 00:03: [io  0x00c0-0x00df]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.360773] pnp 00:03: [dma 4]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.360873] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.360905] pnp 00:04: [io  0x0060]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.360909] pnp 00:04: [io  0x0064]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.360925] pnp 00:04: [irq 1]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.361021] pnp 00:04: Plug and Play ACPI device, IDs PNP0303 (active)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.361052] pnp 00:05: [io  0x00f0-0x00fe]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.361062] pnp 00:05: [irq 13]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.361163] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.361212] pnp 00:06: [irq 12]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.361310] pnp 00:06: Plug and Play ACPI device, IDs PNP0f13 (active)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.361340] pnp 00:07: [io  0x0070-0x0071]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.361349] pnp 00:07: [irq 8]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.361451] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.361481] pnp 00:08: [io  0x0061]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.361581] pnp 00:08: Plug and Play ACPI device, IDs PNP0800 (active)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.361990] pnp 00:09: [io  0x03f8-0x03ff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.362000] pnp 00:09: [irq 4]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.362143] pnp 00:09: Plug and Play ACPI device, IDs PNP0501 (active)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.362812] pnp 00:0a: [io  0x02e8-0x02ef]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.362817] pnp 00:0a: [io  0x06e8-0x06ef]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.362827] pnp 00:0a: [irq 3]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.362831] pnp 00:0a: [dma 3]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.362984] pnp 00:0a: Plug and Play ACPI device, IDs SMCf010 (active)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.363518] pnp 00:0b: [io  0x0378-0x037f]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.363524] pnp 00:0b: [io  0x0778-0x077b]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.363533] pnp 00:0b: [irq 7]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.363702] pnp 00:0b: Plug and Play ACPI device, IDs PNP0400 (active)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.364204] pnp: PnP ACPI: found 12 devices
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.364208] ACPI: ACPI bus type pnp unregistered
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.364215] PnPBIOS: Disabled by ACPI PNP
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402328] pci 0000:00:1e.0: BAR 15: assigned [mem 0x80000000-0x83ffffff pref]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402338] pci 0000:00:1c.0: BAR 15: assigned [mem 0x84000000-0x841fffff pref]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402346] pci 0000:00:1c.2: BAR 15: assigned [mem 0x84200000-0x843fffff 64bit pref]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402353] pci 0000:00:1c.2: BAR 13: assigned [io  0x3000-0x3fff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402359] pci 0000:00:1e.0: BAR 13: assigned [io  0x4000-0x4fff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402367] pci 0000:00:1f.3: BAR 0: assigned [mem 0x84400000-0x844000ff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402376] pci 0000:00:1f.3: BAR 0: set to [mem 0x84400000-0x844000ff] (PCI address [0x84400000-0x844000ff])
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402382] pci 0000:04:00.0: BAR 6: assigned [mem 0x84000000-0x8401ffff pref]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402388] pci 0000:00:1c.0: PCI bridge to [bus 04-07]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402394] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402404] pci 0000:00:1c.0:   bridge window [mem 0xfc200000-0xfc2fffff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402411] pci 0000:00:1c.0:   bridge window [mem 0x84000000-0x841fffff pref]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402422] pci 0000:00:1c.2: PCI bridge to [bus 0c-0f]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402428] pci 0000:00:1c.2:   bridge window [io  0x3000-0x3fff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402437] pci 0000:00:1c.2:   bridge window [mem 0xfc300000-0xfc3fffff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402445] pci 0000:00:1c.2:   bridge window [mem 0x84200000-0x843fffff 64bit pref]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402459] pci 0000:1c:03.0: BAR 15: assigned [mem 0x80000000-0x83ffffff pref]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402467] pci 0000:1c:03.0: BAR 16: assigned [mem 0x88000000-0x8bffffff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402473] pci 0000:1c:03.0: BAR 0: assigned [mem 0xfc403000-0xfc403fff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402483] pci 0000:1c:03.0: BAR 0: set to [mem 0xfc403000-0xfc403fff] (PCI address [0xfc403000-0xfc403fff])
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402488] pci 0000:1c:03.0: BAR 13: assigned [io  0x4000-0x40ff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402493] pci 0000:1c:03.0: BAR 14: assigned [io  0x4400-0x44ff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402498] pci 0000:1c:03.0: CardBus bridge to [bus 1d-20]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402502] pci 0000:1c:03.0:   bridge window [io  0x4000-0x40ff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402510] pci 0000:1c:03.0:   bridge window [io  0x4400-0x44ff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402518] pci 0000:1c:03.0:   bridge window [mem 0x80000000-0x83ffffff pref]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402526] pci 0000:1c:03.0:   bridge window [mem 0x88000000-0x8bffffff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402534] pci 0000:00:1e.0: PCI bridge to [bus 1c-1d]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402540] pci 0000:00:1e.0:   bridge window [io  0x4000-0x4fff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402549] pci 0000:00:1e.0:   bridge window [mem 0xfc400000-0xfc4fffff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402557] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0x83ffffff pref]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402593] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402602] pci 0000:00:1c.0: setting latency timer to 64
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402620] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402627] pci 0000:00:1c.2: setting latency timer to 64
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402639] pci 0000:00:1e.0: setting latency timer to 64
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402652] pci 0000:1c:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402661] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402666] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402671] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402675] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402680] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402684] pci_bus 0000:00: resource 9 [mem 0x000dc000-0x000dffff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402689] pci_bus 0000:00: resource 10 [mem 0x80000000-0xfebfffff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402694] pci_bus 0000:04: resource 0 [io  0x2000-0x2fff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402698] pci_bus 0000:04: resource 1 [mem 0xfc200000-0xfc2fffff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402703] pci_bus 0000:04: resource 2 [mem 0x84000000-0x841fffff pref]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402708] pci_bus 0000:0c: resource 0 [io  0x3000-0x3fff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402713] pci_bus 0000:0c: resource 1 [mem 0xfc300000-0xfc3fffff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402718] pci_bus 0000:0c: resource 2 [mem 0x84200000-0x843fffff 64bit pref]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402722] pci_bus 0000:1c: resource 0 [io  0x4000-0x4fff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402727] pci_bus 0000:1c: resource 1 [mem 0xfc400000-0xfc4fffff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402732] pci_bus 0000:1c: resource 2 [mem 0x80000000-0x83ffffff pref]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402737] pci_bus 0000:1c: resource 4 [io  0x0000-0x0cf7]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402741] pci_bus 0000:1c: resource 5 [io  0x0d00-0xffff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402746] pci_bus 0000:1c: resource 6 [mem 0x000a0000-0x000bffff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402750] pci_bus 0000:1c: resource 7 [mem 0x000d4000-0x000d7fff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402755] pci_bus 0000:1c: resource 8 [mem 0x000d8000-0x000dbfff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402759] pci_bus 0000:1c: resource 9 [mem 0x000dc000-0x000dffff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402764] pci_bus 0000:1c: resource 10 [mem 0x80000000-0xfebfffff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402769] pci_bus 0000:1d: resource 0 [io  0x4000-0x40ff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402773] pci_bus 0000:1d: resource 1 [io  0x4400-0x44ff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402778] pci_bus 0000:1d: resource 2 [mem 0x80000000-0x83ffffff pref]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402783] pci_bus 0000:1d: resource 3 [mem 0x88000000-0x8bffffff]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402846] NET: Registered protocol family 2
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.402967] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.403376] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.403962] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.404266] TCP: Hash tables configured (established 131072 bind 65536)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.404270] TCP reno registered
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.404276] UDP hash table entries: 512 (order: 2, 16384 bytes)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.404288] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.404409] NET: Registered protocol family 1
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.404435] pci 0000:00:02.0: Boot video device
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.404670] PCI: CLS 64 bytes, default 64
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.404706] Simple Boot Flag at 0x7b set to 0x1
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.405042] cpufreq-nforce2: No nForce2 chipset.
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.405266] audit: initializing netlink socket (disabled)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.405279] type=2000 audit(1313098829.400:1): initialized
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.422317] highmem bounce pool size: 64 pages
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.422326] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.425802] VFS: Disk quotas dquot_6.5.2
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.425913] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.427148] fuse init (API version 7.16)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.427322] msgmni has been set to 1668
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.427727] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.427777] io scheduler noop registered
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.427781] io scheduler deadline registered
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.427808] io scheduler cfq registered (default)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.428050] pcieport 0000:00:1c.0: setting latency timer to 64
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.428133] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.428256] pcieport 0000:00:1c.2: setting latency timer to 64
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.428333] pcieport 0000:00:1c.2: irq 41 for MSI/MSI-X
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.428499] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.428543] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.428714] intel_idle: MWAIT substates: 0x22220
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.428717] intel_idle: does not run on family 6 model 15
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.428868] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.428981] ACPI: AC Adapter [AC] (off-line)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.429126] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.492021] ACPI: Lid Switch [LID]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.492141] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.492150] ACPI: Power Button [PWRB]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.492240] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.492247] ACPI: Sleep Button [SLPB]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.492329] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.492335] ACPI: Power Button [PWRF]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.492724] ACPI: acpi_idle registered with cpuidle
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.493062] Monitor-Mwait will be used to enter C-1 state
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.493116] Monitor-Mwait will be used to enter C-2 state
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.493159] Monitor-Mwait will be used to enter C-3 state
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.493168] Marking TSC unstable due to TSC halts in idle
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.508659] thermal LNXTHERM:00: registered as thermal_zone0
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.508664] ACPI: Thermal Zone [TZ00] (27 C)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.508939] thermal LNXTHERM:01: registered as thermal_zone1
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.508944] ACPI: Thermal Zone [TZ01] (27 C)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.509078] ERST: Table is not found!
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.509203] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.529912] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.530070] isapnp: Scanning for PnP cards...
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.547945] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.547961] ACPI: Battery Slot [CMB1] (battery present)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.548022] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.548034] ACPI: Battery Slot [CMB2] (battery absent)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.884725] isapnp: No Plug & Play device found
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.885846] Freeing initrd memory: 17792k freed
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.932632] serial8250: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.956376] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.956823] Linux agpgart interface v0.103
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.957035] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.957178] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.959070] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.959235] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.961705] brd: module loaded
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.962861] loop: module loaded
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.963017] i2c-core: driver [adp5520] using legacy suspend method
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.963021] i2c-core: driver [adp5520] using legacy resume method
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.963193] ata_piix 0000:00:1f.1: version 2.13
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.963225] ata_piix 0000:00:1f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.963278] ata_piix 0000:00:1f.1: setting latency timer to 64
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.963903] scsi0 : ata_piix
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.964088] scsi1 : ata_piix
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.964868] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.964874] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.965593] Fixed MDIO Bus: probed
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.965667] PPP generic driver version 2.4.2
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.965743] tun: Universal TUN/TAP device driver, 1.6
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.965747] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.965905] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.965940] ehci_hcd 0000:00:1a.7: PCI INT B -> GSI 23 (level, low) -> IRQ 23
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.965961] ehci_hcd 0000:00:1a.7: setting latency timer to 64
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.965967] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.966035] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.966117] ehci_hcd 0000:00:1a.7: debug port 1
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.969998] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.970025] ehci_hcd 0000:00:1a.7: irq 23, io mem 0xfc704800
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.984025] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.984253] hub 1-0:1.0: USB hub found
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.984261] hub 1-0:1.0: 4 ports detected
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.984402] ehci_hcd 0000:00:1d.7: PCI INT B -> GSI 23 (level, low) -> IRQ 23
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.984421] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.984427] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.984502] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.984579] ehci_hcd 0000:00:1d.7: debug port 1
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.988463] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    0.988473] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfc704c00
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.004025] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.004250] hub 2-0:1.0: USB hub found
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.004258] hub 2-0:1.0: 6 ports detected
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.004410] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.004437] uhci_hcd: USB Universal Host Controller Interface driver
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.004483] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.004494] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.004500] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.004569] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.004649] uhci_hcd 0000:00:1a.0: irq 22, io base 0x00001820
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.004873] hub 3-0:1.0: USB hub found
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.004880] hub 3-0:1.0: 2 ports detected
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.005011] uhci_hcd 0000:00:1a.1: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.005021] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.005027] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.005097] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.005160] uhci_hcd 0000:00:1a.1: irq 22, io base 0x00001840
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.005387] hub 4-0:1.0: USB hub found
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.005395] hub 4-0:1.0: 2 ports detected
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.005531] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.005541] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.005547] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.005619] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.008067] uhci_hcd 0000:00:1d.0: irq 22, io base 0x00001860
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.008296] hub 5-0:1.0: USB hub found
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.008303] hub 5-0:1.0: 2 ports detected
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.008435] uhci_hcd 0000:00:1d.1: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.008446] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.008452] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.008529] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.008592] uhci_hcd 0000:00:1d.1: irq 22, io base 0x00001880
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.008825] hub 6-0:1.0: USB hub found
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.008832] hub 6-0:1.0: 2 ports detected
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.008963] uhci_hcd 0000:00:1d.2: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.008976] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.008982] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.009049] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.009111] uhci_hcd 0000:00:1d.2: irq 22, io base 0x000018a0
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.009331] hub 7-0:1.0: USB hub found
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.009338] hub 7-0:1.0: 2 ports detected
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.009585] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.012219] i8042: Detected active multiplexing controller, rev 1.1
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.013610] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.013620] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.013677] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.013731] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.013781] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.014000] mousedev: PS/2 mouse device common for all mice
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.014336] rtc_cmos 00:07: RTC can wake from S4
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.014437] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.014477] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.014618] device-mapper: uevent: version 1.0.3
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.014763] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.014862] device-mapper: multipath: version 1.2.0 loaded
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.014867] device-mapper: multipath round-robin: version 1.0.0 loaded
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.014995] EISA: Probing bus 0 at eisa.0
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.014999] EISA: Cannot allocate resource for mainboard
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.015003] Cannot allocate resource for EISA slot 1
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.015007] Cannot allocate resource for EISA slot 2
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.015010] Cannot allocate resource for EISA slot 3
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.015013] Cannot allocate resource for EISA slot 4
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.015017] Cannot allocate resource for EISA slot 5
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.015020] Cannot allocate resource for EISA slot 6
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.015023] Cannot allocate resource for EISA slot 7
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.015027] Cannot allocate resource for EISA slot 8
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.015030] EISA: Detected 0 cards.
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.015239] cpuidle: using governor ladder
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.015432] cpuidle: using governor menu
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.015972] TCP cubic registered
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.016229] NET: Registered protocol family 10
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.017319] NET: Registered protocol family 17
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.017349] Registering the dns_resolver key type
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.018229] Using IPI No-Shortcut mode
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.018378] PM: Hibernation image not present or could not be loaded.
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.018389] registered taskstats version 1
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.018743]   Magic number: 7:200:702
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.018846] rtc_cmos 00:07: setting system clock to 2011-08-11 21:40:30 UTC (1313098830)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.018849] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.018851] EDD information not available.
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.041859] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.131889] ata1.00: ATAPI: Optiarc  DVD RW AD-7910A, 1.50, max UDMA/33
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.148355] ata1.00: configured for UDMA/33
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.151215] scsi 0:0:0:0: CD-ROM            Optiarc  DVD RW AD-7910A  1.50 PQ: 0 ANSI: 5
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.157047] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.157050] cdrom: Uniform CD-ROM driver Revision: 3.20
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.157162] sr 0:0:0:0: Attached scsi CD-ROM sr0
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.157228] sr 0:0:0:0: Attached scsi generic sg0 type 5
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.157383] Freeing unused kernel memory: 700k freed
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.157661] Write protecting the kernel text: 5192k
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.157731] Write protecting the kernel read-only data: 2148k
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.182881] <30>udev[76]: starting version 167
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.278949] sdhci: Secure Digital Host Controller Interface driver
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.278952] sdhci: Copyright(c) Pierre Ossman
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.291479] sdhci-pci 0000:1c:03.2: SDHCI controller found [1217:7120] (rev 2)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.291498] sdhci-pci 0000:1c:03.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.291551] mmc0: no vmmc regulator found
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.291588] Registered led device: mmc0::
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.291640] mmc0: SDHCI controller on PCI [0000:1c:03.2] using PIO
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.313851] firewire_ohci 0000:1c:03.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.314312] ahci 0000:00:1f.2: version 3.0
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.314325] ahci 0000:00:1f.2: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.314379] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.314451] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.314455] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.314461] ahci 0000:00:1f.2: setting latency timer to 64
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.320475] sky2: driver version 1.28
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.320512] sky2 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.320528] sky2 0000:04:00.0: setting latency timer to 64
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.320559] sky2 0000:04:00.0: Yukon-2 EC Ultra chip revision 3
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.320710] sky2 0000:04:00.0: irq 43 for MSI/MSI-X
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.321396] scsi2 : ahci
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.321506] sky2 0000:04:00.0: eth0: addr 00:17:42:74:cd:23
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.321707] scsi3 : ahci
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.323149] scsi4 : ahci
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.323300] ata3: SATA max UDMA/133 abar m2048@0xfc704000 port 0xfc704100 irq 42
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.323305] ata4: SATA max UDMA/133 abar m2048@0xfc704000 port 0xfc704180 irq 42
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.323309] ata5: SATA max UDMA/133 abar m2048@0xfc704000 port 0xfc704200 irq 42
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.349524] [drm] Initialized drm 1.1.0 20060810
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.368134] firewire_ohci: Added fw-ohci device 0000:1c:03.4, OHCI v1.10, 8 IR + 8 IT contexts, quirks 0x0
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.408070] usb 1-3: new high speed USB device using ehci_hcd and address 3
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.640149] ata4: SATA link down (SStatus 0 SControl 300)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.640186] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.641064] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.641068] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.648059] ata5: SATA link down (SStatus 0 SControl 300)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.692520] ata3.00: ATA-8: ST9320325AS, 0001SDM1, max UDMA/133
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.692523] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.694333] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.694337] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.694695] ata3.00: configured for UDMA/133
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.694866] scsi 2:0:0:0: Direct-Access     ATA      ST9320325AS      0001 PQ: 0 ANSI: 5
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.695026] sd 2:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.695062] sd 2:0:0:0: Attached scsi generic sg1 type 0
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.695080] sd 2:0:0:0: [sda] Write Protect is off
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.695084] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.695108] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.736956]  sda: sda1 sda2 < sda5 >
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.737264] sd 2:0:0:0: [sda] Attached SCSI disk
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.764611] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.764617] i915 0000:00:02.0: setting latency timer to 64
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.781503] i915 0000:00:02.0: irq 44 for MSI/MSI-X
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.781510] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.781512] [drm] Driver supports precise vblank timestamp query.
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.868139] firewire_core: created device fw0: GUID 00000e1003d43d25, S400
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.924044] usb 3-2: new full speed USB device using uhci_hcd and address 2
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.937376] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    1.937707] [drm] initialized overlay support
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    2.392082] usb 5-2: new full speed USB device using uhci_hcd and address 2
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    2.604550] fbcon: inteldrmfb (fb0) is primary device
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    2.604613] Console: switching to colour frame buffer device 160x50
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    2.604650] fb0: inteldrmfb frame buffer device
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    2.604652] drm: registered panic notifier
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    2.606878] acpi device:04: registered as cooling_device2
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    2.606994] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    2.607041] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    2.607178] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    3.252361] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [    4.672053] usb 7-1: new full speed USB device using uhci_hcd and address 2
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [   15.931428] <30>udev[358]: starting version 167
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [   15.958622] lp: driver loaded but no devices found
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [   15.968262] fujitsu-laptop: Identified laptop model 'Fujitsu Siemens S6410'.
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [   15.968402] input: Fujitsu FUJ02B1 as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:38/FUJ02B1:00/input/input6
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [   15.968504] ACPI: Fujitsu FUJ02B1 [FJEX] (on)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [   16.011739] input: Fujitsu FUJ02E3 as /devices/LNXSYSTM:00/device:00/FUJ02E3:00/input/input7
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [   16.011843] ACPI: Fujitsu FUJ02E3 [FEXT] (on)
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [   16.012293] fujitsu-laptop: BTNI: [0xff0101]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [   16.024166] fujitsu-laptop: driver 0.6.0 successfully loaded.
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [   16.100282] EXT4-fs (sda1): warning: maximal mount count reached, running e2fsck is recommended
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [   16.108843] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [   16.172667] parport_pc 00:0b: reported by Plug and Play ACPI
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [   16.172712] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [   16.268645] lp0: using parport0 (interrupt-driven).
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [   16.286375] type=1400 audit(1313098845.762:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=642 comm="apparmor_parser"
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [   16.287332] type=1400 audit(1313098845.762:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=642 comm="apparmor_parser"
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [   16.287937] type=1400 audit(1313098845.762:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=642 comm="apparmor_parser"
Aug 11 22:40:45 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Aug 11 22:40:45 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> trying to start the modem manager...
Aug 11 22:40:45 sam-LIFEBOOK-S6410 modem-manager[821]: <info>  ModemManager (version 0.4) starting...
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [   16.455061] yenta_cardbus 0000:1c:03.0: CardBus bridge found [10cf:143d]
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [   16.455092] yenta_cardbus 0000:1c:03.0: O2: enabling read prefetch/write burst. If you experience problems or performance issues, use the yenta_socket parameter 'o2_speedup=off'
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [   16.465836] type=1400 audit(1313098845.942:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=840 comm="apparmor_parser"
Aug 11 22:40:45 sam-LIFEBOOK-S6410 modem-manager[821]: <info>  Loaded plugin Sierra
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [   16.469873] type=1400 audit(1313098845.946:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=841 comm="apparmor_parser"
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [   16.470844] type=1400 audit(1313098845.946:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=841 comm="apparmor_parser"
Aug 11 22:40:45 sam-LIFEBOOK-S6410 modem-manager[821]: <info>  Loaded plugin Gobi
Aug 11 22:40:45 sam-LIFEBOOK-S6410 modem-manager[821]: <info>  Loaded plugin Option High-Speed
Aug 11 22:40:45 sam-LIFEBOOK-S6410 modem-manager[821]: <info>  Loaded plugin X22X
Aug 11 22:40:45 sam-LIFEBOOK-S6410 modem-manager[821]: <info>  Loaded plugin Nokia
Aug 11 22:40:45 sam-LIFEBOOK-S6410 modem-manager[821]: <info>  Loaded plugin AnyData
Aug 11 22:40:45 sam-LIFEBOOK-S6410 modem-manager[821]: <info>  Loaded plugin SimTech
Aug 11 22:40:45 sam-LIFEBOOK-S6410 modem-manager[821]: <info>  Loaded plugin Linktop
Aug 11 22:40:45 sam-LIFEBOOK-S6410 modem-manager[821]: <info>  Loaded plugin Longcheer
Aug 11 22:40:45 sam-LIFEBOOK-S6410 modem-manager[821]: <info>  Loaded plugin Huawei
Aug 11 22:40:45 sam-LIFEBOOK-S6410 modem-manager[821]: <info>  Loaded plugin MotoC
Aug 11 22:40:45 sam-LIFEBOOK-S6410 modem-manager[821]: <info>  Loaded plugin Generic
Aug 11 22:40:45 sam-LIFEBOOK-S6410 modem-manager[821]: <info>  Loaded plugin Novatel
Aug 11 22:40:45 sam-LIFEBOOK-S6410 modem-manager[821]: <info>  Loaded plugin Ericsson MBM
Aug 11 22:40:45 sam-LIFEBOOK-S6410 modem-manager[821]: <info>  Loaded plugin Option
Aug 11 22:40:45 sam-LIFEBOOK-S6410 modem-manager[821]: <info>  Loaded plugin ZTE
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [   16.481037] type=1400 audit(1313098845.958:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=841 comm="apparmor_parser"
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [   16.486420] type=1400 audit(1313098845.962:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/freshclam" pid=853 comm="apparmor_parser"
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [   16.492224] type=1400 audit(1313098845.970:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=854 comm="apparmor_parser"
Aug 11 22:40:45 sam-LIFEBOOK-S6410 kernel: [   16.498539] type=1400 audit(1313098845.974:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=854 comm="apparmor_parser"
Aug 11 22:40:46 sam-LIFEBOOK-S6410 polkitd[827]: started daemon version 0.101 using authority implementation `local' version `0.101'
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> monitoring kernel firmware directory '/lib/firmware'.
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]:    SCPlugin-Ifupdown: init!
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]:    SCPlugin-Ifupdown: update_system_hostname
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]:    SCPluginIfupdown: management mode: unmanaged
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:04:00.0/net/eth0, iface: eth0)
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:04:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]:    SCPlugin-Ifupdown: end _init.
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]:    Ifupdown: get unmanaged devices count: 0
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]:    SCPlugin-Ifupdown: (166489120) ... get_connections.
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]:    SCPlugin-Ifupdown: (166489120) ... get_connections (managed=false): return empty list.
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.584902] yenta_cardbus 0000:1c:03.0: ISA IRQ mask 0x0c38, PCI irq 16
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.584907] yenta_cardbus 0000:1c:03.0: Socket status: 30000006
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.584911] pci_bus 0000:1c: Raising subordinate bus# of parent bus (#1c) from #1d to #20
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.588161] yenta_cardbus 0000:1c:03.0: pcmcia: parent PCI bridge window: [io  0x4000-0x4fff]
Aug 11 22:40:46 sam-LIFEBOOK-S6410 gdm-binary[649]: WARNING: Unable to find users: no seat-id found
Aug 11 22:40:46 sam-LIFEBOOK-S6410 gdm-simple-slave[869]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]:    Ifupdown: get unmanaged devices count: 0
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> WiFi enabled by radio killswitch; enabled by state file
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> WWAN enabled by radio killswitch; enabled by state file
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> WiMAX enabled by radio killswitch; enabled by state file
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Networking is enabled by state file
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.588166] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x4000-0x4fff: excluding 0x4000-0x40ff 0x4400-0x44ff
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.631061] sky2 0000:04:00.0: eth0: enabling interface
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.631319] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (eth0): carrier is OFF
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (eth0): new Ethernet device (driver: 'sky2' ifindex: 2)
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (eth0): now managed
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (eth0): bringing up device.
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (eth0): preparing device.
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (eth0): deactivating device (reason: 2).
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.0/0000:04:00.0/net/eth0
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> modem-manager is now available
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Trying to start the supplicant...
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.654733]
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.654740] yenta_cardbus 0000:1c:03.0: pcmcia: parent PCI bridge window: [mem 0xfc400000-0xfc4fffff]
Aug 11 22:40:46 sam-LIFEBOOK-S6410 init: apport pre-start process (931) terminated with status 1
Aug 11 22:40:46 sam-LIFEBOOK-S6410 init: alsa-restore main process (945) terminated with status 19
Aug 11 22:40:46 sam-LIFEBOOK-S6410 anacron[972]: Anacron 2.3 started on 2011-08-11
Aug 11 22:40:46 sam-LIFEBOOK-S6410 acpid: starting up with proc fs
Aug 11 22:40:46 sam-LIFEBOOK-S6410 acpid: 32 rules loaded
Aug 11 22:40:46 sam-LIFEBOOK-S6410 acpid: waiting for events: event logging is off
Aug 11 22:40:46 sam-LIFEBOOK-S6410 cron[949]: (CRON) INFO (pidfile fd = 3)
Aug 11 22:40:46 sam-LIFEBOOK-S6410 init: apport post-stop process (974) terminated with status 1
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.761575] pcmcia_socket pcmcia_socket0: cs: memory probe 0xfc400000-0xfc4fffff: excluding 0xfc400000-0xfc40ffff
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.761597] yenta_cardbus 0000:1c:03.0: pcmcia: parent PCI bridge window: [mem 0x80000000-0x83ffffff pref]
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.761601] pcmcia_socket pcmcia_socket0: cs: memory probe 0x80000000-0x83ffffff: excluding 0x80000000-0x83ffffff
Aug 11 22:40:46 sam-LIFEBOOK-S6410 cron[994]: (CRON) STARTUP (fork ok)
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.795179] cfg80211: Calling CRDA to update world regulatory domain
Aug 11 22:40:46 sam-LIFEBOOK-S6410 cron[994]: (CRON) INFO (Running @reboot jobs)
Aug 11 22:40:46 sam-LIFEBOOK-S6410 anacron[972]: Will run job `cron.daily' in 5 min.
Aug 11 22:40:46 sam-LIFEBOOK-S6410 anacron[972]: Jobs will be executed sequentially
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.880961] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x202000/0x0
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.919288] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.937528] ppdev: user-space parallel port driver
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.938253] cfg80211: World regulatory domain updated:
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.938256] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.938259] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.938262] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.938265] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.938268] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.938271] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 11 22:40:46 sam-LIFEBOOK-S6410 udev-configure-printer: add /devices/pnp0/00:0b/printer/lp0
Aug 11 22:40:46 sam-LIFEBOOK-S6410 udev-configure-printer: Failed to get parent
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.944919] irda_init()
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.944933] NET: Registered protocol family 23
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.951750] found SMC SuperIO Chip (devid=0x7a rev=03 base=0x002e): LPC47N227
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.951775] smsc_superio_flat(): fir: 0x6e8, sir: 0x2e8, dma: 03, irq: 3, mode: 0x0e
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.951780] smsc_ircc_present: can't get sir_base of 0x2e8
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.968254] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x2e8-0x2ef 0x370-0x37f
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.970375] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3ff 0x4d0-0x4d7
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.971269] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.972839] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.973794] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xd3fff 0xe0000-0xfffff
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.973863] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.973933] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   16.974003] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.019556] Linux video capture interface: v2.00
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.041720] uvcvideo: Found UVC 1.00 device OEM Camera (046d:09b2)
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.051234] input: OEM Camera as /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0/input/input9
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.052225] usbcore: registered new interface driver uvcvideo
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.052228] USB Video Class driver (v1.0.0)
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.054682] Bluetooth: Core ver 2.15
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.054736] NET: Registered protocol family 31
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.054738] Bluetooth: HCI device and connection manager initialized
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.054741] Bluetooth: HCI socket layer initialized
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.077124] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.077127] iwlagn: Copyright(c) 2003-2010 Intel Corporation
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.077214] iwlagn 0000:0c:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.077224] iwlagn 0000:0c:00.0: setting latency timer to 64
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.077255] iwlagn 0000:0c:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.115733] iwlagn 0000:0c:00.0: device EEPROM VER=0x36, CALIB=0x5
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.115736] iwlagn 0000:0c:00.0: Device SKU: 0Xb
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.116680] Bluetooth: Generic Bluetooth USB driver ver 0.6
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.121093] usbcore: registered new interface driver btusb
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.136431] iwlagn 0000:0c:00.0: Tunable channels: 13 802.11bg, 19 802.11a channels
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.136519] iwlagn 0000:0c:00.0: irq 45 for MSI/MSI-X
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.137255] usbcore: registered new interface driver usbserial
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.137300] USB Serial support registered for generic
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.137898] usbcore: registered new interface driver usbserial_generic
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.137901] usbserial: USB Serial Driver core
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.141750] USB Serial support registered for Sierra USB modem
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.142050] sierra 7-1:1.0: Sierra USB modem converter detected
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.144891] usb 7-1: Sierra USB modem converter now attached to ttyUSB0
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.145079] usb 7-1: Sierra USB modem converter now attached to ttyUSB1
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.145261] usb 7-1: Sierra USB modem converter now attached to ttyUSB2
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.145911] usbcore: registered new interface driver sierra
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.145914] sierra: v.1.7.16:USB Driver for Sierra Wireless USB modems
Aug 11 22:40:46 sam-LIFEBOOK-S6410 bluetoothd[1218]: Bluetooth deamon 4.91
Aug 11 22:40:46 sam-LIFEBOOK-S6410 bluetoothd[1236]: Starting SDP server
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.172926] Bluetooth: L2CAP ver 2.15
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.172928] Bluetooth: L2CAP socket layer initialized
Aug 11 22:40:46 sam-LIFEBOOK-S6410 modem-manager[821]: <info>  (ttyUSB0) opening serial port...
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.190243] iwlagn 0000:0c:00.0: loaded firmware version 228.61.2.24
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:1c.2/0000:0c:00.0/ieee80211/phy0/rfkill1) (driver <unknown>)
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.190450] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.198430] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.198437] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.198455] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.198521] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.198555] HDA Intel 0000:00:1b.0: setting latency timer to 64
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.215106] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.215109] Bluetooth: BNEP filters: protocol multicast
Aug 11 22:40:46 sam-LIFEBOOK-S6410 modem-manager[821]: <info>  (ttyUSB1) opening serial port...
Aug 11 22:40:46 sam-LIFEBOOK-S6410 bluetoothd[1236]: Listening for HCI events on hci0
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]: <warn> bluez error getting default adapter: No such adapter
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.225435] Bluetooth: SCO (Voice Link) ver 0.6
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.225438] Bluetooth: SCO socket layer initialized
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.229456] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
Aug 11 22:40:46 sam-LIFEBOOK-S6410 modem-manager[821]: <info>  (ttyUSB2) opening serial port...
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlagn' ifindex: 3)
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (wlan0): now managed
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (wlan0): bringing up device.
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.271368] vboxdrv: Found 2 processor cores.
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.271507] vboxdrv: fAsync=0 offMin=0x208 offMax=0x802
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.271625] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.271628] vboxdrv: Successfully loaded version 4.1.0 (interface 0x00190000).
Aug 11 22:40:46 sam-LIFEBOOK-S6410 bluetoothd[1236]: HCI dev 0 up
Aug 11 22:40:46 sam-LIFEBOOK-S6410 bluetoothd[1236]: Adapter /org/bluez/1218/hci0 has been enabled
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.445665] Bluetooth: RFCOMM TTY layer initialized
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.445671] Bluetooth: RFCOMM socket layer initialized
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.445673] Bluetooth: RFCOMM ver 1.11
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (wlan0): preparing device.
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (wlan0): deactivating device (reason: 2).
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:0c:00.0/net/wlan0, iface: wlan0)
Aug 11 22:40:46 sam-LIFEBOOK-S6410 NetworkManager[761]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:0c:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.484155] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 11 22:40:46 sam-LIFEBOOK-S6410 kernel: [   17.500346] vboxpci: IOMMU not found (not registered)
Aug 11 22:40:47 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (wlan0): supplicant interface state:  starting -> ready
Aug 11 22:40:47 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (wlan0): device state change: 2 -> 3 (reason 42)
Aug 11 22:40:47 sam-LIFEBOOK-S6410 wpa_supplicant[913]: Failed to initiate AP scan.
Aug 11 22:40:47 sam-LIFEBOOK-S6410 kernel: [   18.370437] Intel AES-NI instructions are not detected.
Aug 11 22:40:47 sam-LIFEBOOK-S6410 kernel: [   18.395954] padlock_aes: VIA PadLock not detected.
Aug 11 22:40:47 sam-LIFEBOOK-S6410 kernel: [   18.429443] padlock_sha: VIA PadLock Hash Engine not detected.
Aug 11 22:40:47 sam-LIFEBOOK-S6410 modprobe: FATAL: Error inserting padlock_sha (/lib/modules/2.6.38-10-generic/kernel/drivers/crypto/padlock-sha.ko): No such device
Aug 11 22:40:48 sam-LIFEBOOK-S6410 init: anacron main process (972) killed by TERM signal
Aug 11 22:40:49 sam-LIFEBOOK-S6410 kernel: [   20.116384] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
Aug 11 22:40:49 sam-LIFEBOOK-S6410 kernel: [   20.432633] Adding 2086908k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:2086908k
Aug 11 22:40:50 sam-LIFEBOOK-S6410 gdm-session-worker[1655]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Aug 11 22:40:50 sam-LIFEBOOK-S6410 rtkit-daemon[1679]: Successfully called chroot.
Aug 11 22:40:50 sam-LIFEBOOK-S6410 rtkit-daemon[1679]: Successfully dropped privileges.
Aug 11 22:40:50 sam-LIFEBOOK-S6410 rtkit-daemon[1679]: Successfully limited resources.
Aug 11 22:40:50 sam-LIFEBOOK-S6410 rtkit-daemon[1679]: Running.
Aug 11 22:40:50 sam-LIFEBOOK-S6410 init: plymouth-stop pre-start process (1673) terminated with status 1
Aug 11 22:40:50 sam-LIFEBOOK-S6410 rtkit-daemon[1679]: Watchdog thread running.
Aug 11 22:40:50 sam-LIFEBOOK-S6410 rtkit-daemon[1679]: Canary thread running.
Aug 11 22:40:50 sam-LIFEBOOK-S6410 rtkit-daemon[1679]: Successfully made thread 1677 of process 1677 (n/a) owned by '106' high priority at nice level -11.
Aug 11 22:40:50 sam-LIFEBOOK-S6410 rtkit-daemon[1679]: Supervising 1 threads of 1 processes of 1 users.
Aug 11 22:40:50 sam-LIFEBOOK-S6410 rtkit-daemon[1679]: Successfully made thread 1701 of process 1677 (n/a) owned by '106' RT at priority 5.
Aug 11 22:40:50 sam-LIFEBOOK-S6410 rtkit-daemon[1679]: Supervising 2 threads of 1 processes of 1 users.
Aug 11 22:40:50 sam-LIFEBOOK-S6410 rtkit-daemon[1679]: Successfully made thread 1702 of process 1677 (n/a) owned by '106' RT at priority 5.
Aug 11 22:40:50 sam-LIFEBOOK-S6410 rtkit-daemon[1679]: Supervising 3 threads of 1 processes of 1 users.
Aug 11 22:40:51 sam-LIFEBOOK-S6410 gdm-simple-greeter[1654]: Gtk-WARNING: /build/buildd/gtk+2.0-2.24.4/gtk/gtkwidget.c:5687: widget not within a GtkWindow
Aug 11 22:40:51 sam-LIFEBOOK-S6410 kernel: [   22.399734] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
Aug 11 22:40:52 sam-LIFEBOOK-S6410 gdm-simple-greeter[1654]: WARNING: Unable to load CK history: no seat-id found
Aug 11 22:40:53 sam-LIFEBOOK-S6410 modem-manager[821]: <info>  (ttyUSB0) closing serial port...
Aug 11 22:40:54 sam-LIFEBOOK-S6410 modem-manager[821]: <info>  (ttyUSB0) serial port closed
Aug 11 22:40:54 sam-LIFEBOOK-S6410 modem-manager[821]: <info>  (Sierra): GSM modem /sys/devices/pci0000:00/0000:00:1d.2/usb7/7-1 claimed port ttyUSB0
Aug 11 22:40:54 sam-LIFEBOOK-S6410 modem-manager[821]: <info>  (ttyUSB2) closing serial port...
Aug 11 22:40:54 sam-LIFEBOOK-S6410 modem-manager[821]: <info>  (ttyUSB2) serial port closed
Aug 11 22:40:54 sam-LIFEBOOK-S6410 modem-manager[821]: <info>  (ttyUSB2) opening serial port...
Aug 11 22:40:54 sam-LIFEBOOK-S6410 modem-manager[821]: <info>  (Sierra): GSM modem /sys/devices/pci0000:00/0000:00:1d.2/usb7/7-1 claimed port ttyUSB2
Aug 11 22:41:00 sam-LIFEBOOK-S6410 modem-manager[821]: <info>  (ttyUSB1) closing serial port...
Aug 11 22:41:00 sam-LIFEBOOK-S6410 modem-manager[821]: <info>  (ttyUSB1) serial port closed
Aug 11 22:41:00 sam-LIFEBOOK-S6410 modem-manager[821]: <info>  (ttyUSB1) opening serial port...
Aug 11 22:41:01 sam-LIFEBOOK-S6410 modem-manager[821]: <info>  (ttyUSB2) closing serial port...
Aug 11 22:41:01 sam-LIFEBOOK-S6410 modem-manager[821]: <info>  (ttyUSB2) serial port closed
Aug 11 22:41:06 sam-LIFEBOOK-S6410 modem-manager[821]: <info>  (ttyUSB1) closing serial port...
Aug 11 22:41:06 sam-LIFEBOOK-S6410 modem-manager[821]: <info>  (ttyUSB1) serial port closed
Aug 11 22:41:06 sam-LIFEBOOK-S6410 NetworkManager[761]: <warn> (ttyUSB2): failed to look up interface index
Aug 11 22:41:06 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (ttyUSB2): new GSM device (driver: 'sierra' ifindex: -1)
Aug 11 22:41:06 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (ttyUSB2): exported as /org/freedesktop/NetworkManager/Devices/2
Aug 11 22:41:06 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (ttyUSB2): now managed
Aug 11 22:41:06 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (ttyUSB2): device state change: 1 -> 2 (reason 2)
Aug 11 22:41:06 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (ttyUSB2): deactivating device (reason: 2).
Aug 11 22:41:06 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (ttyUSB2): device state change: 2 -> 3 (reason 0)
Aug 11 22:41:57 sam-LIFEBOOK-S6410 gdm-session-worker[1655]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Aug 11 22:42:01 sam-LIFEBOOK-S6410 gdm-session-worker[1655]: pam_sm_authenticate: Called
Aug 11 22:42:01 sam-LIFEBOOK-S6410 gdm-session-worker[1655]: pam_sm_authenticate: username = [sam]
Aug 11 22:42:01 sam-LIFEBOOK-S6410 gdm-session-worker[1783]: Passphrase file wrapped
Aug 11 22:42:03 sam-LIFEBOOK-S6410 kernel: [   94.346936] ecryptfs_parse_options: eCryptfs: unrecognized option [ecryptfs_check_dev_ruid]
Aug 11 22:42:09 sam-LIFEBOOK-S6410 rtkit-daemon[1679]: Successfully made thread 1881 of process 1881 (n/a) owned by '1000' high priority at nice level -11.
Aug 11 22:42:09 sam-LIFEBOOK-S6410 rtkit-daemon[1679]: Supervising 4 threads of 2 processes of 2 users.
Aug 11 22:42:09 sam-LIFEBOOK-S6410 rtkit-daemon[1679]: Successfully made thread 1883 of process 1881 (n/a) owned by '1000' RT at priority 5.
Aug 11 22:42:09 sam-LIFEBOOK-S6410 rtkit-daemon[1679]: Supervising 5 threads of 2 processes of 2 users.
Aug 11 22:42:09 sam-LIFEBOOK-S6410 rtkit-daemon[1679]: Successfully made thread 1884 of process 1881 (n/a) owned by '1000' RT at priority 5.
Aug 11 22:42:09 sam-LIFEBOOK-S6410 rtkit-daemon[1679]: Supervising 6 threads of 2 processes of 2 users.
Aug 11 22:42:09 sam-LIFEBOOK-S6410 gnome-session[1813]: WARNING: Could not launch application 'tracker-miner-fs.desktop': Unable to start application: Failed to execute child process "/usr/lib/tracker/tracker-miner-fs" (No such file or directory)
Aug 11 22:42:09 sam-LIFEBOOK-S6410 gnome-session[1813]: WARNING: Could not launch application 'tracker-store.desktop': Unable to start application: Failed to execute child process "/usr/lib/tracker/tracker-store" (No such file or directory)
Aug 11 22:42:09 sam-LIFEBOOK-S6410 gnome-session[1813]: WARNING: Could not launch application 'mail-notification.desktop': Unable to start application: Failed to execute child process "mail-notification" (No such file or directory)
Aug 11 22:42:09 sam-LIFEBOOK-S6410 gnome-session[1813]: WARNING: Could not launch application 'gnome-do.desktop': Unable to start application: Failed to execute child process "gnome-do" (No such file or directory)
Aug 11 22:42:09 sam-LIFEBOOK-S6410 gnome-session[1813]: WARNING: Could not launch application 'Screenlets%20Daemon.desktop': Unable to start application: Failed to execute child process "/usr/share/screenlets-manager/screenlets-daemon.py" (No such file or directory)
Aug 11 22:42:09 sam-LIFEBOOK-S6410 gnome-session[1813]: WARNING: Could not launch application 'tracker-status-icon.desktop': Unable to start application: Failed to execute child process "tracker-status-icon" (No such file or directory)
Aug 11 22:42:12 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Activation (wlan0) starting connection 'Auto BTHomeHub-DFF5'
Aug 11 22:42:12 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Aug 11 22:42:12 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 11 22:42:12 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 11 22:42:12 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 11 22:42:12 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 11 22:42:12 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 11 22:42:12 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Aug 11 22:42:12 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Activation (wlan0/wireless): access point 'Auto BTHomeHub-DFF5' has security, but secrets are required.
Aug 11 22:42:12 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Aug 11 22:42:12 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 11 22:42:12 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 11 22:42:12 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 11 22:42:12 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Aug 11 22:42:12 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 11 22:42:12 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 11 22:42:12 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 11 22:42:12 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Aug 11 22:42:12 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Activation (wlan0/wireless): connection 'Auto BTHomeHub-DFF5' has security, and secrets exist.  No new secrets needed.
Aug 11 22:42:12 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Config: added 'ssid' value 'BTHomeHub-DFF5'
Aug 11 22:42:12 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Config: added 'scan_ssid' value '1'
Aug 11 22:42:12 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Config: added 'key_mgmt' value 'NONE'
Aug 11 22:42:12 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Config: added 'auth_alg' value 'OPEN'
Aug 11 22:42:12 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Config: added 'wep_key0' value '<omitted>'
Aug 11 22:42:12 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Config: added 'wep_tx_keyidx' value '0'
Aug 11 22:42:12 sam-LIFEBOOK-S6410 NetworkManager[761]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 11 22:42:12 sam-LIFEBOOK-S6410 NetworkManager[761]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 11 22:42:12 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 11 22:42:12 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Config: set interface ap_scan to 1
Aug 11 22:42:12 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (wlan0): supplicant connection state:  inactive -> scanning
Aug 11 22:42:14 sam-LIFEBOOK-S6410 wpa_supplicant[913]: Trying to associate with 00:18:f6:09:a7:4b (SSID='BTHomeHub-DFF5' freq=2442 MHz)
Aug 11 22:42:14 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (wlan0): supplicant connection state:  scanning -> associating
Aug 11 22:42:14 sam-LIFEBOOK-S6410 kernel: [  105.384922] wlan0: authenticate with 00:18:f6:09:a7:4b (try 1)
Aug 11 22:42:14 sam-LIFEBOOK-S6410 kernel: [  105.386713] wlan0: authenticated
Aug 11 22:42:14 sam-LIFEBOOK-S6410 kernel: [  105.386743] wlan0: associate with 00:18:f6:09:a7:4b (try 1)
Aug 11 22:42:14 sam-LIFEBOOK-S6410 kernel: [  105.389289] wlan0: RX AssocResp from 00:18:f6:09:a7:4b (capab=0x411 status=0 aid=4)
Aug 11 22:42:14 sam-LIFEBOOK-S6410 kernel: [  105.389293] wlan0: associated
Aug 11 22:42:14 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (wlan0): supplicant connection state:  associating -> associated
Aug 11 22:42:14 sam-LIFEBOOK-S6410 wpa_supplicant[913]: Associated with 00:18:f6:09:a7:4b
Aug 11 22:42:14 sam-LIFEBOOK-S6410 wpa_supplicant[913]: CTRL-EVENT-CONNECTED - Connection to 00:18:f6:09:a7:4b completed (auth) [id=0 id_str=]
Aug 11 22:42:14 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (wlan0): supplicant connection state:  associated -> completed
Aug 11 22:42:14 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'BTHomeHub-DFF5'.
Aug 11 22:42:14 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 11 22:42:14 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Aug 11 22:42:14 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Aug 11 22:42:14 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Aug 11 22:42:14 sam-LIFEBOOK-S6410 kernel: [  105.416130] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Aug 11 22:42:14 sam-LIFEBOOK-S6410 dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Aug 11 22:42:14 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> dhclient started with pid 1996
Aug 11 22:42:14 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Aug 11 22:42:14 sam-LIFEBOOK-S6410 dhclient: Copyright 2004-2010 Internet Systems Consortium.
Aug 11 22:42:14 sam-LIFEBOOK-S6410 dhclient: All rights reserved.
Aug 11 22:42:14 sam-LIFEBOOK-S6410 dhclient: For info, please visit https://www.isc.org/software/dhcp/
Aug 11 22:42:14 sam-LIFEBOOK-S6410 dhclient:
Aug 11 22:42:15 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Aug 11 22:42:15 sam-LIFEBOOK-S6410 dhclient: Listening on LPF/wlan0/00:1d:e0:67:05:1d
Aug 11 22:42:15 sam-LIFEBOOK-S6410 dhclient: Sending on   LPF/wlan0/00:1d:e0:67:05:1d
Aug 11 22:42:15 sam-LIFEBOOK-S6410 dhclient: Sending on   Socket/fallback
Aug 11 22:42:15 sam-LIFEBOOK-S6410 dhclient: DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
Aug 11 22:42:15 sam-LIFEBOOK-S6410 dhclient: DHCPACK of 192.168.1.65 from 192.168.1.254
Aug 11 22:42:15 sam-LIFEBOOK-S6410 dhclient: bound to 192.168.1.65 -- renewal in 40474 seconds.
Aug 11 22:42:15 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Aug 11 22:42:15 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Aug 11 22:42:15 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Aug 11 22:42:15 sam-LIFEBOOK-S6410 NetworkManager[761]: <info>   address 192.168.1.65
Aug 11 22:42:15 sam-LIFEBOOK-S6410 NetworkManager[761]: <info>   prefix 24 (255.255.255.0)
Aug 11 22:42:15 sam-LIFEBOOK-S6410 NetworkManager[761]: <info>   gateway 192.168.1.254
Aug 11 22:42:15 sam-LIFEBOOK-S6410 NetworkManager[761]: <info>   nameserver '192.168.1.254'
Aug 11 22:42:15 sam-LIFEBOOK-S6410 NetworkManager[761]: <info>   domain name 'home'
Aug 11 22:42:15 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Scheduling stage 5
Aug 11 22:42:15 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Aug 11 22:42:15 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Done scheduling stage 5
Aug 11 22:42:15 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Aug 11 22:42:15 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Aug 11 22:42:16 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> (wlan0): device state change: 7 -> 8 (reason 0)
Aug 11 22:42:16 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Policy set 'Auto BTHomeHub-DFF5' (wlan0) as default for IPv4 routing and DNS.
Aug 11 22:42:16 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Activation (wlan0) successful, device activated.
Aug 11 22:42:16 sam-LIFEBOOK-S6410 NetworkManager[761]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Aug 11 22:42:20 sam-LIFEBOOK-S6410 kernel: [  110.731619] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
Aug 11 22:42:24 sam-LIFEBOOK-S6410 ntpdate[2057]: adjust time server 91.189.94.4 offset 0.032753 sec
Aug 11 22:42:25 sam-LIFEBOOK-S6410 kernel: [  116.104041] wlan0: no IPv6 routers present
Aug 11 22:43:24 sam-LIFEBOOK-S6410 rtkit-daemon[1679]: Successfully made thread 2322 of process 2322 (n/a) owned by '1000' high priority at nice level -11.
Aug 11 22:43:24 sam-LIFEBOOK-S6410 rtkit-daemon[1679]: Supervising 1 threads of 1 processes of 1 users.
Aug 11 22:43:24 sam-LIFEBOOK-S6410 pulseaudio[2322]: pid.c: Stale PID file, overwriting.
Aug 11 22:43:24 sam-LIFEBOOK-S6410 rtkit-daemon[1679]: Successfully made thread 2323 of process 2322 (n/a) owned by '1000' RT at priority 5.
Aug 11 22:43:24 sam-LIFEBOOK-S6410 rtkit-daemon[1679]: Supervising 2 threads of 1 processes of 1 users.
Aug 11 22:43:24 sam-LIFEBOOK-S6410 rtkit-daemon[1679]: Successfully made thread 2324 of process 2322 (n/a) owned by '1000' RT at priority 5.
Aug 11 22:43:24 sam-LIFEBOOK-S6410 rtkit-daemon[1679]: Supervising 3 threads of 1 processes of 1 users.

```

---

### Post by samsanchez on 2011-08-11
(I should have written part 2 on that last printout)

---

### Post by Toz on 2011-08-11
That's interesting. I don't see anything in the logs about a suspend or hibernate. The fact that there is nothing in /var/log/pm-suspend.log is really odd.

Exactly what happens to the computer when you try to suspend? Does it turn off? Any error messages?

Can you try another suspend now, and when you re-gain control of the computer, post back again the requested information.

---

### Post by samsanchez on 2011-08-13
When I suspend (1) the screensaver starts (2) the screen goes black, but is still on (its a sort of 'backlit' black) and some lights flash above the keyboard (the caps-lock light and another one with a symbol of a padlock with up/down arrows on it). The laptop does not respond to the keyboard or mouse. (3) I have to switch off the laptop by holding down the off button.

---

### Post by Toz on 2011-08-13
> When I suspend (1)
How do you suspend? What menu item/action do you perform to initiate the suspend?

Open a terminal window, type in the following command (to manually suspend the computer), and let us know what happens:
```
sudo pm-suspend
```

Also, post back the contents of **/var/log/pm-suspend.log**

---

### Post by samsanchez on 2011-08-14
To suspend I press this icon [IMG]http://www.samfrances.com/offbutton.png[/IMG] and select 'Suspend'.

When I type 'sudo pm-suspend', the same thing happens as when I suspend using the [IMG]http://www.samfrances.com/offbutton.png[/IMG] menu.

 **/var/log/pm-suspend.log:**

```
Initial commandline parameters: 
Sat Aug 13 21:11:49 BST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux sam-LIFEBOOK-S6410 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686 i686 i386 GNU/Linux
Module                  Size  Used by
rfcomm                 38125  8 
binfmt_misc            13213  1 
sco                    17827  2 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
pci_stub               12550  1 
vboxpci                22892  0 
vboxnetadp             13348  0 
vboxnetflt             27225  0 
vboxdrv               251892  3 vboxpci,vboxnetadp,vboxnetflt
sha256_generic         20911  2 
cryptd                 19801  0 
aes_i586               16956  500 
aes_generic            38023  1 aes_i586
dm_crypt               22463  1 
joydev                 17322  0 
arc4                   12473  2 
snd_hda_codec_realtek   255882  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
iwlagn                284746  0 
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
sierra                 17992  0 
snd_seq_midi           13132  0 
usbserial              37116  1 sierra
btusb                  18160  2 
snd_rawmidi            25269  1 snd_seq_midi
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
iwlcore               148965  1 iwlagn
uvcvideo               66851  0 
mac80211              257001  2 iwlagn,iwlcore
videodev               75143  1 uvcvideo
snd_timer              28659  2 snd_pcm,snd_seq
pcmcia                 39671  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  12849  0 
irda                  185091  0 
psmouse                73312  0 
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              156212  3 iwlagn,iwlcore,mac80211
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
parport_pc             32111  1 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
crc_ccitt              12595  1 irda
serio_raw              12990  0 
fujitsu_laptop         18500  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
i915                  450934  4 
drm_kms_helper         40745  1 i915
firewire_ohci          31504  0 
drm                   180037  5 i915,drm_kms_helper
firewire_core          56138  1 firewire_ohci
sdhci_pci              13623  0 
ahci                   21591  2 
sdhci                  22720  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
i2c_algo_bit           13184  1 i915
libahci                25548  1 ahci
sky2                   49172  0 
video                  18951  1 i915
             total       used       free     shared    buffers     cached
Mem:       2051156    1307432     743724          0     392072     596572
-/+ buffers/cache:     318788    1732368
Swap:      2086908          0    2086908

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Sat Aug 13 21:11:54 BST 2011: performing suspend
Initial commandline parameters: 
Sat Aug 13 21:15:27 BST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux sam-LIFEBOOK-S6410 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686 i686 i386 GNU/Linux
Module                  Size  Used by
sha256_generic         20911  2 
cryptd                 19801  0 
aes_i586               16956  260 
aes_generic            38023  1 aes_i586
binfmt_misc            13213  1 
dm_crypt               22463  1 
pci_stub               12550  1 
vboxpci                22892  0 
vboxnetadp             13348  0 
vboxnetflt             27225  0 
rfcomm                 38125  8 
snd_hda_codec_realtek   255882  1 
sco                    17827  2 
vboxdrv               251892  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   17785  2 
snd_hda_intel          24140  2 
l2cap                  48656  16 rfcomm,bnep
sierra                 17992  0 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
arc4                   12473  2 
snd_hwdep              13274  1 snd_hda_codec
joydev                 17322  0 
usbserial              37116  1 sierra
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
btusb                  18160  2 
uvcvideo               66851  0 
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
videodev               75143  1 uvcvideo
iwlagn                284746  0 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
iwlcore               148965  1 iwlagn
snd_seq_midi_event     14475  1 snd_seq_midi
mac80211              257001  2 iwlagn,iwlcore
ppdev                  12849  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39671  0 
irda                  185091  0 
cfg80211              156212  3 iwlagn,iwlcore,mac80211
snd_timer              28659  2 snd_pcm,snd_seq
yenta_socket           27230  0 
crc_ccitt              12595  1 irda
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             32111  1 
psmouse                73312  0 
pcmcia_rsrc            18292  1 yenta_socket
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
fujitsu_laptop         18500  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
i915                  450934  4 
firewire_ohci          31504  0 
sdhci_pci              13623  0 
firewire_core          56138  1 firewire_ohci
sdhci                  22720  1 sdhci_pci
ahci                   21591  3 
crc_itu_t              12627  1 firewire_core
drm_kms_helper         40745  1 i915
drm                   180037  5 i915,drm_kms_helper
sky2                   49172  0 
libahci                25548  1 ahci
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
             total       used       free     shared    buffers     cached
Mem:       2051156     689376    1361780          0      69660     358268
-/+ buffers/cache:     261448    1789708
Swap:      2086908          0    2086908

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Sat Aug 13 21:15:34 BST 2011: performing suspend
Initial commandline parameters: 
Sun Aug 14 10:29:51 BST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux sam-LIFEBOOK-S6410 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686 i686 i386 GNU/Linux
Module                  Size  Used by
sha256_generic         20911  2 
cryptd                 19801  0 
aes_i586               16956  528 
aes_generic            38023  1 aes_i586
binfmt_misc            13213  1 
dm_crypt               22463  1 
pci_stub               12550  1 
vboxpci                22892  0 
vboxnetadp             13348  0 
vboxnetflt             27225  0 
rfcomm                 38125  8 
vboxdrv               251892  3 vboxpci,vboxnetadp,vboxnetflt
snd_hda_codec_realtek   255882  1 
sco                    17827  2 
sierra                 17992  0 
bnep                   17785  2 
usbserial              37116  1 sierra
l2cap                  48656  16 rfcomm,bnep
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
btusb                  18160  2 
snd_hwdep              13274  1 snd_hda_codec
arc4                   12473  2 
joydev                 17322  0 
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
uvcvideo               66851  0 
snd_rawmidi            25269  1 snd_seq_midi
videodev               75143  1 uvcvideo
iwlagn                284746  0 
snd_seq_midi_event     14475  1 snd_seq_midi
ppdev                  12849  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
iwlcore               148965  1 iwlagn
pcmcia                 39671  0 
irda                  185091  0 
snd_timer              28659  2 snd_pcm,snd_seq
mac80211              257001  2 iwlagn,iwlcore
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             32111  1 
yenta_socket           27230  0 
cfg80211              156212  3 iwlagn,iwlcore,mac80211
pcmcia_rsrc            18292  1 yenta_socket
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
crc_ccitt              12595  1 irda
psmouse                73312  0 
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
fujitsu_laptop         18500  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
i915                  450934  3 
drm_kms_helper         40745  1 i915
drm                   180037  4 i915,drm_kms_helper
firewire_ohci          31504  0 
ahci                   21591  2 
i2c_algo_bit           13184  1 i915
libahci                25548  1 ahci
sky2                   49172  0 
firewire_core          56138  1 firewire_ohci
sdhci_pci              13623  0 
sdhci                  22720  1 sdhci_pci
video                  18951  1 i915
crc_itu_t              12627  1 firewire_core
             total       used       free     shared    buffers     cached
Mem:       2051156    1485508     565648          0      74664     924672
-/+ buffers/cache:     486172    1564984
Swap:      2086908          0    2086908

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...method return sender=:1.7 -> dest=:1.65 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Sun Aug 14 10:30:01 BST 2011: performing suspend
```

---

### Post by Toz on 2011-08-14
I notice you are running virtual box. If you have upgraded to version 4.1, please have a look at this thread: [http://ubuntuforums.org/showthread.php?t=1822314]("http://ubuntuforums.org/showthread.php?t=1822314"). There is a bug with this version of virtualbox that is preventing suspend/hibernate.

Otherwise, post back contents of /var/log/syslog again.

---

### Post by samsanchez on 2011-08-16
Ok, but Ubuntu isn't running on Virtualbox. Its my host system that won't suspend, not a virtual machine. Is there a bug in VBox that prevents the *host *system from suspending?

---

### Post by Toz on 2011-08-16
Yes, the bug is with the host system. More specifically in the modules that are loaded that enable virtualbox to run.

---

