---
title: "Elantech touchpad frozen after resume from suspend"
date: 2017-09-26
forum: Hardware
---

### Post by martinr on 2017-09-26
When I resume my laptop from suspend then it seems to start at first, but then the screen is frozen and none of the input devices work. Open windows are displayed, but not even the caps-lock key works. The laptop is completely frozen. (Plugging in a USB flash drive does not open the file browser, so the laptop seems to be in a coma, but starts running hot after a while).

The laptop is an Acer 5500Z, with an i915 Intel graphics chipset.

I'm running Xubuntu 16.04.3 LTS with the latest updates:
Description:    Ubuntu 16.04.3 LTS
Release:        16.04
Codename:       xenial
Linux version 4.10.0-37-generic (buildd@lcy01-30) (gcc version 5.
4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.4)

This is what I found in syslog:
```

Sep 26 22:42:43 avalon kernel: [    3.246750] ------------[ cut here ]------------
Sep 26 22:42:43 avalon kernel: [    3.246854] WARNING: CPU: 0 PID: 115 at /build/linux-hwe-8msm5I/linux-hwe-4.10.0/drivers/gpu/drm/i915/intel_display.c:13568 intel_atomic_commit_tail+0xdd0/0xf10 [i915]
Sep 26 22:42:43 avalon kernel: [    3.246939] encoder's enabled state mismatch (expected 0, found 1)
Sep 26 22:42:43 avalon kernel: [    3.246940] Modules linked in: i915 i2c_algo_bit drm_kms_helper syscopyarea sysfillrect b44 sysimgblt fb_sys_fops psmouse ssb drm mii pata_acpi fjes video
Sep 26 22:42:43 avalon kernel: [    3.246958] CPU: 0 PID: 115 Comm: kworker/u2:4 Tainted: G S      W       4.10.0-35-generic #39~16.04.1-Ubuntu
Sep 26 22:42:43 avalon kernel: [    3.246960] Hardware name: Acer             Aspire 5500Z                    /Mimid, BIOS V2.90 05/19/2006
Sep 26 22:42:43 avalon kernel: [    3.246969] Workqueue: events_unbound async_run_entry_fn
Sep 26 22:42:43 avalon kernel: [    3.246971] Call Trace:
Sep 26 22:42:43 avalon kernel: [    3.246979]  dump_stack+0x58/0x79
Sep 26 22:42:43 avalon kernel: [    3.246982]  __warn+0xea/0x110
Sep 26 22:42:43 avalon kernel: [    3.247040]  ? intel_atomic_commit_tail+0xdd0/0xf10 [i915]
Sep 26 22:42:43 avalon kernel: [    3.247043]  warn_slowpath_fmt+0x46/0x60
Sep 26 22:42:43 avalon kernel: [    3.247101]  intel_atomic_commit_tail+0xdd0/0xf10 [i915]
Sep 26 22:42:43 avalon kernel: [    3.247159]  intel_atomic_commit+0x3a2/0x4d0 [i915]
Sep 26 22:42:43 avalon kernel: [    3.247216]  ? intel_plane_duplicate_state+0x21/0x40 [i915]
Sep 26 22:42:43 avalon kernel: [    3.247273]  ? intel_plane_duplicate_state+0x30/0x40 [i915]
Sep 26 22:42:43 avalon kernel: [    3.247311]  drm_atomic_commit+0x4b/0x60 [drm]
Sep 26 22:42:43 avalon kernel: [    3.247369]  intel_get_load_detect_pipe+0x4f7/0x740 [i915]
Sep 26 22:42:43 avalon kernel: [    3.247427]  intel_tv_detect+0x13a/0x600 [i915]
Sep 26 22:42:43 avalon kernel: [    3.247449]  ? drm_atomic_state_default_clear+0x153/0x190 [drm]
Sep 26 22:42:43 avalon kernel: [    3.247469]  drm_helper_probe_single_connector_modes+0x293/0x4e0 [drm_kms_helper]
Sep 26 22:42:43 avalon kernel: [    3.247480]  drm_setup_crtcs+0x6a/0x9f0 [drm_kms_helper]
Sep 26 22:42:43 avalon kernel: [    3.247483]  ? dequeue_entity+0xc3/0x500
Sep 26 22:42:43 avalon kernel: [    3.247493]  drm_fb_helper_initial_config+0x6a/0x3c0 [drm_kms_helper]
Sep 26 22:42:43 avalon kernel: [    3.247495]  ? set_next_entity+0xfa/0x250
Sep 26 22:42:43 avalon kernel: [    3.247499]  ? pick_next_task_fair+0x459/0x520
Sep 26 22:42:43 avalon kernel: [    3.247555]  intel_fbdev_initial_config+0x16/0x30 [i915]
Sep 26 22:42:43 avalon kernel: [    3.247558]  async_run_entry_fn+0x38/0x180
Sep 26 22:42:43 avalon kernel: [    3.247564]  ? __schedule+0x269/0x720
Sep 26 22:42:43 avalon kernel: [    3.247568]  process_one_work+0x121/0x400
Sep 26 22:42:43 avalon kernel: [    3.247570]  worker_thread+0x37/0x4b0
Sep 26 22:42:43 avalon kernel: [    3.247573]  kthread+0xdb/0x110
Sep 26 22:42:43 avalon kernel: [    3.247575]  ? process_one_work+0x400/0x400
Sep 26 22:42:43 avalon kernel: [    3.247577]  ? kthread_create_on_node+0x30/0x30
Sep 26 22:42:43 avalon kernel: [    3.247580]  ret_from_fork+0x21/0x2c
Sep 26 22:42:43 avalon kernel: [    3.247582] ---[ end trace f135efad69a7533d ]---
Sep 26 22:42:43 avalon kernel: [    3.247614] ------------[ cut here ]------------
Sep 26 22:42:43 avalon kernel: [    3.247673] WARNING: CPU: 0 PID: 115 at /build/linux-hwe-8msm5I/linux-hwe-4.10.0/drivers/gpu/drm/i915/intel_display.c:13576 intel_atomic_commit_tail+0xf04/0xf10 [i915]
Sep 26 22:42:43 avalon kernel: [    3.247674] encoder detached but still enabled on pipe B.
Sep 26 22:42:43 avalon kernel: [    3.247675] Modules linked in: i915 i2c_algo_bit drm_kms_helper syscopyarea sysfillrect b44 sysimgblt fb_sys_fops psmouse ssb drm mii pata_acpi fjes video
Sep 26 22:42:43 avalon kernel: [    3.247687] CPU: 0 PID: 115 Comm: kworker/u2:4 Tainted: G S      W       4.10.0-35-generic #39~16.04.1-Ubuntu
Sep 26 22:42:43 avalon kernel: [    3.247688] Hardware name: Acer             Aspire 5500Z                    /Mimid, BIOS V2.90 05/19/2006


```

Does anybody have an idea what can be wrong. I ran several previous versions of Ubuntu on the same laptop, without this problem.

Extra edit:
After thouroughly analyzing the logs, the following problem occurs:
During resume from suspend the ImPS/2 Elantech Touchpad is wrongly recognized as ETPS/2 Elantech Touchpad.
How can one fix this or implement a workaround?

---

### Post by ajgreeny on 2017-09-27
It will help us to know a lot more about the specs of your laptop which appears to be a relatively low spec machine with a maximum of 2GB ram.

Whilst this should be sufficient for Xubuntu, the machine came originally with either 256 or 512MB ram according to my findings and if you have not upgraded ram that may be the problem.

If you're not sure of the complete spec run ```
sudo lshw -short
``` and copy back here the output using **Code-Tags** for terminal output just as you did above.

---

### Post by martinr on 2017-09-27
Thanks for your reply.
Here are the hardware specs:
```

