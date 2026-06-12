---
title: "Troubleshooting hardware problem (kernel panic) using Ubuntu"
date: 2016-06-07
forum: Hardware
---

### Post by Brian_Maher on 2016-06-07
I have a Lenovo Thinkpad T410 that I used to use as my school computer. I recently dug it out and decided to reinstall Ubuntu 16.04 on it and noticed that my install froze. When it froze, the caps lock key was flashing. After doing some research I found that this means there was a kernel panic.

I tried to reinstall several times with varying level of successes. One time I even managed to install completely and use Ubuntu for a day before the freeze happened again. This is obviously faulty hardware and has likely nothing to do with Ubuntu.. I was wondering however, how I could use Ubuntu (live USB) to help debug my hardware problem. I hope to be able to narrow down on the defective piece and replace it. I'm a software engineer with a medium level of Ubuntu/linux familiarity, but very little hardware experience.

Where do I start? Which logs should I read (if any)? What should I be doing to try to narrow this down? Is there a better forum for this kind of help?

Note: I also ran memtest and checked my hard drive (recently replaced) and both pass. I have a suspicion that it could be related to the network card because during each install connecting to the network had varying issues.

---

### Post by DuckHook on 2016-06-07
Welcome to the forums Brian_Maher,

I wouldn't conclude so quickly that the problem is "faulty" HW. It may be as simple as an incompatible driver for a component that is not really faulty... just unsupported or assigned the wrong driver.

Why don't you give us your full system specs? There are a number of command line reports that can tell us a lot, but since you cannot run your machine reliably, please post everything you can from your user manuals, etc. Of special note are video cards/subsystems, CPU type and model, NIC model and version, WIFI model and version, amount of DRAM and system RAM and anything else you can think of.

If you can successfully run a LiveUSB without the freeze happening, then this is a strong indication that the problem is not HW (or not *only* HW).

Also, another very good option is try installing Trusty (14.04) on it instead. Trusty is now very stable and will sometimes work well on older machines whereas Xenial still has more bugs than we would like. Trusty also still has 3 years of support on it, so it's not as if you will be facing end-of-life pressures using it either. Further options include trying the lighter flavours like L/Xubuntu/-mate, especially in their Trusty version. In all cases, LiveUSB is a good way to try things out first.

---

### Post by Bucky Ball on 2016-06-08
Just a tip. During install, don't tick 'Install Updates' or 'Install third-party drivers'. Do that later when you've installed the OS. If you are doing this, it may be the cause of your problem, including the time you actually got it installed and then it crashed and died after awhile (did you do an update or install any drivers when it did actually boot?). 

Also, if this is an old machine, you sure a modern Ubuntu is going to run on it anyway? Try Xubuntu or Lubuntu and see if you get the same result. You could also go for the minimal install, which is a text-based installer rather than a graphics one, and install 'ubuntu-desktop' when you get the option to during install.

If you are having graphics issues because of something installed during updates this may avoid it.

---

### Post by Brian_Maher on 2016-06-08
Thank you both for the feedback. I've since experimented a bit and got it pretty well narrowed down to an issue with wifi. Whether it's a HW or driver issue, I don't know..

In response to some of your feedback:
1) This laptop is about 6 years old now, from what I can tell it runs Ubuntu 16.04 just fine.
2) Nvidia optimus, 8gb RAM, Intel i5, 1tb HDD. I've upgraded it a bit over the years; I can get some more detailed specs if necesary, but hear me out below to see if that's necessary.
3) I did attempt to install Ubuntu 14.04 and ran into the same issue
4) LiveUSB also caused kernel panic (shortly after connecting to wifi -- this will be relevant below)

Now for some updates: The kernel panics have not provided any output and I was unable to retrieve that information because the liveUSB was crashing as well. Now, the last time I had a kernel panic on install I got some output! I was able to see several references to `iwlwifi`. I had an idea to hit the wifi hardware switch on the side of my laptop and attempt a new install. Turns out that worked just fine! Additionally, I can use ethernet to connect to the internet, which also seems to work just fine.

