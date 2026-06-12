---
title: "Help with fixing System Problems!"
date: 2011-09-29
forum: Hardware
---

### Post by Lamukra on 2011-09-29
I am wondering if Something is wrong in my system or maybe something should be fixed? I do not like in particular output of this
```

cat /var/log/Xorg.0.log | grep WW
```

```
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    31.501] (WW) RADEON(0): You need a newer kernel for VBLANKs on CRTC > 1
[    31.890] (WW) evdev: Logitech USB Receiver: ignoring absolute axes.
```

I do not care about logitech receiver but CRTC line kind a distracting

Also don't like output from 

```
dmesg | grep CPU
```

```
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8800dec00000 s84416 r8192 d22080 u262144
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.001965] CPU: Physical Processor ID: 0
[    0.001967] CPU: Processor Core ID: 0
[    0.001972] mce: CPU supports 9 MCE banks
[    0.001981] CPU0: Thermal monitoring handled by SMI
[    0.134733] CPU0: Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz stepping 02
[    0.412655] CPU1: Thermal monitoring handled by SMI
[    0.592309] CPU2: Thermal monitoring handled by SMI
[    0.771960] CPU3: Thermal monitoring handled by SMI
[    0.792025] Brought up 4 CPUs
[    1.650261] Switched to NOHz mode on CPU #0
[    1.650318] Switched to NOHz mode on CPU #1
[    1.650369] Switched to NOHz mode on CPU #2
[    1.650372] Switched to NOHz mode on CPU #3
[   29.793344] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
[   33.648053] CPUFREQ: Per core ondemand sysfs interface is deprecated - ignore_nice_load
```

in particular this lines

```
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.

```
and

```
[    1.650261] Switched to NOHz mode on CPU #0
[    1.650318] Switched to NOHz mode on CPU #1
[    1.650369] Switched to NOHz mode on CPU #2
[    1.650372] Switched to NOHz mode on CPU #3
[   29.793344] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
```


Should something be fixed or everything is normal

---

### Post by An Sanct on 2011-09-29
The Kernel version is important here, please provide it...
terminal:
```
uname -r
```Also note, the difference between i5 and i7. i5 has 4 CPUs and i7 also, just i7 has multithreading enabled, while i5 does not.

---

### Post by Lamukra on 2011-09-29
> **An Sanct said:**
> The Kernel version is important here, please provide it...
terminal:
```
uname -r
```Also note, the difference between i5 and i7. i5 has 4 CPUs and i7 also, just i7 has multithreading enabled, while i5 does not.

Sorry Man! My Bad! Forgot... Here it is

```
2.6.38-11-generic
```

Yes, I heard about i5 and i7 differences, but not a lot about technical, architecture, cache and etc stuff... This has some relation to dmesg output? I mean is there some line that is saying that multithreading is disabled ? :-?

---

### Post by An Sanct on 2011-09-30
Basically, your system is working just fine, no need to *fix* anything.

1. The "You need a newer kernel for VBLANKs on CRTC > 1" issue:
This is a fall-back thing and is okay (only a warning), [see here]("http://lists.freedesktop.org/archives/dri-devel/2011-March/009463.html")

2. The "RCU-based detection of stalled CPUs is disabled." issue:
This is actually a debug variable, not interesting to *common mortals* ;) [read more here]("http://lwn.net/Articles/301910/")

3. The "intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)" thingie
Also consider this normal, its a BIOS thing. BIOS protects you from harming your hardware with over-usage (constant 100% usage), here is a ["read more" section]("http://us.generation-nt.com/answer/intel-ips-cpu-tdp-doesnt-match-expected-value-help-200012501.html")
and a quote from that section:
> 
Yeah, it's normal, and should probably be downgraded to an
informational message.  It just means your BIOS doesn't want you to
push the CPU all the way up to its maximum TDP, probably because the
platform or chassis wasn't designed for that much heat or power
consumption.


---

### Post by Lamukra on 2011-09-30
Good! I am happy then and just ignoring this! Thx

Lets go further then...
[LIST]
[*]When I close down lid, laptop is not going to sleep...
Closing a lid -> laptop keeps working
Then open a lid -> black screen and have to use force power off with holding poweroff button
Then power on -> going through grub bootloader -> choosing needed kernel(2.6.38 in our case) -> and system boot like I just opened laptop lid (X saved session with all opened windows that were before closing a lid)
[/LIST]
[LIST]
[*] Fan speed and noise kind of a crazy (Have dual boot and in windows this noise and speed appears normally when using after effects or premier - crazy processor load and memory usage, or long time using 2 screen with HDMI output and watching movies). I already Cleaned fan physically and in windows noise is even lower in some cases. In ubuntu System Monitor and "top" do not show anything connected with crazy CPU load
[/LIST]

What to do or check or install?
Maybe some more Information?

Do not like some lines in here also with words ignored, deprecated (assume it is old version of something and not needed on newer) and what gives a negative "colors" :)

output from

```
cat /var/log/Xorg.0.log | grep ACPI
```

[INDENT]```
[  4275.948] (II) Open ACPI successful (/var/run/acpid.socket)
```[/INDENT]

[INDENT]> NOTE: I do not know how this one was fixed, but previously it was saying this
```
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
```
It is still a mystery for me[/INDENT]

```
dmesg | grep ACPI
```