$ sudo lshw -short
H/W path        Device      Class          Description
======================================================
                            system         Aspire 5500Z
/0                          bus            Mimid
/0/0                        memory         84KiB BIOS
/0/4                        processor      Intel(R) Pentium(R) M processor 1.70GHz
/0/4/8                      memory         32KiB L1 cache
/0/4/9                      memory         2MiB L2 cache
/0/13                       memory         2GiB System Memory
/0/13/0                     memory         1GiB SODIMM DDR2 Synchronous 400 MHz (2,5 ns)
/0/13/1                     memory         1GiB SODIMM DDR Synchronous 400 MHz (2,5 ns)
/0/100                      bridge         Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
/0/100/2                    display        Mobile 915GM/GMS/910GML Express Graphics Controller
/0/100/2.1                  display        Mobile 915GM/GMS/910GML Express Graphics Controller
/0/100/1c                   bridge         82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
/0/100/1c.1                 bridge         82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2
/0/100/1d                   bus            82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
/0/100/1d/1     usb2        bus            UHCI Host Controller
/0/100/1d.1                 bus            82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
/0/100/1d.1/1   usb3        bus            UHCI Host Controller
/0/100/1d.2                 bus            82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
/0/100/1d.2/1   usb4        bus            UHCI Host Controller
/0/100/1d.3                 bus            82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
/0/100/1d.3/1   usb5        bus            UHCI Host Controller
/0/100/1d.7                 bus            82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
/0/100/1d.7/1   usb1        bus            EHCI Host Controller
/0/100/1e                   bridge         82801 Mobile PCI Bridge
/0/100/1e/1     eth0        network        BCM4401-B0 100Base-TX
/0/100/1e/2     wlp5s2      network        PRO/Wireless 2200BG [Calexico2] Network Connection
/0/100/1e/4                 bridge         CB1410 Cardbus Controller
/0/100/1e.2                 multimedia     82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
/0/100/1e.3                 communication  82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller
/0/100/1f                   bridge         82801FBM (ICH6M) LPC Interface Bridge
/0/100/1f.1                 storage        82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
/0/100/1f.3                 bus            82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
/0/1            scsi0       storage        
/0/1/0.0.0      /dev/sda    disk           80GB HTS421280H9AT00
/0/1/0.0.0/1    /dev/sda1   volume         3992MiB Windows FAT volume
/0/1/0.0.0/2    /dev/sda2   volume         18GiB Windows NTFS volume
/0/1/0.0.0/3    /dev/sda3   volume         4486MiB Windows FAT volume
/0/1/0.0.0/4    /dev/sda4   volume         47GiB Extended partition
/0/1/0.0.0/4/5  /dev/sda5   volume         2055MiB Linux swap / Solaris partition
/0/1/0.0.0/4/6  /dev/sda6   volume         4486MiB W95 FAT32 partition
/0/1/0.0.0/4/7  /dev/sda7   volume         22GiB W95 FAT32 partition
/0/1/0.0.0/4/8  /dev/sda8   volume         18GiB Linux filesystem partition
/0/1/0.1.0      /dev/cdrom  disk           DVD-RW DVR-K16RA
/0/1/0.1.0/0    /dev/cdrom  disk           
/0/1/0.1.0/0/1              volume         1276MiB Hidden HPFS/NTFS partition
/1                          power          *


```

Previously on the same hardware I ran:
Ubuntu Breezy 5.10 (I can't recall what boot options I had to use in order to get Breezy running, but it probably was noapic)
Ubuntu Dapper 6.06 LTS (with boot options: noapic and installation of 915resolution)
Ubuntu Hardy 8.04  LTS (with boot options: acpi=force)
Ubuntu Lucid 10.04  LTS
XUbuntu Precise 12.04 LTS

In all the previous versions suspend worked, I could even get hibernate to work.
For 5.10 and 6.04 the hardware was still rather new. Versions 10.04 ran out of the box and in version 12.04 I had a workaround for touchpad recognition problems, that doesn't work anymore in 16.04.

I also did a grep on acpi in dmesg:
```

$ dmesg |grep -i acpi
[    0.000000] BIOS-e820: [mem 0x000000007f7e0000-0x000000007f7fffbf] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000007f7fffc0-0x000000007f7fffff] ACPI NVS
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000E5010 000014 (v00 INSYDE)
[    0.000000] ACPI: RSDT 0x000000007F7F87AB 000038 (v01 INSYDE RSDT_000 00000100 ABCD 00010200)
[    0.000000] ACPI: FACP 0x000000007F7FFAC0 000074 (v01 INSYDE FACP_000 00000100 0000 00010200)
[    0.000000] ACPI: DSDT 0x000000007F7F8E10 006CA2 (v01 Acer   EFL50    00000001 INTL 02002036)
[    0.000000] ACPI: FACS 0x000000007F7FFFC0 000040
[    0.000000] ACPI: APIC 0x000000007F7FFB50 000066 (v01 STUPID MAPIC_00 30307830 ABCD 00010200)
[    0.000000] ACPI: MCFG 0x000000007F7FFBC0 00003C (v01 INSYDE MCFG_000 30303030 0000 30303030)
[    0.000000] ACPI: SSDT 0x000000007F7F89BB 0002B9 (v01 PmRef  Cpu0Ist  00003000 INTL 20030522)
[    0.000000] ACPI: SSDT 0x000000007F7F87E3 0001D8 (v01 PmRef  Cpu0Cst  00003001 INTL 20030522)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.008077] ACPI: Core revision 20160930
[    0.018028] ACPI: 3 ACPI AML tables successfully acquired and loaded
[    0.096281] PM: Registering ACPI NVS region [mem 0x7f7fffc0-0x7f7fffff] (64 bytes)
[    0.097517] ACPI: bus type PCI registered
[    0.097519] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.101271] ACPI: Added _OSI(Module Device)
[    0.101273] ACPI: Added _OSI(Processor Device)
[    0.101275] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.101276] ACPI: Added _OSI(Processor Aggregator Device)
[    0.106086] ACPI : EC: EC started
[    0.106088] ACPI : EC: interrupt blocked
[    0.106272] ACPI: \_SB_.PCI0.LPCB.EC0_: Used as first EC
[    0.106276] ACPI: \_SB_.PCI0.LPCB.EC0_: GPE=0x1d, EC_CMD/EC_SC=0x66, EC_DATA=0x62
[    0.106278] ACPI: \_SB_.PCI0.LPCB.EC0_: Used as boot DSDT EC to handle transactions
[    0.106279] ACPI: Interpreter enabled
[    0.106316] ACPI: (supports S0 S3 S4 S5)
[    0.106318] ACPI: Using IOAPIC for interrupt routing
[    0.106649] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.106658] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.109324] acpi PNP0C15:00: ACPI dock station (docks/bays count: 1)
[    0.177858] acpi LNXIOBAY:00: ACPI dock station (docks/bays count: 2)
[    0.179010] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.179017] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.179024] acpi PNP0A08:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[B][    0.180969] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.181252] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.181531] pci 0000:00:1d.1: System wakeup disabled by ACPI
[    0.181806] pci 0000:00:1d.2: System wakeup disabled by ACPI
[    0.182084] pci 0000:00:1d.3: System wakeup disabled by ACPI
[    0.182370] pci 0000:00:1d.7: System wakeup disabled by ACPI
[    0.183164] pci 0000:00:1e.3: System wakeup disabled by ACPI[/B]
[    0.183384] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.184325] acpiphp: Slot [1] registered
**[    0.184607] pci 0000:05:01.0: System wakeup disabled by ACPI**
[    0.186004] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.186103] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.186199] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.186295] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.186391] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.186487] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.186583] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.186679] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.216426] ACPI: Enabled 4 GPEs in block 00 to 1F
[    0.216498] ACPI : EC: interrupt unblocked
[    0.216508] ACPI : EC: event unblocked
[    0.216516] ACPI: \_SB_.PCI0.LPCB.EC0_: GPE=0x1d, EC_CMD/EC_SC=0x66, EC_DATA=0x62
[    0.216518] ACPI: \_SB_.PCI0.LPCB.EC0_: Used as boot DSDT EC to handle transactions and events
[    0.217207] ACPI: bus type USB registered
[    0.217486] PCI: Using ACPI for IRQ routing
[    0.241678] pnp: PnP ACPI init
[    0.241931] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.242352] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.242429] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.271103] pnp 00:03: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.271253] pnp 00:04: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.271311] pnp: PnP ACPI: found 5 devices
[    0.309404] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    1.565640] ACPI: AC Adapter [ACAD] (on-line)
[    1.565803] ACPI: Lid Switch [LID0]
[    1.565893] ACPI: Power Button [PWRB]
[    1.565987] ACPI: Sleep Button [SLPB]
[    1.566090] ACPI: Power Button [PWRF]
[    2.113134] ACPI: Battery Slot [BAT1] (battery present)
[    2.166227] acpi device:1f: hash matches
[    2.570565] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    3.106260] Modules linked in: i915 i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt b44 fb_sys_fops psmouse drm ssb pata_acpi mii video fjes
[    3.109710] Modules linked in: i915 i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt b44 fb_sys_fops psmouse drm ssb pata_acpi mii video fjes
... previous line many times repeated
[   13.301548] Modules linked in: parport_pc ppdev lp parport autofs4 i915 i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt b44 fb_sys_fops psmouse drm ssb pata_acpi mii video fjes
[   13.302528] Modules linked in: parport_pc ppdev lp parport autofs4 i915 i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt b44 fb_sys_fops psmouse drm ssb pata_acpi mii video fjes
... previous line many times repeated
[   26.953087] ACPI Warning: SystemIO range 0x0000000000001028-0x000000000000102F conflicts with OpRegion 0x0000000000001000-0x000000000000107F (\PMIO) (20160930/utaddress-247)
**[   26.953100] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver**
[   26.953103] ACPI Warning: SystemIO range 0x0000000000001330-0x000000000000133F conflicts with OpRegion 0x0000000000001300-0x000000000000133B (\GPIO) (20160930/utaddress-247)
[   26.953109] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   26.953110] ACPI Warning: SystemIO range 0x0000000000001300-0x000000000000132F conflicts with OpRegion 0x0000000000001300-0x000000000000133B (\GPIO) (20160930/utaddress-247)
[   26.953115] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver

