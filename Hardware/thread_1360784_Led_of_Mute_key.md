---
title: "Led of Mute key"
date: 2009-12-21
forum: Hardware
---

### Post by palimmo on 2009-12-21
Hi!
The mute key of my new laptop works, but the red light, which should be on when mute is active, is always turned off.

Here much information:

```
~$ dmesg | grep -i led
[    0.000000] MTRR fixed ranges enabled:
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.001973] console [tty0] enabled
[    0.010000] CPU0: Thermal monitoring enabled (TM1)
[    0.010000] CPU1: Thermal monitoring enabled (TM1)
[    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.330087] ACPI: Interpreter enabled
[    0.357348] pci 0000:00:01.0: PME# disabled
[    0.357642] pci 0000:00:1a.7: PME# disabled
[    0.357733] pci 0000:00:1b.0: PME# disabled
[    0.357798] pci 0000:00:1c.0: PME# disabled
[    0.357865] pci 0000:00:1c.1: PME# disabled
[    0.357932] pci 0000:00:1c.2: PME# disabled
[    0.358369] pci 0000:00:1d.7: PME# disabled
[    0.358621] pci 0000:00:1f.2: PME# disabled
[    0.359183] pci 0000:02:00.0: PME# disabled
[    0.359383] pci 0000:03:00.0: PME# disabled
[    0.371453] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.410024] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.410036] NetLabel:  unlabeled traffic allowed by default
[    0.456516] AppArmor: AppArmor Filesystem Enabled
[    0.456595] pci 0000:00:1c.0:   IO window: disabled
[    0.456604] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.456610] pci 0000:00:1c.1:   IO window: disabled
[    0.456619] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.456624] pci 0000:00:1c.2:   IO window: disabled
[    0.456629] pci 0000:00:1c.2:   MEM window: disabled
[    0.456632] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.456638] pci 0000:00:1e.0:   IO window: disabled
[    0.456642] pci 0000:00:1e.0:   MEM window: disabled
[    0.456646] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.645238] audit: initializing netlink socket (disabled)
[    0.701741] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.703616] ahci: SSS flag set, parallel bus scan disabled
[    0.703649] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems 
[    0.817477] lo: Disabled Privacy Extensions
[    0.818565] PM: Resume from disk failed.
[    1.180329] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.930543] tg3 0000:02:00.0: wake-up capability disabled by ACPI
[    2.930552] tg3 0000:02:00.0: PME# disabled
[    5.432815] PM: Resume from disk failed.
[    5.443505] EXT4-fs (sda5): barriers enabled
[    5.457201] EXT4-fs (sda5): delayed allocation enabled
[    5.457204] EXT4-fs: file extents enabled
[    5.457489] EXT4-fs: mballoc enabled
[   15.141912] Registered led device: ath9k-phy0::radio
[   15.141929] Registered led device: ath9k-phy0::assoc
[   15.141945] Registered led device: ath9k-phy0::tx
[   15.141960] Registered led device: ath9k-phy0::rx
[   15.158595] tg3 0000:02:00.0: wake-up capability disabled by ACPI
[   15.158603] tg3 0000:02:00.0: PME# disabled

```

```
~$ find /sys -name *led*
/sys/devices/platform/i8042/serio0/input/input4/capabilities/led
/sys/devices/platform/i8042/serio1/input/input10/capabilities/led
/sys/devices/system/machinecheck/machinecheck0/cmci_disabled
/sys/devices/system/machinecheck/machinecheck1/cmci_disabled
/sys/devices/virtual/input/input3/capabilities/led
/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0/capabilities/led
/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:02/input/input5/capabilities/led
/sys/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1/capabilities/led
/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/capabilities/led
/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/input7/capabilities/led
/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/input8/capabilities/led
/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/input9/capabilities/led
/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/leds
/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input6/capabilities/led
/sys/class/leds
/sys/kernel/debug/ieee80211/phy0/statistics/failed_count
/sys/kernel/debug/ieee80211/phy0/stations/00:08:a1:a8:a4:0e/tx_retry_failed
/sys/kernel/debug/kprobes/enabled
/sys/kernel/debug/tracing/events/ext4/ext4_journalled_write_end
/sys/kernel/debug/tracing/tracing_enabled
/sys/module/libata/parameters/atapi_enabled
/sys/module/apparmor/parameters/enabled
/sys/module/video/parameters/brightness_switch_enabled
/sys/module/led_class

```

```
~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G98M [GeForce G 105M] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

```

Thanks!

---

### Post by palimmo on 2009-12-22
nothing? :(

---