[INDENT]```
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x06] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] disabled)
[    5.853104] ACPI: acpi_idle yielding to intel_idle
[   25.554517] acpi device:4b: registered as cooling_device4
dimul@vaio-ubuntu:~$ dmesg | grep ACPI
[    0.000000]  BIOS-e820: 00000000dee7c000 - 00000000deebc000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000deecd000 - 00000000deedf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000deee0000 - 00000000deee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000def11000 - 00000000def12000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000def15000 - 00000000def17000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000def1b000 - 00000000def1e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000def22000 - 00000000def31000 (ACPI NVS)
[    0.000000] ACPI: RSDP 00000000000f0410 00024 (v02   Sony)
[    0.000000] ACPI: XSDT 00000000def1ce18 0005C (v01   Sony     VAIO 20100720 MSFT 00010013)
[    0.000000] ACPI: FACP 00000000def15d98 000F4 (v04   Sony     VAIO 20100720 MSFT 00010013)
[    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20110112/tbfadt-369)
[    0.000000] ACPI Warning: 32/64X FACS address mismatch in FADT - 0xDEF2DF40/0x00000000DEF30D40, using 32 (20110112/tbfadt-486)
[    0.000000] ACPI: DSDT 00000000deecd018 0ADBB (v01   Sony     VAIO 20100720 INTL 20051117)
[    0.000000] ACPI: FACS 00000000def2df40 00040
[    0.000000] ACPI: APIC 00000000def1bf18 0008C (v02   Sony     VAIO 20100720 MSFT 00010013)
[    0.000000] ACPI: MCFG 00000000def2fd18 0003C (v01   Sony     VAIO 20100720 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000def2fc98 00038 (v01   Sony     VAIO 20100720 MSFT 00000003)
[    0.000000] ACPI: SLIC 00000000def28a18 00176 (v01   Sony     VAIO 20100720 Sony 01000000)
[    0.000000] ACPI: SSDT 00000000def16018 009F1 (v01   Sony     VAIO 20100720 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000def15c18 0014B (v01   Sony     VAIO 20100720 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x06] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.004019] ACPI: Core revision 20110112
[    0.795579] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.795582] ACPI: bus type pci registered
[    0.808599] ACPI: EC: Look up EC in DSDT
[    0.892097] ACPI: Executed 2 blocks of module-level executable AML code
[    0.971848] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.972259] ACPI: SSDT 00000000def1ac18 003AE (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.972655] ACPI: Dynamic OEM Table Load:
[    0.972657] ACPI: SSDT           (null) 003AE (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.972792] ACPI: SSDT 00000000def18018 00891 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.973165] ACPI: Dynamic OEM Table Load:
[    0.973167] ACPI: SSDT           (null) 00891 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    1.071914] ACPI: SSDT 00000000def19a98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    1.072366] ACPI: Dynamic OEM Table Load:
[    1.072369] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    1.101682] ACPI: SSDT 00000000def17d98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    1.102090] ACPI: Dynamic OEM Table Load:
[    1.102092] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    1.530824] ACPI: Interpreter enabled
[    1.530829] ACPI: (supports S0 S3 S4 S5)
[    1.530852] ACPI: Using IOAPIC for interrupt routing
[    1.571719] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    1.600931] ACPI: No dock devices found.
[    1.600936] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.601264] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    1.642671] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.642825] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    1.642877] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    1.642934] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    1.643001] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    1.643051] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    1.643174]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    1.647275] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus 3f])
[    1.647458]  pci0000:3f: Requesting ACPI _OSC control (0x1d)
[    1.647671] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    1.647714] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    1.647756] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 *4 5 6 7 10 12 14 15)
[    1.647798] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    1.647840] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    1.647882] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    1.647924] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[    1.647965] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    1.648446] PCI: Using ACPI for IRQ routing
[    1.656277] pnp: PnP ACPI init
[    1.656294] ACPI: bus type pnp registered
[    1.656739] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    1.656778] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.656804] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    1.656897] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    1.656939] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.657051] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.657084] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.657121] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    1.657152] pnp 00:08: Plug and Play ACPI device, IDs SNY9011 PNP0f13 (active)
[    1.657602] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.657787] pnp 00:0a: Plug and Play ACPI device, IDs PNP0a03 (active)
[    1.673054] pnp: PnP ACPI: found 11 devices
[    1.673056] ACPI: ACPI bus type pnp unregistered
[    5.694115] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    5.704081] ACPI: AC Adapter [ADP1] (on-line)
[    5.723720] ACPI: Lid Switch [LID0]
[    5.852823] ACPI: Power Button [PWRB]
[    5.853104] ACPI: acpi_idle yielding to intel_idle
[    5.893329] ACPI: Thermal Zone [TZ00] (41 C)
[    5.913440] ACPI: Thermal Zone [TZ01] (41 C)
[    5.982203] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    5.982210] ACPI: Battery Slot [BAT0] (battery present)
[    6.482619] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    6.484002] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[   25.478503] [Firmware Bug]: ACPI(VGA) defines _DOD but not _DOS
[   25.555235] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   25.576929] sony-laptop: brightness ignored, must be controlled by ACPI video driver

```[/INDENT]

---

### Post by An Sanct on 2011-10-11
Okay, here goes :) the acpid.socket bug is known ([launchpad]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/585790"))

Altho it is an older bug, here is a quote from JayBofMA
> Same issue with Natty and nvidia-currentand a quote from dino99 (I guess you might have seen him on the forum before ...)
> ok its only a warning but i get it on all the installed distro (lucid, maverick, natty, oneiric) on Asus p5wdh + 8500 gtSo I guess there is nothing you can do... Again, it is known and should be treated only as a warning...

PS. Thanks for waiting, I kind of got overwhelmed with work ... And yes, you have to have 50 posts to PM people (spam protection ;))
PS2. On such occasions as yours (a question got answered and you add another one) it is better to start a new thread, as it is *new* and *unanswered* and will raise peoples attention ;)

---

### Post by Lamukra on 2011-12-08
OK, Thank You very much for help... Now I will be trying to setup my Samsung R20 with Xpress 1250, which gets in trouble with screen glitches on top of the screen with Unity... Will be making new thread... Thank You Once again!!!

---