```

---

### Post by martinr on 2017-09-28
I managed to get some logging in dmesg of a failed suspend with the boot option acpi=force:
```

[   56.823421] PM: Syncing filesystems ... done.
[   57.385791] PM: Preparing system for sleep (mem)
[   57.385976] Freezing user space processes ... (elapsed 0.001 seconds) done.
[   57.387426] Freezing remaining freezable tasks ... (elapsed 0.000 seconds) done.
[   57.388189] PM: Suspending system (mem)
[   57.388212] Suspending console(s) (use no_console_suspend to debug)
[   57.388512] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[   57.396779] ACPI : EC: event blocked
[   57.397217] wlp5s2: Going into suspend...
[   57.518209] sd 0:0:0:0: [sda] Stopping disk
[   57.912343] ipw2200: Firmware error detected.  Restarting.
[   57.952777] ipw2200: Unable to load ucode: -22
[   57.952785] ipw2200: Unable to load firmware: -22
[   57.952786] ipw2200: Failed to up device
[   57.977330] PM: suspend of devices complete after 588.929 msecs
[   57.996207] PM: late suspend of devices complete after 18.871 msecs
[   57.996399] ACPI : EC: interrupt blocked
[   57.996744] ehci-pci 0000:00:1d.7: System wakeup enabled by ACPI
[   57.996841] uhci_hcd 0000:00:1d.3: System wakeup enabled by ACPI
[   57.996900] uhci_hcd 0000:00:1d.2: System wakeup enabled by ACPI
[   57.996958] uhci_hcd 0000:00:1d.1: System wakeup enabled by ACPI
[   57.997015] uhci_hcd 0000:00:1d.0: System wakeup enabled by ACPI
[   58.016069] PM: noirq suspend of devices complete after 19.858 msecs
[   58.016566] ACPI: Preparing to enter system sleep state S3
[   58.018400] ACPI : EC: EC stopped
[   58.018401] PM: Saving platform NVS memory
[   58.018404] Disabling non-boot CPUs ...
[   58.018404] ACPI: Low-level resume complete
[   58.018404] ACPI : EC: EC started
[   58.018404] PM: Restoring platform NVS memory
[   58.018404] Force enabled HPET at resume
[   58.018404] Suspended for 7.652 seconds
[   58.018404] ACPI: Waking up from system sleep state S3
[   58.024166] uhci_hcd 0000:00:1d.0: System wakeup disabled by ACPI
[   58.024219] uhci_hcd 0000:00:1d.1: System wakeup disabled by ACPI
[   58.024270] uhci_hcd 0000:00:1d.2: System wakeup disabled by ACPI
[   58.024321] uhci_hcd 0000:00:1d.3: System wakeup disabled by ACPI
[   58.024636] ACPI : EC: interrupt unblocked
[   58.044160] ehci-pci 0000:00:1d.7: System wakeup disabled by ACPI
[   58.044195] PM: noirq resume of devices complete after 20.392 msecs
[   58.044436] PM: early resume of devices complete after 0.219 msecs
[   58.048059] usb usb2: root hub lost power or was reset
[   58.048094] usb usb3: root hub lost power or was reset
[   58.048127] usb usb4: root hub lost power or was reset
[   58.048159] usb usb5: root hub lost power or was reset
[   58.048241] wlp5s2: Coming out of suspend...
[   58.071104] ata2: port disabled--ignoring
[   58.071334] sd 0:0:0:0: [sda] Starting disk
[   58.071398] ACPI : button: The lid device is not compliant to SW_LID.
[   58.071418] ACPI : EC: event unblocked
[   58.107697] rtc_cmos 00:02: System wakeup disabled by ACPI
[   59.073664] PM: resume of devices complete after 1029.225 msecs
[   59.073824] PM: Finishing wakeup.
[   59.073825] Restarting tasks ... done.
[   59.914823] psmouse serio4: elantech: assuming hardware version 1 (with firmware version 0x020000)
[   59.942869] psmouse serio4: elantech: Synaptics capabilities query result 0x06, 0x02, 0x64.
**[   60.149548] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input21**
[   60.910651] ata1.01: ACPI cmd ef/03:0c:00:00:00:b0 (SET FEATURES) filtered out
[   60.910655] ata1.01: ACPI cmd ef/03:42:00:00:00:b0 (SET FEATURES) filtered out
[   60.932326] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[   60.932330] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
[   60.937592] ata1.00: configured for UDMA/100
[   60.942232] ata1.01: configured for UDMA/33
[   61.252273] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   61.268932] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   61.273892] IPv6: ADDRCONF(NETDEV_UP): wlp5s2: link is not ready
[   61.276226] IPv6: ADDRCONF(NETDEV_UP): wlp5s2: link is not ready
[   61.317924] IPv6: ADDRCONF(NETDEV_UP): wlp5s2: link is not ready
[   62.021848] IPv6: ADDRCONF(NETDEV_CHANGE): wlp5s2: link becomes ready
[   62.432104] Corrupted low memory at c000ffe0 (ffe0 phys) = 8ab70000
[   62.432112] Corrupted low memory at c000ffe8 (ffe8 phys) = f0003000
[   62.432114] Corrupted low memory at c000ffec (ffec phys) = 00001b42
[   62.432117] Corrupted low memory at c000fff0 (fff0 phys) = 1010022c
[   62.432119] Corrupted low memory at c000fff4 (fff4 phys) = 0000fffe
[   62.432122] Corrupted low memory at c000fff8 (fff8 phys) = 3000ffd2
[   62.432124] Corrupted low memory at c000fffc (fffc phys) = 1accf000
[   62.432127] ------------[ cut here ]------------
[   62.432138] WARNING: CPU: 0 PID: 3 at /build/linux-hwe-8msm5I/linux-hwe-4.10.0/arch/x86/kernel/check.c:141 check_for_bios_corruption.part.1+0x84/0xc0
[   62.432139] Memory corruption detected in low memory
[   62.432142] Modules linked in: joydev michael_mic arc4 lib80211_crypt_tkip lib80211_crypt_ccmp snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_seq_midi ipw2200 snd_seq_midi_event snd_rawmidi pcmcia libipw lib80211 snd_seq input_leds cfg80211 snd_seq_device snd_timer serio_raw yenta_socket pcmcia_rsrc lpc_ich snd pcmcia_core soundcore shpchp irda mac_hid parport_pc ppdev lp parport autofs4 i915 i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops b44 psmouse ssb drm pata_acpi mii video fjes
[   62.432190] CPU: 0 PID: 3 Comm: kworker/0:0 Tainted: G S      W       4.10.0-35-generic #39~16.04.1-Ubuntu
[   62.432192] Hardware name: Acer             Aspire 5500Z                    /Mimid, BIOS V2.90 05/19/2006
[   62.432195] Workqueue: events check_corruption
[   62.432198] Call Trace:
[   62.432206]  dump_stack+0x58/0x79
[   62.432210]  __warn+0xea/0x110
[   62.432213]  ? check_for_bios_corruption.part.1+0x84/0xc0
[   62.432215]  warn_slowpath_fmt+0x46/0x60
[   62.432218]  check_for_bios_corruption.part.1+0x84/0xc0
[   62.432220]  check_corruption+0x19/0x50
[   62.432225]  process_one_work+0x121/0x400
[   62.432227]  worker_thread+0x37/0x4b0
[   62.432230]  kthread+0xdb/0x110
[   62.432233]  ? process_one_work+0x400/0x400
[   62.432235]  ? kthread_create_on_node+0x30/0x30
[   62.432239]  ret_from_fork+0x21/0x2c
[   62.432242] ---[ end trace d295628751c8deaa ]---
[  378.848072] psmouse serio4: elantech: assuming hardware version 1 (with firmware version 0x020000)
[  378.875974] psmouse serio4: elantech: Synaptics capabilities query result 0x06, 0x02, 0x64.
[  379.066942] psmouse serio4: elantech: touchpad refuses to switch to absolute mode.
[  379.066956] psmouse serio4: elantech: failed to initialise registers.
[  379.066966] psmouse serio4: elantech: failed to put touchpad into absolute mode.
**[  379.944082] input: ImPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input26**

