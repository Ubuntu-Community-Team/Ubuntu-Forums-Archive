---
title: "intel atom d2700 HOT / CPU Fan control"
date: 2012-06-12
forum: Hardware
---

### Post by cylent on 2012-06-12
I just bought me a Eee PC VX6S yesterday -- the only problem (while it runs great and fast) is the CPU wont give up. the fan is always on and the heatsink where the hot air dissipates from is a flame. 

this is an intel atom 2.13 d2700 ...

is it possible to control the CPU fan?

---

### Post by mikewhatever on 2012-06-13
D2700 is a cpu from Intel's Cedar Trail line up, and the bad news is, it's coupled with the GMA3xxx, which is the recent reincarnation of the GMA500. 
Intel doesn't want to provide support for GMA500/GMA600/GMA3600 on Linux, and, reportedly, even the W7 driver is crap right now. 
Are you sure it runs all that great and fast?

PS: there a thread discussing the lack of support for GMA3600.
[http://ubuntuforums.org/showthread.php?t=1953734&highlight=gma3600](http://ubuntuforums.org/showthread.php?t=1953734&highlight=gma3600)

---

### Post by cylent on 2012-06-13
> **mikewhatever said:**
> D2700 is a cpu from Intel's Cedar Trail line up, and the bad news is, it's coupled with the GMA3xxx, which is the recent reincarnation of the GMA500. 
Intel doesn't want to provide support for GMA500/GMA600/GMA3600 on Linux, and, reportedly, even the W7 driver is crap right now. 
Are you sure it runs all that great and fast?

PS: there a thread discussing the lack of support for GMA3600.
[http://ubuntuforums.org/showthread.php?t=1953734&highlight=gma3600](http://ubuntuforums.org/showthread.php?t=1953734&highlight=gma3600)

half correct. [http://eee.asus.com/en/eeepc/vx6s#specs](http://eee.asus.com/en/eeepc/vx6s#specs)
this one has a radeon 6470m which works great
however my issue is the cpu is running at full throttle all the time.

please advise

---

### Post by mikewhatever on 2012-06-13
My bad, shouldn't have assumed without asking. I don't have the solution, but can you post some outputs from a terminal window:

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors

dmesg | grep ACPI

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

What version of Ubuntu do you use? Cedar Trail is rather new, so there might be no support for it in older kernels.

---

### Post by typhoon_tip on 2012-06-13
> **cylent said:**
> half correct. [http://eee.asus.com/en/eeepc/vx6s#specs](http://eee.asus.com/en/eeepc/vx6s#specs)
this one has a radeon 6470m which works great
however my issue is the cpu is running at full throttle all the time.

please advise

Radeon ? Then I can assure you that is not the CPU but the video card that is making the fan run full throttle. You must install FGLRX driver, otherwise it is always staying hot all the time. The open source driver is very fine, working fast, but the GPU constantly stays at 100% usage...

Moreover, if you have hybrid configuration, you should use the BIOS to enable only the discreet card (ATI) before attempting to install the driver.

---

### Post by cylent on 2012-06-13
ok few things:

this is on the 3.2 kernel. i tried ubuntu 12.04 and linux mint (latest). same issue.

in reference to it being a radeon issue. i did install the drivers which i downloaded directly from the ati/amd website and installed that. then i loaded the catalyst center and made sure even when its plugged in its set to PowerSave mode. 

still same problem :mad:.

according to powertop the machine is sucking 17.7W constantly. i even went as far as disabling wifi from the bios thinking it maybe an issue and its still the same. draining at 17+

on a side note and i realize these are the ubuntu forums -- in mint since it doesnt use gnome 3 when i added the cpu frequency control applet to the task bar it never adds it just doesnt do it. whatever that may mean... 

i also tried the ASPM grub line. no change. 

i dont know what to do. if it keeps draining battery like this then my hopes of running linux on this laptop are slim ... 

on a side note: i am planning on compiling kernel 3.4 and setting CPU to intel atom. as well as enabling BFS and BFQ patches in it.

---

### Post by mikewhatever on 2012-06-13
Linux Mint is Ubuntu, especially at the kernel level, so no surprizes there. The pcie_aspm=force option shouldn't be CPU related, and should also be on by default. You might want to try Fedora 17, which has 3.4, and please post the outputs I asked for.

---

### Post by cylent on 2012-06-13
> **mikewhatever said:**
> My bad, shouldn't have assumed without asking. I don't have the solution, but can you post some outputs from a terminal window:

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors

dmesg | grep ACPI

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

What version of Ubuntu do you use? Cedar Trail is rather new, so there might be no support for it in older kernels.

first.. i dont have a directory cpufreq/ under any of the cpus as you can see below. it stops at cpuX

[INDENT][FONT=Courier New]paul@paul-VX6S ~ $ cd /sys/devices/system/cpu/cpu[/FONT]
[FONT=Courier New] cpu0/    cpu1/    cpu2/    cpu3/    cpufreq/ cpuidle/ [/FONT]
[FONT=Courier New] paul@paul-VX6S ~ $ cd /sys/devices/system/cpu/cpu0/[/FONT]
[FONT=Courier New] cache/    node0/    topology/ [/FONT]
[FONT=Courier New] paul@paul-VX6S ~ $ cd /sys/devices/system/cpu/cpu0/[/FONT]
[FONT=Courier New] [/FONT]
[FONT=Courier New] paul@paul-VX6S ~ $ dmesg | grep ACPI[/FONT]
[FONT=Courier New] [    0.000000]  BIOS-e820: 00000000bf9a2000 - 00000000bf9e9000 (ACPI NVS)[/FONT]
[FONT=Courier New] [    0.000000]  BIOS-e820: 00000000bfb13000 - 00000000bfb14000 (ACPI NVS)[/FONT]
[FONT=Courier New] [    0.000000]  BIOS-e820: 00000000bfb14000 - 00000000bfb1e000 (ACPI data)[/FONT]
[FONT=Courier New] [    0.000000]  BIOS-e820: 00000000bfb38000 - 00000000bfb49000 (ACPI NVS)[/FONT]
[FONT=Courier New] [    0.000000]  BIOS-e820: 00000000bfb69000 - 00000000bfb75000 (ACPI NVS)[/FONT]
[FONT=Courier New] [    0.000000]  BIOS-e820: 00000000bfbcc000 - 00000000bfc0f000 (ACPI NVS)[/FONT]
[FONT=Courier New] [    0.000000] ACPI: RSDP 00000000000f0450 00024 (v02 ALASKA)[/FONT]
[FONT=Courier New] [    0.000000] ACPI: XSDT 00000000bfb14068 00054 (v01 _ASUS_ Notebook 01072009 AMI  00010013)[/FONT]
[FONT=Courier New] [    0.000000] ACPI: FACP 00000000bfb1c9a8 000F4 (v04 ALASKA    A M I 01072009 AMI  00010013)[/FONT]
[FONT=Courier New] [    0.000000] ACPI: DSDT 00000000bfb14150 08852 (v02 ALASKA    A M I 00000000 INTL 20051117)[/FONT]
[FONT=Courier New] [    0.000000] ACPI: FACS 00000000bfb72f80 00040[/FONT]
[FONT=Courier New] [    0.000000] ACPI: APIC 00000000bfb1caa0 00072 (v03 ALASKA    A M I 01072009 AMI  00010013)[/FONT]
[FONT=Courier New] [    0.000000] ACPI: MCFG 00000000bfb1cb18 0003C (v01 ALASKA    A M I 01072009 MSFT 00000097)[/FONT]
[FONT=Courier New] [    0.000000] ACPI: HPET 00000000bfb1cb58 00038 (v01 ALASKA    A M I 01072009 AMI. 00000005)[/FONT]
[FONT=Courier New] [    0.000000] ACPI: SSDT 00000000bfb1cb90 00655 (v01  PmRef    CpuPm 00003000 INTL 20051117)[/FONT]
[FONT=Courier New] [    0.000000] ACPI: SLIC 00000000bfb1d1e8 00176 (v01 _ASUS_ Notebook 00000000      00000000)[/FONT]
[FONT=Courier New] [    0.000000] ACPI: Local APIC address 0xfee00000[/FONT]
[FONT=Courier New] [    0.000000] ACPI: PM-Timer IO Port: 0x408[/FONT]
[FONT=Courier New] [    0.000000] ACPI: Local APIC address 0xfee00000[/FONT]
[FONT=Courier New] [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)[/FONT]
[FONT=Courier New] [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)[/FONT]
[FONT=Courier New] [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)[/FONT]
[FONT=Courier New] [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)[/FONT]
[FONT=Courier New] [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])[/FONT]
[FONT=Courier New] [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])[/FONT]
[FONT=Courier New] [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)[/FONT]
[FONT=Courier New] [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)[/FONT]
[FONT=Courier New] [    0.000000] ACPI: IRQ0 used by override.[/FONT]
[FONT=Courier New] [    0.000000] ACPI: IRQ2 used by override.[/FONT]
[FONT=Courier New] [    0.000000] ACPI: IRQ9 used by override.[/FONT]
[FONT=Courier New] [    0.000000] Using ACPI (MADT) for SMP configuration information[/FONT]
[FONT=Courier New] [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000[/FONT]
[FONT=Courier New] [    0.013122] ACPI: Core revision 20110623[/FONT]
[FONT=Courier New] [    0.348202] PM: Registering ACPI NVS region at bf9a2000 (290816 bytes)[/FONT]
[FONT=Courier New] [    0.348202] PM: Registering ACPI NVS region at bfb13000 (4096 bytes)[/FONT]
[FONT=Courier New] [    0.348202] PM: Registering ACPI NVS region at bfb38000 (69632 bytes)[/FONT]
[FONT=Courier New] [    0.348202] PM: Registering ACPI NVS region at bfb69000 (49152 bytes)[/FONT]
[FONT=Courier New] [    0.348202] PM: Registering ACPI NVS region at bfbcc000 (274432 bytes)[/FONT]
[FONT=Courier New] [    0.350647] ACPI: bus type pci registered[/FONT]
[FONT=Courier New] [    0.354867] ACPI: Added _OSI(Module Device)[/FONT]
[FONT=Courier New] [    0.354876] ACPI: Added _OSI(Processor Device)[/FONT]
[FONT=Courier New] [    0.354882] ACPI: Added _OSI(3.0 _SCP Extensions)[/FONT]
[FONT=Courier New] [    0.354889] ACPI: Added _OSI(Processor Aggregator Device)[/FONT]
[FONT=Courier New] [    0.359567] ACPI: EC: Look up EC in DSDT[/FONT]
[FONT=Courier New] [    0.364308] ACPI: Executed 1 blocks of module-level executable AML code[/FONT]
[FONT=Courier New] [    0.396206] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored[/FONT]
[FONT=Courier New] [    0.397514] ACPI: SSDT 00000000bfb1e018 0091E (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)[/FONT]
[FONT=Courier New] [    0.398669] ACPI: Dynamic OEM Table Load:[/FONT]
[FONT=Courier New] [    0.398679] ACPI: SSDT           (null) 0091E (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)[/FONT]
[FONT=Courier New] [    0.420933] ACPI: SSDT 00000000bfb20f18 0008D (v01  PmRef    ApCst 00003000 INTL 20051117)[/FONT]
[FONT=Courier New] [    0.422099] ACPI: Dynamic OEM Table Load:[/FONT]
[FONT=Courier New] [    0.422109] ACPI: SSDT           (null) 0008D (v01  PmRef    ApCst 00003000 INTL 20051117)[/FONT]
[FONT=Courier New] [    0.454215] ACPI: Interpreter enabled[/FONT]
[FONT=Courier New] [    0.454229] ACPI: (supports S0 S3 S4 S5)[/FONT]
[FONT=Courier New] [    0.454294] ACPI: Using IOAPIC for interrupt routing[/FONT]
[FONT=Courier New] [    0.454875] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources[/FONT]
[FONT=Courier New] [    0.556390] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62[/FONT]
[FONT=Courier New] [    0.556977] ACPI: No dock devices found.[/FONT]
[FONT=Courier New] [    0.556993] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug[/FONT]
[FONT=Courier New] [    0.557506] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])[/FONT]
[FONT=Courier New] [    0.592406] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT][/FONT]
[FONT=Courier New] [    0.592675] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT][/FONT]
[FONT=Courier New] [    0.592815] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT][/FONT]
[FONT=Courier New] [    0.592941] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT][/FONT]
[FONT=Courier New] [    0.593030] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT][/FONT]
[FONT=Courier New] [    0.593363]  pci0000:00: Requesting ACPI _OSC control (0x1d)[/FONT]
[FONT=Courier New] [    0.593504]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d[/FONT]
[FONT=Courier New] [    0.593510] ACPI _OSC control for PCIe not granted, disabling ASPM[/FONT]
[FONT=Courier New] [    0.606492] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)[/FONT]
[FONT=Courier New] [    0.606650] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 *5 6 7 11 12 14 15)[/FONT]
[FONT=Courier New] [    0.606801] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)[/FONT]
[FONT=Courier New] [    0.606970] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 *7 11 12 14 15)[/FONT]
[FONT=Courier New] [    0.607123] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)[/FONT]
[FONT=Courier New] [    0.607282] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)[/FONT]
[FONT=Courier New] [    0.607437] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11[/FONT]
[FONT=Courier New] [    0.607591] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 *4 5 6 7 11 12 14 15)[/FONT]
[FONT=Courier New] [    0.608625] PCI: Using ACPI for IRQ routing[/FONT]
[FONT=Courier New] [    0.644294] pnp: PnP ACPI init[/FONT]
[FONT=Courier New] [    0.644326] ACPI: bus type pnp registered[/FONT]
[FONT=Courier New] [    0.644781] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)[/FONT]
[FONT=Courier New] [    0.645025] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)[/FONT]
[FONT=Courier New] [    0.645163] pnp 00:02: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)[/FONT]
[FONT=Courier New] [    0.645302] pnp 00:03: Plug and Play ACPI device, IDs SYN0a13 SYN0a00 SYN0002 PNP0f13 (active)[/FONT]
[FONT=Courier New] [    0.645870] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)[/FONT]
[FONT=Courier New] [    0.646355] system 00:05: Plug and Play ACPI device, IDs PNP0c01 (active)[/FONT]
[FONT=Courier New] [    0.646473] pnp 00:06: Plug and Play ACPI device, IDs INT0800 (active)[/FONT]
[FONT=Courier New] [    0.646954] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)[/FONT]
[FONT=Courier New] [    0.646963] pnp: PnP ACPI: found 8 devices[/FONT]
[FONT=Courier New] [    0.646966] ACPI: ACPI bus type pnp unregistered[/FONT]
[FONT=Courier New] [    1.197232] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared[/FONT]
[FONT=Courier New] [    1.197326] ACPI: AC Adapter [AC0] (on-line)[/FONT]
[FONT=Courier New] [    1.197568] ACPI: Power Button [PWRB][/FONT]
[FONT=Courier New] [    1.197663] ACPI: Sleep Button [SLPB][/FONT]
[FONT=Courier New] [    1.202429] ACPI: Lid Switch [LID][/FONT]
[FONT=Courier New] [    1.202533] ACPI: Power Button [PWRF][/FONT]
[FONT=Courier New] [    1.213440] ACPI: Thermal Zone [TZ00] (27 C)[/FONT]
[FONT=Courier New] [    1.213881] ACPI: Thermal Zone [TZ01] (52 C)[/FONT]
[FONT=Courier New] [    1.213922] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared[/FONT]
[FONT=Courier New] [    1.213943] ACPI: Battery Slot [BAT0] (battery present)[/FONT]
[FONT=Courier New] [    1.313888] ACPI: Battery Slot [BAT0] (battery present)[/FONT]
[FONT=Courier New] [   11.523891] ACPI: Video Device [AGFX] (multi-head: yes  rom: no  post: no)[/FONT]
[FONT=Courier New] [   13.313861] asus_wmi: Backlight controlled by ACPI video driver[/FONT]
[FONT=Courier New] paul@paul-VX6S ~ $ [/FONT]
[/INDENT][FONT=Courier New]
[FONT=Arial]hopefully that helps[/FONT]


