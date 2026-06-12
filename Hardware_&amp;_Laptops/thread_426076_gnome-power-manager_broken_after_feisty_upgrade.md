---
title: "gnome-power-manager broken after feisty upgrade"
date: 2007-04-28
forum: Hardware &amp; Laptops
---

### Post by lucads on 2007-04-28
I've got this problem after upgrading from Edgy 6.10 to Feisty 7.04 on my Dell Inspiron 6400/e1505 laptop: gnome-power-manager icon says grayed everytime, it does not recognize anymore when my laptop is powered on AC and when running on battey the power level is not diaplayed. In addition when the laptop lid is closed, the screen stays turned ON, preventing me to close the lid.

If I check ACPI module status it seems correctly running and on a typical session on battery power it correctly reports:

```

luca@lds:~$ acpi -V

     Battery 1: discharging, 59%, 02:01:45 remaining
     Thermal 1: ok, 38.0 degrees C
  AC Adapter 1: off-line

```

Instead, manually launching gnome-power manager right after the aforementioned command in the same power conditions, the icon is grayed and it does not recognise that laptop is powered on battery, instead it behaves like laptop is powered with AC cable and it reports:

```

luca@lds:~$ gnome-power-manager --verbose --no-daemon

[gpm_debug_init] gpm-debug.c:217 (10:09:57):     Verbose debugging enabled
[main] gpm-main.c:205 (10:09:57):        GNOME Power Manager 2.18.2
[gpm_proxy_connect] gpm-proxy.c:101 (10:09:57):  emitting proxy-status TRUE: org.freedesktop.Hal
[gpm_proxy_connect] gpm-proxy.c:101 (10:09:57):  emitting proxy-status TRUE: org.freedesktop.Hal
[gpm_ac_adapter_init] gpm-ac-adapter.c:234 (10:09:57):   No devices of capability ac_adapter
[gpm_control_init] gpm-control.c:863 (10:09:57):         Using a supressed policy timeout of 5 seconds
[gpm_refcount_add] gpm-refcount.c:101 (10:09:57):        refcount now: 1
[gpm_refcount_add] gpm-refcount.c:102 (10:09:57):        non zero, so sending REFCOUNT_ADDED
[gpm_power_refcount_added] gpm-power.c:138 (10:09:57):   Data is now not trusted
[gpm_hash_new_kind_cache] gpm-power.c:1727 (10:09:57):   creating cache
[gpm_hash_new_device_cache] gpm-power.c:1761 (10:09:57):         creating cache
[gpm_warning_init] gpm-warning.c:260 (10:09:57):         Using per-time notification policy
[gpm_proxy_connect] gpm-proxy.c:101 (10:09:57):  emitting proxy-status TRUE: org.freedesktop.Hal
[gpm_cpufreq_set_governor] gpm-cpufreq.c:191 (10:09:57):         Doing SetCPUFreqGovernor (ondemand)
[gpm_cpufreq_set_consider_nice] gpm-cpufreq.c:506 (10:09:57):    Doing SetCPUFreqConsiderNice (0)
[gpm_cpufreq_set_performance] gpm-cpufreq.c:126 (10:09:57):      Doing SetCPUFreqPerformance (85)
[gpm_proxy_connect] gpm-proxy.c:101 (10:09:57):  emitting proxy-status TRUE: org.gnome.ScreenSaver
[gpm_srv_backlight_sync_policy] gpm-srv-backlight.c:151 (10:09:57):      choosing sensible default
[gpm_srv_backlight_sync_policy] gpm-srv-backlight.c:153 (10:09:57):      laptop, so use GPM_DPMS_METHOD_OFF
[gpm_srv_backlight_sync_policy] gpm-srv-backlight.c:185 (10:09:57):      SRV_BACKLIGHT parameters 0 0 0, method '4'
[gpm_dpms_set_enabled] gpm-dpms.c:435 (10:09:57):        setting DPMS enabled: 1
[x11_sync_server_dpms_settings] gpm-dpms.c:130 (10:09:57):       Syncing DPMS settings enabled=1 timeouts=0 0 0
[x11_sync_server_dpms_settings] gpm-dpms.c:130 (10:09:57):       Syncing DPMS settings enabled=1 timeouts=0 0 0
[gpm_idle_set_check_cpu] gpm-idle.c:306 (10:09:57):      Setting the CPU load check to 0
[gpm_manager_init] gpm-manager.c:1564 (10:09:57):        creating new inhibit instance
[gpm_manager_init] gpm-manager.c:1575 (10:09:57):        creating new control instance
[gpm_manager_init] gpm-manager.c:1585 (10:09:57):        creating new tray icon
[gpm_manager_init] gpm-manager.c:1594 (10:09:57):        initialising info infrastructure
[gpm_hal_enable_power_save] gpm-hal.c:1414 (10:09:57):   Doing SetPowerSave (1)
[gpm_hal_enable_power_save] gpm-hal.c:1421 (10:09:57):   ERROR: No powersave method found
*** WARNING ***
[gpm_hal_enable_power_save] gpm-hal.c:1426 (10:09:57):   SetPowerSave failed!
[gpm_idle_set_system_timeout] gpm-idle.c:357 (10:09:57):         Setting system idle timeout: 0
[get_stock_id] gpm-tray-icon.c:680 (10:09:57):   Trying CRITICAL icon: primary, ups, mouse, keyboard
[get_stock_id] gpm-tray-icon.c:704 (10:09:57):   Trying CHARGING icon: primary, ups
[get_stock_id] gpm-tray-icon.c:721 (10:09:57):   Trying PRESENT icon: primary, ups
[get_stock_id] gpm-tray-icon.c:736 (10:09:57):   Using fallback
[gpm_tray_icon_sync] gpm-tray-icon.c:763 (10:09:57):     Going to use stock id: gpm-ac-adapter
[gpm_tray_icon_set_image_from_stock] gpm-tray-icon.c:155 (10:09:57):     emitting icon-changed gpm-ac-adapter
[gpm_tray_icon_set_image_from_stock] gpm-tray-icon.c:161 (10:09:57):     Setting icon to gpm-ac-adapter
[gpm_tray_icon_sync] gpm-tray-icon.c:773 (10:09:57):     emitting description-changed gpm-ac-adapter
[gpm_refcount_auto_decrement] gpm-refcount.c:75 (10:09:58):      zero, so sending REFCOUNT_ZERO
[gpm_power_refcount_zero] gpm-power.c:123 (10:09:58):    Data is now trusted
[get_stock_id] gpm-tray-icon.c:680 (10:09:58):   Trying CRITICAL icon: primary, ups, mouse, keyboard
[get_stock_id] gpm-tray-icon.c:704 (10:09:58):   Trying CHARGING icon: primary, ups
[get_stock_id] gpm-tray-icon.c:721 (10:09:58):   Trying PRESENT icon: primary, ups
[get_stock_id] gpm-tray-icon.c:736 (10:09:58):   Using fallback
[gpm_tray_icon_sync] gpm-tray-icon.c:763 (10:09:58):     Going to use stock id: gpm-ac-adapter
[gpm_tray_icon_set_image_from_stock] gpm-tray-icon.c:155 (10:09:58):     emitting icon-changed gpm-ac-adapter
[gpm_tray_icon_sync] gpm-tray-icon.c:773 (10:09:58):     emitting description-changed gpm-ac-adapter
[gpm_power_get_status_summary] gpm-power.c:1451 (10:09:58):      tooltip: Computer is running on AC power
[battery_status_changed_primary] gpm-manager.c:957 (10:09:58):   Laptop battery is not discharging

```