```

After wake-up the mouse didn't work and seemed to heavily interfere with keyboard interaction (took me minutes to open an xterm). Then I could reload the mouse module with:
```

sudo modprobe -r psmouse
sudo modprobe psmouse

```
I also added it to: /etc/pm/sleep.d/65_fixtouchpad :
```

#!/bin/sh
#
# 65_fixtouchpad: unload/reload psmouse module
# Workaround for:  The Elantech touchpad is frozen/unusable and interferes
#   with typing after a suspend/resume.

case "$1" in
   hibernate|suspend)
      modprobe -r psmouse
   ;;
   thaw|resume)
      modprobe psmouse
   ;;
   *) exit $NA
   ;;
esac

```

And added a 10 seconds delay to prevent a drm race condition which led to a failure in X in the past:
in /etc/init/lightdm.conf
add sleep 10 befor exec

None of the above helped the condition: 
After wake-up the mouse didn't work and seemed to heavily interfere with keyboard interaction.

---

### Post by martinr on 2017-09-30
Deep diving into the logs for troubleshooting. 
Hopefully I won't corrupt my disk too much by hard resetting my laptop in order to get out of the frozen states.

---

### Post by martinr on 2017-09-30
After resume from suspend moving the mouse via the built in touch pad causes exactly the same memory corruption each time:
```

(dmesg output:)
[ 4363.232085] Corrupted low memory at c000ffe0 (ffe0 phys) = 8ab70000
[ 4363.232093] Corrupted low memory at c000ffe8 (ffe8 phys) = f0003000
[ 4363.232096] Corrupted low memory at c000ffec (ffec phys) = 00001b42
[ 4363.232098] Corrupted low memory at c000fff0 (fff0 phys) = 1010022c
[ 4363.232101] Corrupted low memory at c000fff4 (fff4 phys) = 0000fffe
[ 4363.232103] Corrupted low memory at c000fff8 (fff8 phys) = 3000ffd2
[ 4363.232106] Corrupted low memory at c000fffc (fffc phys) = 1accf000

```
The mouse pointer does not move and heavily interferes with further keyboard input (or blocks it entirely).

When I do a:
```

$ sudo modprobe -r psmouse
$ sudo modprobe psmouse

```
then I get back control of the mouse and keyboard.

When I automate this into /etc/pm/sleep.d/65_fixtouchpad:
```

#!/bin/sh
#
# 65_fixtouchpad: unload/reload psmouse module
# Workaround for:  The Elantech touchpad is frozen/unusable and interferes
#   with typing after a suspend/resume.

case "$1" in
   hibernate|suspend)
      modprobe -r psmouse
   ;;
   thaw|resume)
      modprobe psmouse
   ;;
   *) exit $NA
   ;;
esac

```
then I can see it being executed at resume, but it does not fix the problem. The corruption still occurs:
```

(dmesg output:)
[ 6094.989746] PM: Finishing wakeup.
[ 6094.989748] Restarting tasks ... done.
[B][ 6095.854430] psmouse serio4: elantech: assuming hardware version 1 (with firmware version 0x020000)        (automated time doesn't fix it)
[ 6095.882908] psmouse serio4: elantech: Synaptics capabilities query result 0x06, 0x02, 0x64.[/B]
[ 6096.091386] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input47
[ 6096.818715] ata1.01: ACPI cmd ef/03:0c:00:00:00:b0 (SET FEATURES) filtered out
[ 6096.818726] ata1.01: ACPI cmd ef/03:42:00:00:00:b0 (SET FEATURES) filtered out
[ 6096.840353] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[ 6096.840363] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
[ 6096.845901] ata1.00: configured for UDMA/100
[ 6096.850832] ata1.01: configured for UDMA/33
[ 6097.065759] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 6097.072905] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 6097.093853] IPv6: ADDRCONF(NETDEV_UP): wlp5s2: link is not ready
[ 6097.095819] IPv6: ADDRCONF(NETDEV_UP): wlp5s2: link is not ready
[ 6097.185477] IPv6: ADDRCONF(NETDEV_UP): wlp5s2: link is not ready
[ 6097.983202] IPv6: ADDRCONF(NETDEV_CHANGE): wlp5s2: link becomes ready
[B][ 6144.992129] Corrupted low memory at c000ffe0 (ffe0 phys) = 8ab70000
[ 6144.992143] Corrupted low memory at c000ffe8 (ffe8 phys) = f0003000
[ 6144.992151] Corrupted low memory at c000ffec (ffec phys) = 00001b42
[ 6144.992158] Corrupted low memory at c000fff0 (fff0 phys) = 1010022c
[ 6144.992165] Corrupted low memory at c000fff4 (fff4 phys) = 0000fffe
[ 6144.992172] Corrupted low memory at c000fff8 (fff8 phys) = 3000ffd2
[ 6144.992179] Corrupted low memory at c000fffc (fffc phys) = 1accf000[/B]
[B][ 6171.861866] psmouse serio4: elantech: assuming hardware version 1 (with firmware version 0x020000)
[ 6171.890750] psmouse serio4: elantech: Synaptics capabilities query result 0x06, 0x02, 0x64.[/B]         (Second manual time fixes it)
[ 6172.081267] psmouse serio4: elantech: touchpad refuses to switch to absolute mode.
[ 6172.081280] psmouse serio4: elantech: failed to initialise registers.
[ 6172.081290] psmouse serio4: elantech: failed to put touchpad into absolute mode.
[ 6172.953631] input: ImPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input58