[/FONT]

---

### Post by mikewhatever on 2012-06-13
> **cylent said:**
> first.. i dont have a directory cpufreq/ under any of the cpus as you can see below. it stops at cpuX

...

Thanks! The lack of the cpufreq/ and cpu gpvernors explains the lack of cpu scaling. I can't find references to similar problem, could something be off in the BIOS?

---

### Post by cylent on 2012-06-13
> **mikewhatever said:**
> Thanks! The lack of the cpufreq/ and cpu gpvernors explains the lack of cpu scaling. I can't find references to similar problem, could something be off in the BIOS?

i figured as much.

the only thing in the bios for any cpu setting is: limit cpuid maxvalue

i am curious then how windows can throttle and achieve 6-8 hours?

what is interesting though is on the intel website under specs it says for 

Enhanced Intel SpeedStep® Technology  _**No**_

[http://ark.intel.com/products/59683/](http://ark.intel.com/products/59683/)

is that the only way to throttle the cpu though?

[edit: if it stops running the fan and somehow use less than 17.7w of power i wouldnt care. is there anyway to do that? maybe underclock the vid card?]

---

### Post by cylent on 2012-06-13
so i assume this case is closed and theres no solution then?

---

### Post by mikewhatever on 2012-06-13
Not sure really. It certainly looks like a case of unsupported hardware. As said above, I'd try a more recent kernel (Fedora 17, Ubuntu 12.10 alpha1) just to see if it makes any difference.

---

### Post by cylent on 2012-06-13
ok well good news goes first.

i decided to try sabayon (based on gentoo). which has kernel 3.4.

now in the /sys/devices/system/cpu/cpu0 there are the following directories.

cache/ microcode/ node0/ power/ subsystem/ topology/ uevent/

in the power/ directory there is:

autosuspend_delay_ms control runtime_active_time runtime_suspended_time runtime_status

ubuntu 12.10 has the same directory structure as sabayon (same kernel) but still no scaling for cpu.

---

### Post by cylent on 2012-06-14
i am soooooooooooo annoyed by this now.

my plan is to purchase an atom based netbook and enjoy slowly returning to my fun days of linux.

3.4 obviously is the latest. 3.5 is bleeding edge and even bfs and bfq arent available as patches for it -- although i still cant vouch for  a system that has those patches to see real world differences.

the thing is even if i choose to ignore this issue i cant. the fan runs constantly. the heatsink area on this laptop is on the bottom left so my left leg would literally become a heat sink recipient slowly turning into a mini stove.

what to do what to do.

---

### Post by typhoon_tip on 2012-06-16
> **cylent said:**
> i am soooooooooooo annoyed by this now.

my plan is to purchase an atom based netbook and enjoy slowly returning to my fun days of linux.

3.4 obviously is the latest. 3.5 is bleeding edge and even bfs and bfq arent available as patches for it -- although i still cant vouch for  a system that has those patches to see real world differences.

the thing is even if i choose to ignore this issue i cant. the fan runs constantly. the heatsink area on this laptop is on the bottom left so my left leg would literally become a heat sink recipient slowly turning into a mini stove.

what to do what to do.

Have you tried to install:
```
sudo apt-get install indicator-cpufreq
```

After install, logoff and login again. Does it gives an error or it works ? If it stays up, does this one too show the CPU constantly at maximum ?

Moreover, can you please post the output of:
```
top
```

---

### Post by cylent on 2012-06-17
> **typhoon_tip said:**
> Have you tried to install:
```
sudo apt-get install indicator-cpufreq
```After install, logoff and login again. Does it gives an error or it works ? If it stays up, does this one too show the CPU constantly at maximum ?

Moreover, can you please post the output of:
```
top
```

cpufreqd when ran just vanishes. nothing happens. 

i haven't run top yet. will do and update. 
if you're thinking a running process (or sleeping) maybe keeping the CPU at max then i doubt it cause almost every distro i run shows the same signs. there's simply no kernel support to throttle the atom.

---

### Post by typhoon_tip on 2012-06-17
> **cylent said:**
> cpufreqd when ran just vanishes. nothing happens. 

i haven't run top yet. will do and update. 
if you're thinking a running process (or sleeping) maybe keeping the CPU at max then i doubt it cause almost every distro i run shows the same signs. there's simply no kernel support to throttle the atom.

Trust me, post a top output anyway, please. I am using my laptop with disabled throttling (2 core, 2.27 Ghz) and all I gain is +1C~+3C on the CPU if a run with fixed frequency. Temperature increase *only* on CPU usage. I think your problem may be related to other devices.

Please post an output of:
```
sensors
```

If is not installed, use this to install:
```
sudo apt-get install lm-sensors
```

---

### Post by cylent on 2012-06-17
> **typhoon_tip said:**
> Trust me, post a top output anyway, please. I am using my laptop with disabled throttling (2 core, 2.27 Ghz) and all I gain is +1C~+3C on the CPU if a run with fixed frequency. Temperature increase only on CPU usage. I think your problem may be related to other devices.

Please post an output of:
```
sensors
```If is not installed, use this to install:
```
sudo apt-get install lm-sensors
```

i sense a lot of confidence in your post and thus gives me hope.
it does make some sense to me cause when i booted sabayon (gentoo directive) it was somewhat cooler and didnt heat up like on ubuntu/mint.
i will update asap.

_**[FONT=Arial][COLOR=Red] [update][/COLOR][/FONT]**_


p@p-VX6S ~ $ cpufreq-info
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to [email]cpufreq@vger.kernel.org[/email], please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 4294.55 ms.
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 4294.55 ms.
analyzing CPU 2:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 4294.55 ms.
analyzing CPU 3:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 4294.55 ms.


    [FONT=Courier New]p@p-VX6S ~ $ sudo sensors
    [sudo] password for p:
    acpitz-virtual-0
    Adapter: Virtual device
    temp1:        +26.8°C  (crit = +127.0°C)
    temp2:        +67.0°C  (crit = +98.0°C)

    coretemp-isa-0000[/FONT] [FONT=Courier New]
    Adapter: ISA adapter
    Core 0:       +65.0°C  (crit = +100.0°C)
    Core 1:       +67.0°C  (crit = +100.0°C)

    radeon-pci-0100[/FONT] [FONT=Courier New]
    Adapter: PCI adapter
    temp1:        +74.5°C 

    p@p-VX6S ~ $[/FONT] [FONT=Courier New]

[FONT=Arial][COLOR=Blue] output of top (seems firefox is hogging 25% of the cpu)[/COLOR][/FONT][/FONT][FONT=Courier New]


[FONT=Courier New]top - 06:36:08 up 5 min,  1 user,  load average: 1.24, 1.19, 0.61
Tasks: 147 total,   2 running, 144 sleeping,   0 stopped,   1 zombie
Cpu(s):  6.3%us,  0.7%sy,  0.0%ni, 92.9%id,  0.0%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:   6110456k total,  1094396k used,  5016060k free,    35352k buffers
Swap:  6284284k total,        0k used,  6284284k free,   604224k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                  
 2782 p         20   0  749m 101m  35m R   24  1.7   1:25.14 firefox                                  
 1538 root      20   0  194m  44m  15m S    3  0.8   0:30.74 Xorg                                     
 3302 p         20   0 17332 1308  952 R    1  0.0   0:00.49 top                                      
    3 root      20   0     0    0    0 S    0  0.0   0:00.70 ksoftirqd/0                              
 2476 p         20   0  420m  15m  11m S    0  0.3   0:01.58 mate-sensors-ap                          
 2479 p         20   0  413m  11m 8156 S    0  0.2   0:00.43 cpufreq-applet                           
    1 root      20   0 24452 2340 1352 S    0  0.0   0:02.12 init                                     
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd                                 
    4 root      20   0     0    0    0 S    0  0.0   0:00.04 kworker/0:0                              
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                              
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                              
   10 root      20   0     0    0    0 S    0  0.0   0:00.39 ksoftirqd/1                              
   12 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/2                              
   13 root      20   0     0    0    0 S    0  0.0   0:00.03 kworker/2:0                              
   14 root      20   0     0    0    0 S    0  0.0   0:00.45 ksoftirqd/2                              
   16 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/3                              
   17 root      20   0     0    0    0 S    0  0.0   0:00.01 kworker/3:0                              
   18 root      20   0     0    0    0 S    0  0.0   0:00.41 ksoftirqd/3                              
   20 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset                                   
   21 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper                                  
   22 root      20   0     0    0    0 S    0  0.0   0:00.00 kdevtmpfs                                
   23 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns                                    
   24 root      20   0     0    0    0 S    0  0.0   0:00.00 sync_supers                              
   25 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default                              
   26 root       0 -20     0    0    0 S    0  0.0   0:00.00 kintegrityd                              
   27 root       0 -20     0    0    0 S    0  0.0   0:00.00 kblockd                                  
   28 root       0 -20     0    0    0 S    0  0.0   0:00.00 ata_sff                                  
   29 root      20   0     0    0    0 S    0  0.0   0:00.00 khubd                                    
   30 root       0 -20     0    0    0 S    0  0.0   0:00.00 md                                       
   31 root      20   0     0    0    0 S    0  0.0   0:00.44 kworker/1:1                              
   32 root      20   0     0    0    0 S    0  0.0   0:00.00 khungtaskd                               
   33 root      20   0     0    0    0 S    0  0.0   0:00.00 kswapd0  [/FONT][/FONT][FONT=Courier New]

[FONT=Arial][COLOR=Blue] and with firefox closed:[/COLOR][/FONT][/FONT][FONT=Courier New]
top - 06:38:40 up 8 min,  1 user,  load average: 1.23, 1.21, 0.70
Tasks: 148 total,   1 running, 145 sleeping,   0 stopped,   2 zombie
Cpu(s):  0.9%us,  0.9%sy,  0.0%ni, 98.2%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   6110456k total,  1019992k used,  5090464k free,    35472k buffers
Swap:  6284284k total,        0k used,  6284284k free,   606060k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                  
 1538 root      20   0  184m  40m  15m S    4  0.7   0:40.12 Xorg                                     
 2840 p         20   0  519m  17m  11m S    2  0.3   0:03.82 mate-terminal                            
 2476 p         20   0  432m  15m  11m S    1  0.3   0:02.25 mate-sensors-ap                          
 3376 root      20   0 17332 1324  952 R    1  0.0   0:00.07 top                                      
    3 root      20   0     0    0    0 S    0  0.0   0:00.84 ksoftirqd/0                              
 1021 root      20   0     0    0    0 S    0  0.0   0:00.49 kworker/0:2                              
 2348 p         20   0 60652 4516 2636 S    0  0.1   0:01.06 mateconfd-2                              
    1 root      20   0 24452 2340 1352 S    0  0.0   0:02.12 init                                     
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd                                 
    4 root      20   0     0    0    0 S    0  0.0   0:00.04 kworker/0:0                              
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                              
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                              
   10 root      20   0     0    0    0 S    0  0.0   0:00.46 ksoftirqd/1                              
   12 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/2                              
   13 root      20   0     0    0    0 S    0  0.0   0:00.03 kworker/2:0                              
   14 root      20   0     0    0    0 S    0  0.0   0:00.55 ksoftirqd/2                              
   16 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/3                              
   18 root      20   0     0    0    0 S    0  0.0   0:00.50 ksoftirqd/3                              
   20 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset                                   
   21 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper                                  
   22 root      20   0     0    0    0 S    0  0.0   0:00.00 kdevtmpfs                                
   23 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns                                    
   24 root      20   0     0    0    0 S    0  0.0   0:00.00 sync_supers                              
   25 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default                              
   26 root       0 -20     0    0    0 S    0  0.0   0:00.00 kintegrityd                              
   27 root       0 -20     0    0    0 S    0  0.0   0:00.00 kblockd                                  
   28 root       0 -20     0    0    0 S    0  0.0   0:00.00 ata_sff                                  
   29 root      20   0     0    0    0 S    0  0.0   0:00.00 khubd                                    
   30 root       0 -20     0    0    0 S    0  0.0   0:00.00 md                                       
   31 root      20   0     0    0    0 S    0  0.0   0:00.52 kworker/1:1                              
   32 root      20   0     0    0    0 S    0  0.0   0:00.00 khungtaskd  [/FONT][FONT=Courier New]

[FONT=Arial][COLOR=Blue] and sensors again (with ff closed)[/COLOR][/FONT][/FONT][FONT=Courier New]

p@p-VX6S ~ $ sudo sensors[/FONT] [FONT=Courier New]
acpitz-virtual-0
Adapter: Virtual device
temp1:        +26.8°C  (crit = +127.0°C)
temp2:        +67.0°C  (crit = +98.0°C)

coretemp-isa-0000[/FONT] [FONT=Courier New]
Adapter: ISA adapter
Core 0:       +65.0°C  (crit = +100.0°C)
Core 1:       +67.0°C  (crit = +100.0°C)

radeon-pci-0100[/FONT] [FONT=Courier New]
Adapter: PCI adapter
temp1:        +73.5°C

_**see attachment if the formatting above is messy.**_
[/FONT]

---

### Post by typhoon_tip on 2012-06-17
Lolll ! Like my beginning post, install FGLRX driver from AMD and everything will be normal. The video card is frying everything up :popcorn:

EDIT: how did you install FGLRX ? Did you run the .run file directly ? If yes, post here if you are using 64 or 32 bits, and we will do a proper cleanup and install the drivers in the correct way.

---

### Post by cylent on 2012-06-17
> **typhoon_tip said:**
> Lolll ! Like my beginning post, install FGLRX driver from AMD and everything will be normal. The video card is frying everything up :popcorn:
sorry where did you get that conclusion from?
how did conclude that?

nevertheless i'll try and report.

---

### Post by typhoon_tip on 2012-06-17
> **cylent said:**
> sorry where did you get that conclusion from?
how did conclude that?

nevertheless i'll try and report.

Because I am running a laptop with AMD and run in the same issues all the time. The heat sink is connected to the GPU and CPU, so if one is low on temp and the other is frying, it gets indirectly cooked and fan is always running at max. This happens with open source radeon driver and with a wrongly installed AMD one.

---

### Post by cylent on 2012-06-17
> **typhoon_tip said:**
> Lolll ! Like my beginning post, install FGLRX driver from AMD and everything will be normal. The video card is frying everything up :popcorn:

EDIT: how did you install FGLRX ? Did you run the .run file directly ? If yes, post here if you are using 64 or 32 bits, and we will do a proper cleanup and install the drivers in the correct way.

64bit.

sudo sh ./amd-driver-installer-12-4-x86.x86_64.run 
and it installs just fine.

then i load the catalyst center and change the powerplay performance so its optimized for battery life.

is there anything else to try? its still a hot fan and i am still unhappy ...:confused:

---

### Post by typhoon_tip on 2012-06-18
> **cylent said:**
> 64bit.

sudo sh ./amd-driver-installer-12-4-x86.x86_64.run 
and it installs just fine.

then i load the catalyst center and change the powerplay performance so its optimized for battery life.

is there anything else to try? its still a hot fan and i am still unhappy ...:confused:

That's what I thought, is NOT the correct way to install in Ubuntu.

Now, purge first with the following:
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx:i386 libgl1-mesa-glx:amd64 libgl1-mesa-dri:i386 libgl1-mesa-dri:amd64 xserver-xorg-core
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo rm -rf /etc/ati
```

After you finish, reboot. Then, install as below:
```
sudo apt-get install build-essential cdbs dh-make dkms execstack dh-modaliases fakeroot
sudo apt-get install ia32-libs-multiarch:i386 lib32gcc1 libc6-i386
cd /usr ; sudo ln -svT lib /usr/lib64

```

Return to the directory where the .run file is located, then:
```
sh ./amd-driver-installer-12-4-x86.x86_64.run --buildpkg Ubuntu/precise
sudo dpkg -i fglrx*.deb
sudo amdconfig --initial -f
```

Remember ! _Do not skip any step_ !!

---

### Post by cylent on 2012-06-18
holy bonkers.

why so complicated?

and this will fix my heat issue and stop the massive power consumption?

---

### Post by typhoon_tip on 2012-06-18
> **cylent said:**
> holy bonkers.

why so complicated?

and this will fix my heat issue and stop the massive power consumption?

Is a sequence of commands... just do it and try, trust me.

And if you don't, just read the "how to" linked on the download page of AMD:
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)

:P

---

### Post by Jack Kelly on 2013-01-15
Hi there,

Are there any updates on this issue?  I believe I'm having the same problems as the original poster (and I don't have an AMD graphics subsystem)

I'm trying to throttle the CPU speed on my [Intel Atom D2700]("http://ark.intel.com/products/59683/Intel-Atom-Processor-D2700-1M-Cache-2_13-GHz") (Cedarview 32nm) on an [Intel Desktop Board D2700MUD]("http://ark.intel.com/products/56457/Intel-Desktop-Board-D2700MUD").  I'm running Ubuntu Server 12.10 64-bit.  I have the latest motherboard BIOS installed (0074).

I have installed [FONT=Courier New]cpufrequtils[/FONT].  When [FONT=Courier New]cpufrequtils[/FONT] was installed, I noticed these worrying messages:

```

Setting up libcpufreq0 (008-1) ...
Setting up cpufrequtils (008-1) ...
 * Loading cpufreq kernel modules...  [fail] 
 * CPUFreq Utilities: Setting ondemand CPUFreq governor... * disabled, governor not available... [ OK ] 

```

Then, when I run[FONT=Courier New] cpufreq-info[/FONT], I get these errors:

```

jack@logger:~$ cpufreq-info
cpufrequtils 008: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 4294.55 ms.
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 4294.55 ms.
analyzing CPU 2:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 4294.55 ms.
analyzing CPU 3:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 4294.55 ms.

```Also: I don't have a [FONT=Courier New]cpufreq[/FONT] directory in [FONT=Courier New]/sys/devices/system/cpu/cpu?/[/FONT]

Incidentally, I understand that Intel provide very little Linux support  for the graphics processor integrated onto the D2700 (because this  specific GMA core is based on PowerVR).  I wonder if Intel have also  failed to provide adequate Linux support for the frequency throttling on  this CPU?

---

### Post by Jack Kelly on 2013-01-15
Hmm... I'm coming to the conclusion that the D2700 simply doesn't support frequency throttling.

---

### Post by mikewhatever on 2013-01-16
From one of the previous posts, there was a /sys/devices/system/cpu/cpufreq directory. We've not explored it further, so what's in it?

---

### Post by Jack Kelly on 2013-01-17
> **mikewhatever said:**
> From one of the previous posts, there was a /sys/devices/system/cpu/cpufreq directory. We've not explored it further, so what's in it?

My D2700 Ubuntu system doesn't have that directory.

---