Here are my ACPI dmesg voices:

```

luca@lds:~$ dmesg |grep ACPI

[    0.000000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fc1d0
[    0.000000] ACPI: RSDT (v001 DELL    M07     0x27d70402 ASL  0x00000061) @ 0x7fed39cd
[    0.000000] ACPI: FADT (v001 DELL    M07     0x27d70402 ASL  0x00000061) @ 0x7fed4800
[    0.000000] ACPI: HPET (v001 DELL    M07     0x00000001 ASL  0x00000061) @ 0x7fed4f00
[    0.000000] ACPI: MADT (v001 DELL    M07     0x27d70402 ASL  0x00000047) @ 0x7fed5000
[    0.000000] ACPI: MCFG (v016 DELL    M07     0x27d70402 ASL  0x00000061) @ 0x7fed4fc0
[    0.000000] ACPI: SLIC (v001 DELL    M07     0x27d70402 ASL  0x00000061) @ 0x7fed509c
[    0.000000] ACPI: BOOT (v001 DELL    M07     0x27d70402 ASL  0x00000061) @ 0x7fed4bc0
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20050624) @ 0x7fed3a0d
[    0.000000] ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 INTL 0x20050624) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[   16.252534] ACPI: Core revision 20060707
[   16.268885] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[    0.072726] ACPI: bus type pci registered
[    0.127860] ACPI: Interpreter enabled
[    0.127863] ACPI: Using IOAPIC for interrupt routing
[    0.128660] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.128836] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[    0.141284] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.142524] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.161081] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *4
[    0.161311] ACPI: PCI Interrupt Link [LNKB] (IRQs *5 7)
[    0.161537] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
[    0.161764] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *3
[    0.161995] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.162225] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.162454] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.162684] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    0.163086] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.164126] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.164363] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.164718] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.165112] pnp: PnP ACPI init
[    0.195030] pnp: PnP ACPI: found 12 devices
[    0.195034] PnPBIOS: Disabled by ACPI PNP
[    0.195070] PCI: Using ACPI for IRQ routing
[    0.255297] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.255323] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.255351] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
[    1.378334] ACPI: (supports S0 S3 S4 S5)
[    2.592520] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]
[    2.592681] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]
[    2.592867] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.592871] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.593249] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[    2.593394] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Cst] [20060707]
[    2.593618] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.593623] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.328000] ACPI: Thermal Zone [THM] (46 C)
[    4.124000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 18
[    4.780000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 19
[    4.884000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 20
[    4.988000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 21
[    5.092000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 22
[    5.196000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 18
[    5.196000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 19
[    5.304000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 17
[   22.224000] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 23
[   22.244000] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   22.480000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 20
[   42.476000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   43.320000] ACPI: AC Adapter [AC] (off-line)
[   43.424000] ACPI: Battery Slot [BAT0] (battery present)
[   43.448000] ACPI: Lid Switch [LID]
[   43.456000] ACPI: Power Button (CM) [PBTN]
[   43.456000] ACPI: Sleep Button (CM) [SBTN]
[   44.016000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   44.020000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   44.020000] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)

```

Is there something I can do to fix this problem? Have you encountered this bug?

Thanks.

---

### Post by Hisstareia on 2007-06-10
I'm having the same problem. My Inspiron 1505 will not show battery charge and thinks it's on AC all the time. I can temporarily fix it by reinstalling hal and libhal through synaptic, but it breaks after reboot :(.

---

### Post by bojo42 on 2007-06-14
hi, there is a bug in the new kernel, for more information look at this bug look [[COLOR="Red"]here[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117773").

cheers for the next kernel update!:popcorn:

---