```
until I manually run:
```

$ sudo modprobe -r psmouse
$ sudo modprobe psmouse

```

In Xorg log I see the following problems:
```

This happens with the automatic fix:
[  4645.416] (II) AIGLX: Suspending AIGLX clients for VT switch
[  4664.954] (II) AIGLX: Resuming AIGLX clients after VT switch
[  4664.955] (II) intel(0): switch to mode 1280x800@60.0 on LVDS1 using pipe 1, position (0, 0), rotation normal, reflection none
[  6095.031] (II) config/udev: removing device ImPS/2 Elantech Touchpad
[  6095.033] (II) evdev: ImPS/2 Elantech Touchpad: Close
[  6095.033] (II) UnloadModule: "evdev"
[  6095.105] (II) AIGLX: Suspending AIGLX clients for VT switch
[  6096.120] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse0)
[  6096.120] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[  6096.145] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event6)
[  6096.145] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[  6096.145] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[  6096.145] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[  6096.145] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[  6096.145] (**) ETPS/2 Elantech Touchpad: always reports core events
[  6096.145] (**) Option "Device" "/dev/input/event6"
[  6096.146] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 32 - 544 (res 31)
[  6096.146] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 32 - 352 (res 31)
[  6096.146] (II) synaptics: ETPS/2 Elantech Touchpad: device does not report pressure, will use touch data.
[  6096.146] (II) synaptics: ETPS/2 Elantech Touchpad: device does not report finger width.
[  6096.146] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[  6096.146] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[  6096.146] (--) synaptics: ETPS/2 Elantech Touchpad: invalid pressure range.  defaulting to 0 - 255
[  6096.146] (--) synaptics: ETPS/2 Elantech Touchpad: invalid finger width range.  defaulting to 0 - 15
[  6096.146] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[  6096.146] (**) ETPS/2 Elantech Touchpad: always reports core events
[  6096.146] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input47/event6"
[  6096.146] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 11)
[  6096.146] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[  6096.146] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[  6096.146] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.332
[  6096.147] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[  6096.147] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[  6096.147] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[  6096.147] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[  6115.155] (II) AIGLX: Resuming AIGLX clients after VT switch
[  6115.155] (II) intel(0): switch to mode 1280x800@60.0 on LVDS1 using pipe 1, position (0, 0), rotation normal, reflection none
[  6115.662] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[  6171.007] (EE) ETPS/2 Elantech Touchpad: Read error 19
[  6171.007] (EE) ETPS/2 Elantech Touchpad: Read error 19
[  6171.007] (EE) ETPS/2 Elantech Touchpad: Read error 19
[  6171.008] (EE) ETPS/2 Elantech Touchpad: Read error 19
...

and this fixes it manually:
[  6171.030] (II) config/udev: removing device ETPS/2 Elantech Touchpad
[  6171.042] (II) UnloadModule: "synaptics"
[  6172.991] (II) config/udev: Adding input device ImPS/2 Elantech Touchpad (/dev/input/mouse0)
[  6172.991] (II) No input driver specified, ignoring this device.
[  6172.991] (II) This device may have been added with another device file.
[  6173.008] (II) config/udev: Adding input device ImPS/2 Elantech Touchpad (/dev/input/event6)
[  6173.008] (**) ImPS/2 Elantech Touchpad: Applying InputClass "evdev pointer catchall"
[  6173.008] (II) Using input driver 'evdev' for 'ImPS/2 Elantech Touchpad'
[  6173.008] (**) ImPS/2 Elantech Touchpad: always reports core events
[  6173.008] (**) evdev: ImPS/2 Elantech Touchpad: Device: "/dev/input/event6"

```

Furthermore I see the following difference between the bad and good situation in
$ cat /proc/bus/input/devices
```

BAD:
I: Bus=0011 Vendor=0002 **Product=000e** Version=0000
**N: Name="ETPS/2 Elantech Touchpad"**
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input73
U: Uniq=
H: Handlers=mouse0 event6 
B: PROP=1
B: EV=b
B: KEY=6420 0 30000 0 0 0 0 0 0 0 0
B: ABS=3


GOOD:
I: Bus=0011 Vendor=0002 **Product=0005** Version=0000
**N: Name="ImPS/2 Elantech Touchpad"**
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input71
U: Uniq=
H: Handlers=mouse0 event6 
B: PROP=1
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

```

It seems to be a faulty detection of the built in touch pad hardware.
Who knows what causes this an how I can fix it structurally?

---

### Post by martinr on 2017-10-01
There seems to be more to it than touchpad recognition.
I just resumed from suspend and did a manual 
```

sudo modprobe -r psmouse
sudo modprobe psmouse

```

I noticed in dmesg that firstly after resume the built-in touchpad is identifiew wrongly (by means of reloading the mouse driver in the /etc/pm/sleep.d/65_fixtouchpad script). Then the touchpad is identified again correctly after my manual procedure as described above. But after that I see corruption again:
```