I was able to consistently reproduce the kernel panic after a clean install by toggling the wifi hardware switch on. The crash occurs within ~3 seconds.

Additionally I cross-posted this issue to the ask ubuntu forums and was asked to provide some additional information. It may be helpful here as well:

```
brian@think:~$ lspci -nnk | grep 0280 -A2
03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [Condor Peak] [8086:0084]
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1315]
    Kernel driver in use: iwlwifi
```
```
brian@think:~$ dmesg | grep iwl
[   14.809250] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   14.866919] iwlwifi 0000:03:00.0: loaded firmware version 39.31.5.1 build 35138 op_mode iwldvm
[   15.297564] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   15.297568] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   15.297570] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   15.297572] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   15.297702] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   15.305024] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
[   15.337092] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   15.554811] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
```

```
brian@think:~$ lsmod | grep -e wmi -e lap
snd_rawmidi            32768  1 snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd                    81920  18 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau
```
[FONT=Ubuntu]
```
brian@think:~$ dmesg | grep -i acpi
[    0.000000] BIOS-e820: [mem 0x00000000bb371000-0x00000000bb3f1fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bb668000-0x00000000bb6e7fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bb76c000-0x00000000bb777fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bb778000-0x00000000bb77afff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bb77b000-0x00000000bb78afff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bb78b000-0x00000000bb78bfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bb78c000-0x00000000bb79efff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bb79f000-0x00000000bb7fefff] ACPI data
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000F6870 000024 (v02 LENOVO)
[    0.000000] ACPI: XSDT 0x00000000BB7EF320 000094 (v01 LENOVO TP-6I    00001340  LTP 00000000)
[    0.000000] ACPI: FACP 0x00000000BB7EF400 0000F4 (v04 LENOVO TP-6I    00001340 LNVO 00000001)
[    0.000000] ACPI BIOS Warning (bug): 32/64X length mismatch in FADT/Pm1aControlBlock: 16/32 (20150930/tbfadt-623)
[    0.000000] ACPI BIOS Warning (bug): Invalid length for FADT/Pm1aControlBlock: 32, using default 16 (20150930/tbfadt-704)
[    0.000000] ACPI: DSDT 0x00000000BB7EF7D1 00F310 (v01 LENOVO TP-6I    00001340 MSFT 03000001)
[    0.000000] ACPI: FACS 0x00000000BB6E7000 000040
[    0.000000] ACPI: FACS 0x00000000BB6E7000 000040
[    0.000000] ACPI: SSDT 0x00000000BB7EF5B4 00021D (v01 LENOVO TP-6I    00001340 MSFT 03000001)
[    0.000000] ACPI: ECDT 0x00000000BB7FEAE1 000052 (v01 LENOVO TP-6I    00001340 LNVO 00000001)
[    0.000000] ACPI: APIC 0x00000000BB7FEB33 000084 (v01 LENOVO TP-6I    00001340 LNVO 00000001)
[    0.000000] ACPI: MCFG 0x00000000BB7FEBEF 00003C (v01 LENOVO TP-6I    00001340 LNVO 00000001)
[    0.000000] ACPI: HPET 0x00000000BB7FEC2B 000038 (v01 LENOVO TP-6I    00001340 LNVO 00000001)
[    0.000000] ACPI: ASF! 0x00000000BB7FEDBE 0000A4 (v16 LENOVO TP-6I    00001340 PTL  00000001)
[    0.000000] ACPI: SLIC 0x00000000BB7FEE62 000176 (v01 LENOVO TP-6I    00001340  LTP 00000000)
[    0.000000] ACPI: BOOT 0x00000000BB7FEFD8 000028 (v01 LENOVO TP-6I    00001340  LTP 00000001)
[    0.000000] ACPI: SSDT 0x00000000BB6E591A 00084B (v01 LENOVO TP-6I    00001340 INTL 20050513)
[    0.000000] ACPI: TCPA 0x00000000BB78B000 000032 (v02 PTL     CRESTLN 06040000      00005A52)
[    0.000000] ACPI: SSDT 0x00000000BB77A000 0009F1 (v01 PmRef  CpuPm    00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 0x00000000BB779000 000259 (v01 PmRef  Cpu0Tst  00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 0x00000000BB778000 00049F (v01 PmRef  ApTst    00003000 INTL 20061109)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000081] ACPI: Core revision 20150930
[    0.030220] ACPI: 6 ACPI AML tables successfully acquired and loaded
[    0.259380] PM: Registering ACPI NVS region [mem 0xbb371000-0xbb3f1fff] (528384 bytes)
[    0.259398] PM: Registering ACPI NVS region [mem 0xbb668000-0xbb6e7fff] (524288 bytes)
[    0.259414] PM: Registering ACPI NVS region [mem 0xbb76c000-0xbb777fff] (49152 bytes)
[    0.259417] PM: Registering ACPI NVS region [mem 0xbb77b000-0xbb78afff] (65536 bytes)
[    0.259421] PM: Registering ACPI NVS region [mem 0xbb78c000-0xbb79efff] (77824 bytes)
[    0.284341] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.284344] ACPI: bus type PCI registered
[    0.284347] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.296867] ACPI: Added _OSI(Module Device)
[    0.296871] ACPI: Added _OSI(Processor Device)
[    0.296874] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.296877] ACPI: Added _OSI(Processor Aggregator Device)
[    0.299479] ACPI : EC: EC description table is found, configuring boot EC
[    0.299497] ACPI : EC: EC started
[    0.307594] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.384745] ACPI: Dynamic OEM Table Load:
[    0.384759] ACPI: SSDT 0xFFFF880231CCA800 0004F3 (v01 PmRef  Cpu0Ist  00003000 INTL 20061109)
[    0.385672] ACPI: Dynamic OEM Table Load:
[    0.385684] ACPI: SSDT 0xFFFF880231CCB000 0006B2 (v01 PmRef  Cpu0Cst  00003001 INTL 20061109)
[    0.386952] ACPI: Dynamic OEM Table Load:
[    0.386963] ACPI: SSDT 0xFFFF880231CDAC00 000303 (v01 PmRef  ApIst    00003000 INTL 20061109)
[    0.387880] ACPI: Dynamic OEM Table Load:
[    0.387889] ACPI: SSDT 0xFFFF880231D0DA00 000119 (v01 PmRef  ApCst    00003000 INTL 20061109)
[    0.390790] ACPI: Interpreter enabled
[    0.390801] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150930/hwxface-580)
[    0.390810] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150930/hwxface-580)
[    0.390838] ACPI: (supports S0 S3 S4 S5)
[    0.390841] ACPI: Using IOAPIC for interrupt routing
[    0.390883] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.400677] ACPI: Power Resource [PUBS] (on)
[    0.401555] acpi PNP0C0A:01: ACPI dock station (docks/bays count: 1)
[    0.403891] acpi LNXIOBAY:00: ACPI dock station (docks/bays count: 2)
[    0.407127] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    0.407297] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    0.407428] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.407596] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    0.407762] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[    0.407927] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[    0.408057] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.408242] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    0.408407] ACPI: PCI Root Bridge [UNCR] (domain 0000 [bus ff])
[    0.408417] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.408425] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.409171] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.409179] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.409525] acpi PNP0A08:00: _OSC: platform does not support [PCIeCapability]
[    0.409686] acpi PNP0A08:00: _OSC: not requesting control; platform does not support [PCIeCapability]
[    0.409692] acpi PNP0A08:00: _OSC: OS requested [PCIeHotplug PME AER PCIeCapability]
[    0.409696] acpi PNP0A08:00: _OSC: platform willing to grant [PCIeHotplug PME AER]
[    0.409700] acpi PNP0A08:00: _OSC failed (AE_SUPPORT); disabling ASPM
[    0.411200] pci 0000:00:19.0: System wakeup disabled by ACPI
[    0.411504] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.411828] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.412103] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.412393] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.412667] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.412941] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.413246] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.416613] acpiphp: Slot [1] registered
[    0.426340] ACPI: Enabled 3 GPEs in block 00 to 3F
[    0.426456] ACPI : EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    0.427288] ACPI: bus type USB registered
[    0.427635] PCI: Using ACPI for IRQ routing
[    0.454198] pnp: PnP ACPI init
[    0.456227] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.456910] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.457025] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.457074] pnp 00:03: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.457124] pnp 00:04: Plug and Play ACPI device, IDs LEN0015 PNP0f13 (active)
[    0.458144] pnp: PnP ACPI: found 5 devices
[    0.467231] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    1.741232] ACPI: AC Adapter [AC] (off-line)
[    1.741519] ACPI: Lid Switch [LID]
[    1.741604] ACPI: Sleep Button [SLPB]
[    1.741691] ACPI: Power Button [PWRF]
[    1.747288] ACPI: Thermal Zone [THM0] (49 C)
[    1.763626] ACPI: Battery Slot [BAT0] (battery present)
[    1.933181] ACPI Warning: \_SB_.PCI0.VID_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
[    1.933199] ACPI: \_SB_.PCI0.VID_: failed to evaluate _DSM
[    1.933265] ACPI Warning: \_SB_.PCI0.PEG_.VID_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
[    1.933523] ACPI Warning: \_SB_.PCI0.PEG_.VID_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
[    2.410145] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    2.411183] acpi device:01: registered as cooling_device4
[    2.411423] ACPI: Video Device [VID1] (multi-head: yes  rom: yes  post: no)
[    2.586961] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    2.586967] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    2.586971] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.588673] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    2.588680] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    2.588685] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    3.085139] ata2.00: ACPI cmd e3/00:1f:00:00:00:a0 (IDLE) succeeded
[    3.086016] ata2.00: ACPI cmd e3/00:02:00:00:00:a0 (IDLE) succeeded
[    3.091254] ata2.00: ACPI cmd e3/00:1f:00:00:00:a0 (IDLE) succeeded
[    3.092093] ata2.00: ACPI cmd e3/00:02:00:00:00:a0 (IDLE) succeeded
[    7.998233] ACPI Warning: \_SB_.PCI0.PEG_.VID_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
[    7.999069] ACPI Warning: \_SB_.PCI0.PEG_.VID_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
[   14.343063] ACPI Warning: SystemIO range 0x0000000000001028-0x000000000000102F conflicts with OpRegion 0x0000000000001000-0x000000000000107F (\_SB_.PCI0.LPC_.PMIO) (20150930/utaddress-254)
[   14.343070] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.343073] ACPI Warning: SystemIO range 0x00000000000011C0-0x00000000000011CF conflicts with OpRegion 0x0000000000001180-0x00000000000011FF (\_SB_.PCI0.LPC_.LPIO) (20150930/utaddress-254)
[   14.343076] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.343078] ACPI Warning: SystemIO range 0x00000000000011B0-0x00000000000011BF conflicts with OpRegion 0x0000000000001180-0x00000000000011FF (\_SB_.PCI0.LPC_.LPIO) (20150930/utaddress-254)
[   14.343080] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.343081] ACPI Warning: SystemIO range 0x0000000000001180-0x00000000000011AF conflicts with OpRegion 0x0000000000001180-0x00000000000011FF (\_SB_.PCI0.LPC_.LPIO) (20150930/utaddress-254)
[   14.343084] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.987261] thinkpad_acpi: ThinkPad ACPI Extras v0.25
[   14.987264] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[   14.987266] thinkpad_acpi: ThinkPad BIOS 6IET74WW (1.34 ), EC 6IHT38WW-1.13
[   14.987267] thinkpad_acpi: Lenovo ThinkPad T410, model 2516CTO
[   14.987632] thinkpad_acpi: detected a 16-level brightness capable ThinkPad
[   14.987779] thinkpad_acpi: radio switch found; radios are disabled
[   14.987792] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
[   14.987793] thinkpad_acpi: Disabling thinkpad-acpi brightness events by default...
[   14.990826] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one
[   14.992369] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input9
[   15.767814] thinkpad_acpi: EC reports that Thermal Table has changed
[   33.986527] ACPI Warning: \_SB_.PCI0.PEG_.VID_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
[   33.987257] ACPI Warning: \_SB_.PCI0.PEG_.VID_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
[   36.132251] thinkpad_acpi: EC reports that Thermal Table has changed
[   37.803999] thinkpad_acpi: EC reports that Thermal Table has changed
[   45.974727] ACPI Warning: \_SB_.PCI0.PEG_.VID_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
[   45.975831] ACPI Warning: \_SB_.PCI0.PEG_.VID_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
[   48.071213] thinkpad_acpi: EC reports that Thermal Table has changed
[   53.828605] thinkpad_acpi: EC reports that Thermal Table has changed
[   59.761786] ACPI Warning: \_SB_.PCI0.PEG_.VID_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
[   59.762655] ACPI Warning: \_SB_.PCI0.PEG_.VID_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
[   61.845248] thinkpad_acpi: EC reports that Thermal Table has changed
[  298.125243] thinkpad_acpi: EC reports that Thermal Table has changed
[  305.632720] ACPI Warning: \_SB_.PCI0.PEG_.VID_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
[  305.633633] ACPI Warning: \_SB_.PCI0.PEG_.VID_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
[  307.729603] thinkpad_acpi: EC reports that Thermal Table has changed
[  374.159405] thinkpad_acpi: EC reports that Thermal Table has changed
[  389.646710] ACPI Warning: \_SB_.PCI0.PEG_.VID_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
[  389.647770] ACPI Warning: \_SB_.PCI0.PEG_.VID_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
[  391.780885] thinkpad_acpi: EC reports that Thermal Table has changed
[  423.828001] thinkpad_acpi: EC reports that Thermal Table has changed
[  429.654620] ACPI Warning: \_SB_.PCI0.PEG_.VID_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
[  429.655667] ACPI Warning: \_SB_.PCI0.PEG_.VID_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
[  431.783992] thinkpad_acpi: EC reports that Thermal Table has changed
[ 1102.513116] thinkpad_acpi: EC reports that Thermal Table has changed
[ 1107.839485] ACPI Warning: \_SB_.PCI0.PEG_.VID_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
[ 1107.840697] ACPI Warning: \_SB_.PCI0.PEG_.VID_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
[ 1109.932024] thinkpad_acpi: EC reports that Thermal Table has changed
[ 1569.514290] thinkpad_acpi: EC reports that Thermal Table has changed
[ 1575.668596] ACPI Warning: \_SB_.PCI0.PEG_.VID_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
[ 1575.669643] ACPI Warning: \_SB_.PCI0.PEG_.VID_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
[ 1577.768968] thinkpad_acpi: EC reports that Thermal Table has changed
[ 3102.744959] thinkpad_acpi: EC reports that Thermal Table has changed
```


[/FONT]
This is where I'm at on the ask ubuntu [post]("http://askubuntu.com/questions/784223/thinkpad-kernel-panic-when-wifi-switch-enabled") as well.

---

### Post by DuckHook on 2016-06-08
...please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

You are being helped out by chili555 on AskUbuntu. He is a member of these forums too, and you could not ask to be put in better hands. I recommend that you just pursue your solution there. BTW, thank you for alerting us to your AU thread so as not to dilute community effort.

*EDIT*

I see that my fellow mod *deadflowr* has already added the code tags.

---

### Post by Brian_Maher on 2016-06-08
Thanks for fixing the formatting. I'll go ahead and pursue the answer on AU.. Should I do anything to mark this thread as such?

---

### Post by DuckHook on 2016-06-08
> **Brian_Maher said:**
> ...I'll go ahead and pursue the answer on AU.. Should I do anything to mark this thread as such?Very considerate of you to ask. You may wish to keep this thread unsolved for now. It does no harm and you may wish to make use of it later. However, if you find the solution on AU and don't mind following up here, then please post that solution back to this thread and mark it *solved*. That way others who have the same problem can find it when searching.

It would be your first solution contributed to the community! ;)

---