(dmesg output:)
[14952.928612] ACPI: Preparing to enter system sleep state S3                (before suspend)
[14952.930418] ACPI : EC: EC stopped
[14952.930419] PM: Saving platform NVS memory
[14952.930422] Disabling non-boot CPUs ...
[14952.930422] ACPI: Low-level resume complete                                     (start of resume)
[14952.930422] ACPI : EC: EC started
[14952.930422] PM: Restoring platform NVS memory
[14952.930422] Force enabled HPET at resume
[14952.930422] Suspended for 35239.389 seconds
[14952.930422] ACPI: Waking up from system sleep state S3
[14952.936177] uhci_hcd 0000:00:1d.0: System wakeup disabled by ACPI
[14952.936230] uhci_hcd 0000:00:1d.1: System wakeup disabled by ACPI
[14952.936281] uhci_hcd 0000:00:1d.2: System wakeup disabled by ACPI
[14952.936333] uhci_hcd 0000:00:1d.3: System wakeup disabled by ACPI
[14952.936649] ACPI : EC: interrupt unblocked
[14952.956155] ehci-pci 0000:00:1d.7: System wakeup disabled by ACPI
[14952.956195] PM: noirq resume of devices complete after 20.384 msecs
[14952.956438] PM: early resume of devices complete after 0.222 msecs
[14952.960300] usb usb2: root hub lost power or was reset
[14952.960335] usb usb3: root hub lost power or was reset
[14952.960368] usb usb4: root hub lost power or was reset
[14952.960400] usb usb5: root hub lost power or was reset
[14952.960482] wlp5s2: Coming out of suspend...
[14952.983321] ata2: port disabled--ignoring
[14952.983555] sd 0:0:0:0: [sda] Starting disk
[14952.983647] ACPI : EC: event unblocked
[14953.082002] rtc_cmos 00:02: System wakeup disabled by ACPI
[14953.985511] PM: resume of devices complete after 1029.068 msecs
[14953.985656] PM: Finishing wakeup.
[14953.985658] Restarting tasks ... done.
[14954.861432] psmouse serio4: elantech: assuming hardware version 1 (with firmware version 0x020000)
[14954.889342] psmouse serio4: elantech: Synaptics capabilities query result 0x06, 0x02, 0x64.
**[14955.096122] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input104**        (by /etc/pm/sleep.d/65_fixtouchpad)
[14955.762873] ata1.01: ACPI cmd ef/03:0c:00:00:00:b0 (SET FEATURES) filtered out
[14955.762885] ata1.01: ACPI cmd ef/03:42:00:00:00:b0 (SET FEATURES) filtered out
[14955.784367] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[14955.784377] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
[14955.789772] ata1.00: configured for UDMA/100
[14955.794827] ata1.01: configured for UDMA/33
[14956.210421] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[14956.222501] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[14956.245786] IPv6: ADDRCONF(NETDEV_UP): wlp5s2: link is not ready
[14956.249147] IPv6: ADDRCONF(NETDEV_UP): wlp5s2: link is not ready
[14956.324333] IPv6: ADDRCONF(NETDEV_UP): wlp5s2: link is not ready
[14957.085748] IPv6: ADDRCONF(NETDEV_CHANGE): wlp5s2: link becomes ready
[14981.342534] psmouse serio4: elantech: assuming hardware version 1 (with firmware version 0x020000)
[14981.370920] psmouse serio4: elantech: Synaptics capabilities query result 0x06, 0x02, 0x64.
[14981.561508] psmouse serio4: elantech: touchpad refuses to switch to absolute mode.
[14981.561521] psmouse serio4: elantech: failed to initialise registers.
[14981.561530] psmouse serio4: elantech: failed to put touchpad into absolute mode.
[B][14982.436092] input: ImPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input115                      (manual reloading of mouse module, correct detection)
[14992.352135] Corrupted low memory at c000ffe0 (ffe0 phys) = 8ab70000                                                             (Still corruption afterwards)
[14992.352148] Corrupted low memory at c000ffe8 (ffe8 phys) = f0003000
[14992.352156] Corrupted low memory at c000ffec (ffec phys) = 00001b42
[14992.352163] Corrupted low memory at c000fff0 (fff0 phys) = 1010022c
[14992.352171] Corrupted low memory at c000fff4 (fff4 phys) = 0000fffe
[14992.352178] Corrupted low memory at c000fff8 (fff8 phys) = 3000ffd2
[14992.352185] Corrupted low memory at c000fffc (fffc phys) = 1accf000[/B]

```

What the heck is going wrong?

---

### Post by martinr on 2017-10-02
Is there an Xorg expert in the house that can have a look at the touchpad / mouse driver logging from above?

---

### Post by martinr on 2017-10-04
Would it be possible to make a hardcoded Xorg config file to correct the detection problem after resume from suspend?

Currently I find the following:
```

/usr/share/X11/xorg.conf.d$ ls
10-amdgpu.conf  10-radeon.conf            51-synaptics-quirks.conf
10-evdev.conf   11-evdev-quirks.conf      70-synaptics.conf

```

With the following contents:
```

/usr/share/X11/xorg.conf.d$ more * | cat
::::::::::::::
10-amdgpu.conf
::::::::::::::
Section "OutputClass"
	Identifier "AMDgpu"
	MatchDriver "amdgpu"
	Driver "amdgpu"
EndSection::::::::::::::
10-evdev.conf
::::::::::::::
#
# Catch-all evdev loader for udev-based systems
# We don't simply match on any device since that also adds accelerometers
# and other devices that we don't really want to use. The list below
# matches everything but joysticks.

Section "InputClass"
        Identifier "evdev pointer catchall"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev keyboard catchall"
        MatchIsKeyboard "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchpad catchall"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev tablet catchall"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection
::::::::::::::
10-quirks.conf
::::::::::::::
# Collection of quirks and blacklist/whitelists for specific devices.


# Accelerometer device, posts data through ABS_X/ABS_Y, making X unusable
# http://bugs.freedesktop.org/show_bug.cgi?id=22442 
Section "InputClass"
        Identifier "ThinkPad HDAPS accelerometer blacklist"
        MatchProduct "ThinkPad HDAPS accelerometer data"
        Option "Ignore" "on"
EndSection

# https://bugzilla.redhat.com/show_bug.cgi?id=523914
# Mouse does not move in PV Xen guest
# Explicitly tell evdev to not ignore the absolute axes.
Section "InputClass"
        Identifier "Xen Virtual Pointer axis blacklist"
        MatchProduct "Xen Virtual Pointer"
        Option "IgnoreAbsoluteAxes" "off"
        Option "IgnoreRelativeAxes" "off"
EndSection

# https://bugs.freedesktop.org/show_bug.cgi?id=55867
# Bug 55867 - Doesn't know how to tag XI_TRACKBALL
Section "InputClass"
        Identifier "Tag trackballs as XI_TRACKBALL"
        MatchProduct "trackball"
        MatchDriver "evdev"
        Option "TypeName" "TRACKBALL"
EndSection

# https://bugs.freedesktop.org/show_bug.cgi?id=62831
# Bug 62831 - Mionix Naos 5000 mouse detected incorrectly
Section "InputClass"
        Identifier "Tag Mionix Naos 5000 mouse XI_MOUSE"
        MatchProduct "La-VIEW Technology Naos 5000 Mouse"
        MatchDriver "evdev"
        Option "TypeName" "MOUSE"
EndSection
::::::::::::::
10-radeon.conf
::::::::::::::
Section "OutputClass"
	Identifier "Radeon"
	MatchDriver "radeon"
	Driver "radeon"
EndSection::::::::::::::
11-evdev-quirks.conf
::::::::::::::
Section "InputClass"
	Identifier "Avago Technologies mouse quirks (LP: #746639)"
	MatchIsPointer "on"
	MatchDevicePath "/dev/input/event*"
	Driver "evdev"
	MatchUSBID "192f:0416"
	Option "Emulate3Buttons" "True"
	Option "Emulate3Timeout" "50"
EndSection

# X/Y axis not working due to device reporting absolute axes
# https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/325581
# https://bugs.freedesktop.org/show_bug.cgi?id=32882
Section "InputClass"
	Identifier	"Benq m310"
	MatchProduct	"HID 0d62:1000"
	Driver		"evdev"
	Option		"IgnoreAbsoluteAxes"	"true"
EndSection
::::::::::::::
11-evdev-trackpoint.conf
::::::::::::::
# trackpoint users want wheel emulation

Section "InputClass"
	Identifier	"trackpoint catchall"
	MatchIsPointer	"true"
	MatchProduct	"TrackPoint|DualPoint Stick"
	MatchDevicePath	"/dev/input/event*"
	Option	"Emulate3Buttons"	"true"
	Option	"EmulateWheel"	"true"
	Option	"EmulateWheelButton"	"2"
	Option	"XAxisMapping"	"6 7"
	Option	"YAxisMapping"	"4 5"
EndSection
::::::::::::::
51-synaptics-quirks.conf
::::::::::::::
Section "InputClass"
	Identifier "Dell Inspiron embedded buttons quirks"
	MatchTag "inspiron_1011|inspiron_1012"
	MatchDevicePath "/dev/input/event*"
	Driver "synaptics"
	Option "JumpyCursorThreshold" "90"
EndSection

Section "InputClass"
	Identifier "Dell Inspiron quirks"
	MatchTag "inspiron_1120"
	MatchDevicePath "/dev/input/event*"
	Driver "synaptics"
	Option "JumpyCursorThreshold" "250"
EndSection

Section "InputClass"
	Identifier "HP Mininote quirks"
	MatchTag "mininote_1000"
	MatchDevicePath "/dev/input/event*"
	Driver "synaptics"
	Option "JumpyCursorThreshold" "20"
EndSection
::::::::::::::
70-synaptics.conf
::::::::::::::
# Example xorg.conf.d snippet that assigns the touchpad driver
# to all touchpads. See xorg.conf.d(5) for more information on
# InputClass.
# DO NOT EDIT THIS FILE, your distribution will likely overwrite
# it when updating. Copy (and rename) this file into
# /etc/X11/xorg.conf.d first.
# Additional options may be added in the form of
#   Option "OptionName" "value"
#
Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
# This option is recommend on all Linux systems using evdev, but cannot be
# enabled by default. See the following link for details:
# http://who-t.blogspot.com/2010/11/how-to-ignore-configuration-errors.html
      MatchDevicePath "/dev/input/event*"
EndSection

Section "InputClass"
        Identifier "touchpad ignore duplicates"
        MatchIsTouchpad "on"
        MatchOS "Linux"
        MatchDevicePath "/dev/input/mouse*"
        Option "Ignore" "on"
EndSection

# This option enables the bottom right corner to be a right button on clickpads
# and the right and middle top areas to be right / middle buttons on clickpads
# with a top button area.
# This option is only interpreted by clickpads.
Section "InputClass"
        Identifier "Default clickpad buttons"
        MatchDriver "synaptics"
        Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
        Option "SecondarySoftButtonAreas" "58% 0 0 15% 42% 58% 0 15%"
EndSection

# This option disables software buttons on Apple touchpads.
# This option is only interpreted by clickpads.
Section "InputClass"
        Identifier "Disable clickpad buttons on Apple touchpads"
        MatchProduct "Apple|bcm5974"
        MatchDriver "synaptics"
        Option "SoftButtonAreas" "0 0 0 0 0 0 0 0"
EndSection
::::::::::::::
70-wacom.conf
::::::::::::::
# Some of the below input classes appear 3x times, once for each of
# "tablet", "touchscreen", and "touchpad" to ensure that the Wacom
# driver is not accidentally bound to other types of hardware that
# Wacom has made which are not handled by the wacom driver (e.g the
# Wacom Bluetooth Keyboard)
#
# https://sourceforge.net/p/linuxwacom/bugs/294/

Section "InputClass"
        Identifier "Wacom USB tablet class"
        MatchUSBID "056a:*"
        MatchDevicePath "/dev/input/event*"
        MatchIsTablet "true"
        Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom USB touchscreen class"
        MatchUSBID "056a:*"
        MatchDevicePath "/dev/input/event*"
        MatchIsTouchscreen "true"
        Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom USB touchpad class"
        MatchUSBID "056a:*"
        MatchDevicePath "/dev/input/event*"
        MatchIsTouchpad "true"
        Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom tablet class"
	MatchProduct "Wacom|WACOM|PTK-540WL|ISD-V4"
	MatchDevicePath "/dev/input/event*"
	MatchIsTablet "true"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom touchscreen class"
	MatchProduct "Wacom|WACOM|PTK-540WL|ISD-V4"
	MatchDevicePath "/dev/input/event*"
	MatchIsTouchscreen "true"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom touchpad class"
	MatchProduct "Wacom|WACOM|PTK-540WL|ISD-V4"
	MatchDevicePath "/dev/input/event*"
	MatchIsTouchpad "true"
	Driver "wacom"
EndSection

# Serial Wacom devices should always be one of tablet, touchscreen, or
# touchpad so we can safely get away with just one match section in
# these cases
Section "InputClass"
        Identifier "Wacom PnP device class"
        MatchPnPID "WACf*|WCOM*|WACM*|FUJ02e5|FUJ02e7|FUJ02e9"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
        Driver "wacom"
EndSection

# Hanwang tablets
Section "InputClass"
	Identifier "Hanwang class"
	MatchProduct "Hanwang"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

# Waltop tablets
Section "InputClass"
	Identifier "Waltop class"
	MatchProduct "WALTOP"
	MatchIsTablet "on"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001|N-Trig Pen|N-Trig DuoSense"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "Button2" "3"
EndSection
martinr@avalon:/usr/share/X11/xorg.conf.d$ 

```

---

### Post by martinr on 2017-10-07
Where can I find the XUbuntu Xorg experts?

---

### Post by mörgæs on 2017-10-07
I guess there are only few of them left. 
Xorg.conf is not part of a standard Buntu install any more.

The output shows memory errors. Have you tried running **memtest** from the boot menu?

---

### Post by martinr on 2017-10-08
Hi  mörgæs,

Mem test does all-right (see attached pic, btw Do you reckon that I could upp the CAS timings?).

XUbuntu comes with Xorg (who maintains the pasted configs from [above]("https://ubuntuforums.org/showthread.php?t=2372591&p=13694044#post13694044")?)

There seems to be a fault in hardware detection at resume from suspend. The built-in touchpad hardware is wrongly detected at resume (but not at initial boot time).

---

### Post by mörgæs on 2017-10-08
> **martinr said:**
> Do you reckon that I could upp the CAS timings?

One thing at a time. I recommend that you set all BIOS settings to default until the other problems are solved.


> **martinr said:**
> 
XUbuntu comes with Xorg 

Yes but not with xorg.conf.


> **martinr said:**
> 
There seems to be a fault in hardware detection at resume from suspend.  The built-in touchpad hardware is wrongly detected at resume (but not at  initial boot time).

Have you tried 17.04 to see if there is any difference here?

---

### Post by martinr on 2017-10-08
Hi mörgæs,

Thanks for your reply.

> **mörgæs said:**
> One thing at a time. I recommend that you set all BIOS settings to default until the other problems are solved.

Agree, nothing has been changed to the bios settings. With the same settings [the previous *buntu versions]("https://ubuntuforums.org/showthread.php?t=2372591&p=13691064#post13691064") also ran on the same hardware.

> **mörgæs said:**
> 
Yes but not with xorg.conf.

Not the complete xorg.conf, but the partial Xorg conf files from /usr/share/X11/xorg.conf.d ([see this previous posting]("https://ubuntuforums.org/showthread.php?t=2372591&p=13694044#post13694044")) are included in the LTS version and are related to touchpad recognition. Especially 70-synaptics.conf.

> Have you tried 17.04 to see if there is any difference here?
Not yet, I will download a live CD and try it out. I am however very fond of the LTS versions, because this is my main rig I would prefer it to run a stable and long lasting version of XUbuntu.

---

### Post by martinr on 2017-10-09
> **mörgæs said:**
> 
Have you tried 17.04 to see if there is any difference here?
I wasted a DVD in order to test 17.04 and the same problems persist.
I tested with the XUbuntu 17.04 live DVD 
and also tested it with the XUbuntu 16.04.2 live DVD.

I've attached both dmesg outputs at the resume from suspend moment until the touchpad freezing the system to this posting.

---

### Post by mörgæs on 2017-10-09
It's certainly not a waste to try various releases. It should be the first test to do.

Running low on ideas. Is the BIOS updated?

---

### Post by martinr on 2017-10-09
> **mörgæs said:**
> Running low on ideas. Is the BIOS updated?

The BIOS is as patched as it'll ever get. No new updates come out any more. Heck it worked with Buntus 5 - 12.

Doing:
```
sudo modprobe -r psmouse
sudo modprobe psmouse

```
fixes the problem. Automating this doesn't work and I don't understand why. There might be a race condition. (I suspect more race conditions were introduced by the seemingly half way transition to upstart.)

The core of the problem seems to me to be in faulty touchpad hardware detection. There is some sort of a fix related to psmouse in the Xorg conf files in the distribution, but I'm unfamiliar with quirck / Xorg config snippets and the attempted fix.

Who knows how to hardcode a touchpad into a Xorg quirck file? Maybe that can fix it. Or find a way to beat the race condition to automate modprobe in order to fix it.

I'm not the only one that is experiencing these problems (see [here]("https://ubuntuforums.org/showthread.php?t=2373653") and [here]("https://ubuntuforums.org/showthread.php?t=2327156&highlight=ETPS%2F2+ImPS%2F2"), and [here]("https://unix.stackexchange.com/questions/334785/touchpad-unresponsive-on-resume-from-sleep-on-debian-8")), but they're kind of hard to diagnose and fix if you're not a Buntu half god.

---

### Post by martinr on 2017-10-18
I just found out that *Buntu 16.04 is the first LTS version that switched from upstart to systemD. The old System V style intit was never even completely transferred. I noticed it by accident, because I couldn't stop a service from auto-starting.

This makes systemD to me the number one suspect for the root cause of not recognizing the touch-pad correctly after suspend (at boot time it is recognized correctly).

I suspect another race condition. How can I build in a 10 second delay SystemD style (analogous to the above mentioned script)?

---

### Post by martinr on 2017-10-20
Summarizing dmesg:
The problem is that the touchpad hardware is wrongly recognized after resume from suspend as:
```

[  138.604118] input: **ETPS/2** Elantech Touchpad as /devices/platform/i8042/serio4/input/input21

```
After doing:
```

sudo modprobe -r psmouse
sudo modprobe psmouse

```
It is correctly recognized as:
```

[  190.562132] input: **ImPS/2** Elantech Touchpad as /devices/platform/i8042/serio4/input/input26

```
And things work again.

Who knows how to fix this permanently?

---

### Post by martinr on 2017-10-24
I see stack traces in dmesg:
```
/build/linux-hwe-JBRI_s/linux-hwe-4.10.0/drivers/gpu/drm/drm_atomic_helper.c:784 drm_atomic_helper_update_legacy_modeset_state [drm_kms_helper]
[   13.621447] Workqueue: events output_poll_execute [drm_kms_helper]
```

And in the stack trace:

```
[   13.621464]  ? drm_atomic_helper_update_legacy_modeset_state+0x242/0x270 [drm_kms_helper]
[   13.621466]  warn_slowpath_null+0x2a/0x30
[   13.621476]  drm_atomic_helper_update_legacy_modeset_state+0x242/0x270 [drm_kms_helper]
[   13.621520]  intel_atomic_commit_tail+0x9a3/0xf10 [i915]
```

This one is repeated very often and then stops after a while. Is it crucial?

Initial recognition of the touchpad at the initial boot goes all-right:

```
[    3.703051] psmouse serio4: elantech: assuming hardware version 1 (with firmware version 0x020000)
[    3.730956] psmouse serio4: elantech: Synaptics capabilities query result 0x06, 0x02, 0x64.
[    3.921398] psmouse serio4: elantech: touchpad refuses to switch to absolute mode.
[    3.921408] psmouse serio4: elantech: failed to initialise registers.
[    3.921411] psmouse serio4: elantech: failed to put touchpad into absolute mode.
[    4.766740] input: ImPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input13
```

Then the machine is suspended to memory:
```

[ 3632.442598] PM: Restoring platform NVS memory
[ 3632.442598] Force enabled HPET at resume
[ 3632.442598] Suspended for 3.249 seconds
[ 3632.442598] ACPI: Waking up from system sleep state S3

```

And the touchpad hardware recognition goes horribly **WRONG**:
```
[ 3633.497950] PM: Finishing wakeup.
[ 3633.497953] Restarting tasks ... done.
[ 3634.326783] psmouse serio4: elantech: assuming hardware version 1 (with firmware version 0x020000)
[ 3634.354770] psmouse serio4: elantech: Synaptics capabilities query result 0x06, 0x02, 0x64.
[ 3634.558544] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input21
```
The touchpad is now frozen and heavily interferes/blocks keyboard input, but with fiddling a lot and clicking the keyboard unfreezes now and then.

And after that I see:
```
[ 3687.392129] Corrupted low memory at c000ffe0 (ffe0 phys) = 8ab70000
[ 3687.392143] Corrupted low memory at c000ffe8 (ffe8 phys) = f0003000
[ 3687.392151] Corrupted low memory at c000ffec (ffec phys) = 00001b42
[ 3687.392158] Corrupted low memory at c000fff0 (fff0 phys) = 1010022c
[ 3687.392165] Corrupted low memory at c000fff4 (fff4 phys) = 0000fffe
[ 3687.392172] Corrupted low memory at c000fff8 (fff8 phys) = 3000ffd2
[ 3687.392179] Corrupted low memory at c000fffc (fffc phys) = 1accf000
[ 3687.392185] ------------[ cut here ]------------
[ 3687.392204] WARNING: CPU: 0 PID: 2377 at /build/linux-hwe-JBRI_s/linux-hwe-4.10.0/arch/x86/kernel/check.c:141 check_for_bios_corruption.part.1+0x84/0xc0
[ 3687.392207] Memory corruption detected in low memory
[ 3687.392213] Modules linked in: psmouse joydev michael_mic arc4 lib80211_crypt_tkip lib80211_crypt_ccmp snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_seq_midi snd_seq_midi_event ipw2200 snd_rawmidi libipw lib80211 pcmcia snd_seq cfg80211 snd_seq_device snd_timer input_leds yenta_socket snd lpc_ich serio_raw pcmcia_rsrc pcmcia_core soundcore irda shpchp mac_hid parport_pc ppdev lp parport autofs4 i915 i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops drm b44 ssb mii pata_acpi video fjes [last unloaded: psmouse]
[ 3687.392326] CPU: 0 PID: 2377 Comm: kworker/0:1 Tainted: G S      W       4.10.0-37-generic #41~16.04.1-Ubuntu
[ 3687.392330] Hardware name: Acer             Aspire 5500Z                    /Mimid, BIOS V2.90 05/19/2006
[ 3687.392337] Workqueue: events check_corruption
[ 3687.392342] Call Trace:
[ 3687.392357]  dump_stack+0x58/0x79
[ 3687.392365]  __warn+0xea/0x110
[ 3687.392373]  ? check_for_bios_corruption.part.1+0x84/0xc0
[ 3687.392380]  warn_slowpath_fmt+0x46/0x60
[ 3687.392388]  check_for_bios_corruption.part.1+0x84/0xc0
[ 3687.392395]  check_corruption+0x19/0x50
[ 3687.392403]  process_one_work+0x121/0x400
[ 3687.392411]  worker_thread+0x37/0x4b0
[ 3687.392418]  kthread+0xdb/0x110
[ 3687.392424]  ? process_one_work+0x400/0x400
[ 3687.392430]  ? kthread_create_on_node+0x30/0x30
[ 3687.392439]  ret_from_fork+0x21/0x2c
[ 3687.392445] ---[ end trace ac807a2c0ccbad10 ]---
```

The corruption repeats and seems to continue until I manually fix the touchpad by issuing commands (but goes on one last time after that):
```

sudo modprobe -r psmouse
sudo modprobe psmouse

```

I now want to automate fixing the touchpad recognition problem.
Where can I do that?
And how can I re-initialize the corrupted low memory after that?

---

### Post by martinr on 2017-10-24
Seemingly no-one knows what can be done.
It's time to log a bug I think. 
Where should I log one that is related to hardware / evdev / elantech touchpad recognition?
And what information should I supply?
It seems to be a regression, because it used to work in the past.

---

