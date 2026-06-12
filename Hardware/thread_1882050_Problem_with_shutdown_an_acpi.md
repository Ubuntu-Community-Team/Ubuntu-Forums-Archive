---
title: "Problem with shutdown an acpi"
date: 2011-11-16
forum: Hardware
---

### Post by woernsn on 2011-11-16
Hi community :)

After searching a fix for this problem for a long time, I thought I should ask here.

I've got a new notebook (chiliGREEN) and installed ubuntu (of course) 64x (11.10).
Now I have the problem, that the notebook desn't want to shut down..

It always stucks at "System will hold now".

The only way to solve the problem - so far I could find out till now - is to write "acpi=off" into the /etc/default/grub"-file.

If I am doing this, the notebook comes till "System halted" and i have to press the power-button shortly to turn of the device.

The problem is, that if i use "acpi=off", I can not control my brightness level any or see my battery state any longer..
And this (first of all - the battery) is very import for me.

So - is there any solution with that I can do both? Shutting down AND using acpi?

Thanks in advance..
I'm going crazy..

---

### Post by matt_symes on 2011-11-16
Hi

Is your BIOS up to date ?

Kind regards

---

### Post by woernsn on 2011-11-17
Thanks for the hint..

It's pretty a bit deal to update the bios..

I have to try it with WindowsPE and hoping that it will work.

I will post again, if it is done ;)

---

### Post by woernsn on 2011-11-21
Wow.. i REALLY don't like Windows ;)
After searching about 5 hours, I found out that I own a "Compal" notebook with a "CBL21" motherboard. But I wasn't able to find out, if there is a bios update for me..
I'll ask the chiligreen support about it, but I don't have big hope..

Sooo.. are there maybe other solutions?

---

### Post by matt_symes on 2011-11-21
Hi

It may be a dodgy ACPI (that's why i suggested a BIOS update) or it may be a kernel module that is causing the issue.

If, from the terminal, you type

```
sudo shutdown -h now
```does it shut down correctly without the ACPI option ?

Have you tried unloading kernel modules before shutting down ?

Kind regard

---

### Post by woernsn on 2011-11-21
Of course.. i tired without every acpi-entry in the grub at first (by default there wasn't a acpi-entry ;) )

How to unload modules? And what modules?

Thanks

---

### Post by matt_symes on 2011-11-21
Hi

These problems can be a pain to track down and i feel quite sorry for you. 

My initial thoughts would be try to get a  BIOS  update. The rest are moot if a BIOS update will fix your problem.

You can also try some of other ACPI kernel command line options. *acpi=off* is a real kludge as it switches the entire ACPI subsystem off in the kernel. There are some other switches you can try here.

[http://www.lesswatts.org/projects/acpi/debug.php](http://www.lesswatts.org/projects/acpi/debug.php)

One of the things i have read in the past is what you are seeing can be caused by a kernel module or hardware misbehaving at shutdown.

You can list your kernel modules with

```
lsmod
```

This command can be used to remove a module.

```
sudo modprobe -r <module_name>
```

I would start by removing your wireless and ethernet drivers and then attempt to shutdown, if that fails move onto others.

Some you will not be able to remove as they will be in use.

I would not bother with anything else until you have a definitive answer for a BIOS update though.

Kind regards

---

### Post by woernsn on 2011-11-22
I just got an answer from the chiligreen-support: There's no bios-update because there is no known problem with the actual one (windows device grrr)..

And I can't disable modules.. it always says "... is in use."

:(

Is it possible that other Distrubutions don't have this problem?

Thanks for your help!

---

### Post by matt_symes on 2011-11-22
Hi

> **woernsn said:**
> I just got an answer from the chiligreen-support: There's no bios-update because there is no known problem with the actual one (windows device grrr)..

Yep. Sounds about right. The command
```

dmesg | grep -i acpi
```may point to some obvious errors is you would like to post it.

> 
And I can't disable modules.. it always says "... is in use."
You should be able to remove some such as you wireless driver and Ethernet driver before shutting down.

> 
Is it possible that other Distrubutions don't have this problem?

Thanks for your help!ACPI support is build into the kernel but it does use some kernel loadable modules so maybe.

Did you try some of the other ACPI options listed in the link i posted ?

Kind regards

---

### Post by woernsn on 2011-11-24
dmesg | grep -i acpi:
```

[    0.000000] Command line: root=/dev/sda1 resume=/dev/disk/by-id/ata-SAMSUNG_HN-M750MBB_S2R9J9EB701254-part3 splash=silent quiet vga=0x34d acpi=oldboot
[    0.000000]  BIOS-e820: 00000000af6bf000 - 00000000af7bf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000af7bf000 - 00000000af7ff000 (ACPI data)
[    0.000000] Malformed early option 'acpi'
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 QUANMX)
[    0.000000] ACPI: XSDT 00000000af7fe120 0008C (v01 QUANMX QUANMAX1 00000001      01000013)
[    0.000000] ACPI: FACP 00000000af7fc000 000F4 (v04 QUANMX QUANMAX1 00000001 ACPI 00040000)
[    0.000000] ACPI: DSDT 00000000af7f0000 08D16 (v01 QUANMX QUANMAX1 00000000 ACPI 00040000)
[    0.000000] ACPI: FACS 00000000af74e000 00040
[    0.000000] ACPI: ASF! 00000000af7fd000 000A5 (v32 QUANMX QUANMAX1 00000001 ACPI 00040000)
[    0.000000] ACPI: HPET 00000000af7fb000 00038 (v01 QUANMX QUANMAX1 00000001 ACPI 00040000)
[    0.000000] ACPI: APIC 00000000af7fa000 0008C (v02 QUANMX QUANMAX1 00000001 ACPI 00040000)
[    0.000000] ACPI: MCFG 00000000af7f9000 0003C (v01 QUANMX QUANMAX1 00000001 ACPI 00040000)
[    0.000000] ACPI: SLIC 00000000af7ef000 00176 (v01 QUANMX QUANMAX1 00000001 ACPI 00040000)
[    0.000000] ACPI: WDAT 00000000af7ee000 00224 (v01 QUANMX QUANMAX1 00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 00000000af7ed000 006FE (v01 QUANMX QUANMAX1 00001000 ACPI 00040000)
[    0.000000] ACPI: BOOT 00000000af7eb000 00028 (v01 QUANMX QUANMAX1 00000001 ACPI 00040000)
[    0.000000] ACPI: ASPT 00000000af7e8000 00034 (v07 QUANMX QUANMAX1 00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 00000000af7e7000 007C2 (v01 QUANMX QUANMAX1 00003000 ACPI 00040000)
[    0.000000] ACPI: SSDT 00000000af7e6000 00996 (v01 QUANMX QUANMAX1 00003000 ACPI 00040000)
[    0.000000] ACPI: DMAR 00000000af7e5000 000B0 (v01 QUANMX QUANMAX1 00000001 ACPI 00040000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Kernel command line: root=/dev/sda1 resume=/dev/disk/by-id/ata-SAMSUNG_HN-M750MBB_S2R9J9EB701254-part3 splash=silent quiet vga=0x34d acpi=oldboot
[    0.004217] ACPI: Core revision 20110623
[    0.441201] PM: Registering ACPI NVS region at af6bf000 (1048576 bytes)
[    0.441569] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.441571] ACPI: bus type pci registered
[    0.476768] ACPI: Added _OSI(Module Device)
[    0.476770] ACPI: Added _OSI(Processor Device)
[    0.476772] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.476773] ACPI: Added _OSI(Processor Aggregator Device)
[    0.478371] ACPI: EC: Look up EC in DSDT
[    0.479955] ACPI: Executed 1 blocks of module-level executable AML code
[    0.484255] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.484788] ACPI: SSDT 00000000af670718 0067C (v01  PmRef  Cpu0Cst 00003001 INTL 20100121)
[    0.485205] ACPI: Dynamic OEM Table Load:
[    0.485207] ACPI: SSDT           (null) 0067C (v01  PmRef  Cpu0Cst 00003001 INTL 20100121)
[    0.487915] ACPI: SSDT 00000000af671a98 00303 (v01  PmRef    ApIst 00003000 INTL 20100121)
[    0.488384] ACPI: Dynamic OEM Table Load:
[    0.488386] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20100121)
[    0.491712] ACPI: SSDT 00000000af66fd98 00119 (v01  PmRef    ApCst 00003000 INTL 20100121)
[    0.492119] ACPI: Dynamic OEM Table Load:
[    0.492121] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20100121)
[    0.495422] ACPI: Interpreter enabled
[    0.495425] ACPI: (supports S0 S3 S4 S5)
[    0.495448] ACPI: Using IOAPIC for interrupt routing
[    0.617814] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.618184] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.619347] ACPI: Power Resource [FN00] (off)
[    0.619437] ACPI: Power Resource [FN01] (off)
[    0.619828] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.620014] ACPI: No dock devices found.
[    0.620018] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.620445] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.631168] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.631341] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.631381] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.631420] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.631457] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.631507] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG0._PRT]
[    0.631608]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.631652]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
[    0.631653] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.635500] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
[    0.635557] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.635611] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.635668] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.635722] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.635776] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
[    0.635829] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.635883] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.636254] PCI: Using ACPI for IRQ routing
[    0.653704] pnp: PnP ACPI init
[    0.653715] ACPI: bus type pnp registered
[    0.654175] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.654212] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.654236] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.654337] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.654374] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.654463] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.654495] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.654547] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.713774] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.713813] pnp 00:09: Plug and Play ACPI device, IDs SYN072f SYN0700 SYN0002 PNP0f13 (active)
[    0.714011] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.714294] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.714317] pnp: PnP ACPI: found 12 devices
[    0.714318] ACPI: ACPI bus type pnp unregistered
[    3.356777] ACPI: acpi_idle yielding to intel_idle
[    3.373451] ACPI: Thermal Zone [TZ00] (0 C)
[    3.373548] ACPI: Fan [FAN0] (off)
[    3.373591] ACPI: Fan [FAN1] (off)
[   11.652847] ACPI: Lid Switch [LID0]
[   11.652942] ACPI: Sleep Button [SLPB]
[   11.653023] ACPI: Power Button [PWRF]
[   11.686434] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   11.842984] acpi device:30: registered as cooling_device6
[   11.843291] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   11.882329] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[   11.942348] ACPI: AC Adapter [ACAD] (on-line)
[   12.143325] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[   12.143334] ACPI: Battery Slot [BAT1] (battery present)
[   19.502484] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   19.502489] nvidia 0000:01:00.0: power state changed by ACPI to D0

```And I tried the other acpi-options -> didn't help at all..
I'm beginning to cry :(

---

### Post by matt_symes on 2011-11-24
Hi

You have a buggy ACPI.
[FONT=monospace]
[/FONT]```
[FONT=monospace][    0.617814] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness 
[    0.618184] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness [/FONT]
```
[FONT=monospace]
[/FONT]```
[    0.631652]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d 
```[FONT=monospace]
[/FONT]```
[   11.686434] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness 
```This is interesting.

```
[    0.484255] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
```Try booting with *acpi=linux*. If not then i am crying with you :P

Kind regards

---

### Post by woernsn on 2011-11-25
> **matt_symes said:**
> Hi

You have a buggy ACPI.
[FONT=monospace]
[/FONT]```
[FONT=monospace][    0.617814] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness 
[    0.618184] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness [/FONT]
```[FONT=monospace]
[/FONT]```
[    0.631652]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d 
```[FONT=monospace]
[/FONT]```
[   11.686434] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness 
```This is interesting.

```
[    0.484255] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
```Try booting with *acpi=linux*. If not then i am crying with you :P

Kind regards

FINALLY.. i solved the problem:
I installed openSuse (because of trying other distros) and here it works with following kernel-parameters:
```
[COLOR="white"]acpi_os=Windows[/COLOR] noapic
```With this, **everything** works! Brightness, shutting down, wlan (didn't work with *[COLOR="White"]acpi_os=Windows[/COLOR] nolapic*) (what i tried before).

I don't know if it also works with ubuntu, but i think so.
I'm finally happy with a stable system, that works :D

Thank you very much for your time and help!

---

### Post by matt_symes on 2011-11-25
Hi

I didn't really help you. I think you did it yourself.

BTW: Thanks for posting the solution.

Please can you mark this thread as solved using the thread tools.

Kind regards

---

### Post by FedorV on 2012-04-21
Greetings,
i used Ubuntu 11.04 and 12.04 - on both is the equal problem detected:
normal shutdown works without any problems (shutdown -h now)
but when i'm trying to use sleep or hibernate feature - notebook start with some disk operations and black screen, then after aprox. 30 seconds freezes (no disk operations, black screen, no output or any replyies on keyboard inputs..)

And here is my "dmesg | grep -i acpi" output:

```
[    0.000000]  BIOS-e820: 00000000aaf24000 - 00000000aafe8000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000aaffd000 - 00000000ab000000 (ACPI data)
[    0.000000] ACPI: RSDP 00000000000f0430 00024 (v02 _ASUS_)
[    0.000000] ACPI: XSDT 00000000aaffee18 0006C (v01 _ASUS_ Notebook 06222004 MSFT 00010013)
[    0.000000] ACPI: FACP 00000000aaf9ad98 000F4 (v04 _ASUS_ Notebook 06222004 MSFT 00010013)
[    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20110623/tbfadt-365)
[    0.000000] ACPI Warning: 32/64X FACS address mismatch in FADT - 0xAAFE4E40/0x00000000AAFE4D40, using 32 (20110623/tbfadt-489)
[    0.000000] ACPI: DSDT 00000000aaf86018 13512 (v01 _ASUS_ Notebook 00000000 INTL 20091112)
[    0.000000] ACPI: FACS 00000000aafe4e40 00040
[    0.000000] ACPI: APIC 00000000aaffdf18 000CC (v02 _ASUS_ Notebook 06222004 MSFT 00010013)
[    0.000000] ACPI: DBGP 00000000aaffff18 00034 (v01 _ASUS_ Notebook 06222004 MSFT 00010013)
[    0.000000] ACPI: ECDT 00000000aafe4b18 000C1 (v01 _ASUS_ Notebook 06222004 AMI. 00000003)
[    0.000000] ACPI: HPET 00000000aafe5d18 00038 (v01 _ASUS_ Notebook 06222004 AMI. 00000003)
[    0.000000] ACPI: MCFG 00000000aafe5c98 0003C (v01 _ASUS_ Notebook 06222004 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000aaf85818 007C9 (v01  PmRef  Cpu0Ist 00003000 INTL 20091112)
[    0.000000] ACPI: SSDT 00000000aaf84018 00996 (v01  PmRef    CpuPm 00003000 INTL 20091112)
[    0.000000] ACPI: ASF! 00000000aafe4a18 000A0 (v32 INTEL       HCG 00000001 TFSM 000F4240)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x06] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x08] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x09] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x0a] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x0b] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x0c] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x0d] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x0e] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x0f] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.004729] ACPI: Core revision 20110623
[    0.636607] PM: Registering ACPI NVS region at aaf24000 (802816 bytes)
[    0.637497] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.637500] ACPI: bus type pci registered
[    0.655177] ACPI: Added _OSI(Module Device)
[    0.655179] ACPI: Added _OSI(Processor Device)
[    0.655180] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.655182] ACPI: Added _OSI(Processor Aggregator Device)
[    0.657513] ACPI: EC: EC description table is found, configuring boot EC
[    0.657519] ACPI: EC: Look up EC in DSDT
[    0.659988] ACPI: Executed 1 blocks of module-level executable AML code
[    0.684064] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.788659] ACPI: SSDT 00000000aadca798 00754 (v01  PmRef  Cpu0Cst 00003001 INTL 20091112)
[    0.789249] ACPI: Dynamic OEM Table Load:
[    0.789252] ACPI: SSDT           (null) 00754 (v01  PmRef  Cpu0Cst 00003001 INTL 20091112)
[    0.820195] ACPI: SSDT 00000000aadcba98 00303 (v01  PmRef    ApIst 00003000 INTL 20091112)
[    0.820815] ACPI: Dynamic OEM Table Load:
[    0.820817] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20091112)
[    0.844058] ACPI: SSDT 00000000aadc9d98 00119 (v01  PmRef    ApCst 00003000 INTL 20091112)
[    0.844655] ACPI: Dynamic OEM Table Load:
[    0.844657] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20091112)
[    0.876454] ACPI: Interpreter enabled
[    0.876460] ACPI: (supports S0 S3 S4 S5)
[    0.876483] ACPI: Using IOAPIC for interrupt routing
[    0.997042] ACPI: EC: GPE = 0x1b, I/O: command/status = 0x66, data = 0x62
[    0.997312] ACPI: No dock devices found.
[    0.997317] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.997761] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    1.027945] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.028066] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG0._PRT]
[    1.028133] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    1.028161] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    1.028192] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    1.028225] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    1.028410]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    1.028692]  pci0000:00: ACPI _OSC control (0x1d) granted
[    1.756032] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12)
[    1.756075] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 12)
[    1.756115] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 12)
[    1.756155] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 12)
[    1.756200] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 12) *0, disabled.
[    1.756241] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 12) *0, disabled.
[    1.756282] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 12)
[    1.756325] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 12)
[    1.756750] PCI: Using ACPI for IRQ routing
[    1.765948] pnp: PnP ACPI init
[    1.765960] ACPI: bus type pnp registered
[    1.766293] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    1.816595] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.816621] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    1.816721] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    1.816760] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.816855] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.816887] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.816938] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    1.816981] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.817036] pnp 00:09: Plug and Play ACPI device, IDs SYN0a06 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
[    1.817080] pnp 00:0a: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    1.817385] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.817477] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.817632] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.817651] pnp: PnP ACPI: found 14 devices
[    1.817652] ACPI: ACPI bus type pnp unregistered
[    2.184335] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    2.184406] ACPI: AC Adapter [AC0] (on-line)
[    2.200432] ACPI: Lid Switch [LID]
[    2.200473] ACPI: Sleep Button [SLPB]
[    2.200505] ACPI: Power Button [PWRF]
[    2.253814] ACPI: Thermal Zone [THRM] (58 C)
[    2.253833] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    2.253840] ACPI: Battery Slot [BAT0] (battery present)
[    2.267907] ACPI: Battery Slot [BAT0] (battery present)
[    2.561266] acpi device:0e: hash matches
[    2.667830] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    2.677413] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[    2.677426] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.736569] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    2.736866] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[    2.736877] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[   36.341261] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   36.341267] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   36.507298] asus_wmi: Backlight controlled by ACPI video driver
[   36.955551] ACPI Warning: _BQC returned an invalid level (20110623/video-480)
[   36.955791] acpi device:04: registered as cooling_device4
[   36.956052] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   36.979403] ACPI Warning: _BQC returned an invalid level (20110623/video-480)
[   36.979708] acpi device:47: registered as cooling_device5
[   36.980143] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   38.437017] acpi_call: Module loaded successfully
[   38.438849] acpi_call: Calling \_SB.PCI0.PEG0.GFX0.DOFF
[   38.457897] acpi_call: Call successful: 0x0
root@fva-i5:/etc/grub.d# dmesg | grep -i acpi
[    0.000000]  BIOS-e820: 00000000aaf24000 - 00000000aafe8000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000aaffd000 - 00000000ab000000 (ACPI data)
[    0.000000] ACPI: RSDP 00000000000f0430 00024 (v02 _ASUS_)
[    0.000000] ACPI: XSDT 00000000aaffee18 0006C (v01 _ASUS_ Notebook 06222004 MSFT 00010013)
[    0.000000] ACPI: FACP 00000000aaf9ad98 000F4 (v04 _ASUS_ Notebook 06222004 MSFT 00010013)
[    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20110623/tbfadt-365)
[    0.000000] ACPI Warning: 32/64X FACS address mismatch in FADT - 0xAAFE4E40/0x00000000AAFE4D40, using 32 (20110623/tbfadt-489)
[    0.000000] ACPI: DSDT 00000000aaf86018 13512 (v01 _ASUS_ Notebook 00000000 INTL 20091112)
[    0.000000] ACPI: FACS 00000000aafe4e40 00040
[    0.000000] ACPI: APIC 00000000aaffdf18 000CC (v02 _ASUS_ Notebook 06222004 MSFT 00010013)
[    0.000000] ACPI: DBGP 00000000aaffff18 00034 (v01 _ASUS_ Notebook 06222004 MSFT 00010013)
[    0.000000] ACPI: ECDT 00000000aafe4b18 000C1 (v01 _ASUS_ Notebook 06222004 AMI. 00000003)
[    0.000000] ACPI: HPET 00000000aafe5d18 00038 (v01 _ASUS_ Notebook 06222004 AMI. 00000003)
[    0.000000] ACPI: MCFG 00000000aafe5c98 0003C (v01 _ASUS_ Notebook 06222004 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000aaf85818 007C9 (v01  PmRef  Cpu0Ist 00003000 INTL 20091112)
[    0.000000] ACPI: SSDT 00000000aaf84018 00996 (v01  PmRef    CpuPm 00003000 INTL 20091112)
[    0.000000] ACPI: ASF! 00000000aafe4a18 000A0 (v32 INTEL       HCG 00000001 TFSM 000F4240)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x06] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x08] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x09] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x0a] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x0b] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x0c] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x0d] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x0e] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x0f] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.004729] ACPI: Core revision 20110623
[    0.636607] PM: Registering ACPI NVS region at aaf24000 (802816 bytes)
[    0.637497] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.637500] ACPI: bus type pci registered
[    0.655177] ACPI: Added _OSI(Module Device)
[    0.655179] ACPI: Added _OSI(Processor Device)
[    0.655180] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.655182] ACPI: Added _OSI(Processor Aggregator Device)
[    0.657513] ACPI: EC: EC description table is found, configuring boot EC
[    0.657519] ACPI: EC: Look up EC in DSDT
[    0.659988] ACPI: Executed 1 blocks of module-level executable AML code
[    0.684064] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.788659] ACPI: SSDT 00000000aadca798 00754 (v01  PmRef  Cpu0Cst 00003001 INTL 20091112)
[    0.789249] ACPI: Dynamic OEM Table Load:
[    0.789252] ACPI: SSDT           (null) 00754 (v01  PmRef  Cpu0Cst 00003001 INTL 20091112)
[    0.820195] ACPI: SSDT 00000000aadcba98 00303 (v01  PmRef    ApIst 00003000 INTL 20091112)
[    0.820815] ACPI: Dynamic OEM Table Load:
[    0.820817] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20091112)
[    0.844058] ACPI: SSDT 00000000aadc9d98 00119 (v01  PmRef    ApCst 00003000 INTL 20091112)
[    0.844655] ACPI: Dynamic OEM Table Load:
[    0.844657] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20091112)
[    0.876454] ACPI: Interpreter enabled
[    0.876460] ACPI: (supports S0 S3 S4 S5)
[    0.876483] ACPI: Using IOAPIC for interrupt routing
[    0.997042] ACPI: EC: GPE = 0x1b, I/O: command/status = 0x66, data = 0x62
[    0.997312] ACPI: No dock devices found.
[    0.997317] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.997761] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    1.027945] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.028066] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG0._PRT]
[    1.028133] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    1.028161] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    1.028192] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    1.028225] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    1.028410]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    1.028692]  pci0000:00: ACPI _OSC control (0x1d) granted
[    1.756032] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12)
[    1.756075] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 12)
[    1.756115] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 12)
[    1.756155] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 12)
[    1.756200] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 12) *0, disabled.
[    1.756241] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 12) *0, disabled.
[    1.756282] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 12)
[    1.756325] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 12)
[    1.756750] PCI: Using ACPI for IRQ routing
[    1.765948] pnp: PnP ACPI init
[    1.765960] ACPI: bus type pnp registered
[    1.766293] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    1.816595] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.816621] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    1.816721] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    1.816760] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.816855] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.816887] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.816938] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    1.816981] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.817036] pnp 00:09: Plug and Play ACPI device, IDs SYN0a06 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
[    1.817080] pnp 00:0a: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    1.817385] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.817477] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.817632] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.817651] pnp: PnP ACPI: found 14 devices
[    1.817652] ACPI: ACPI bus type pnp unregistered
[    2.184335] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    2.184406] ACPI: AC Adapter [AC0] (on-line)
[    2.200432] ACPI: Lid Switch [LID]
[    2.200473] ACPI: Sleep Button [SLPB]
[    2.200505] ACPI: Power Button [PWRF]
[    2.253814] ACPI: Thermal Zone [THRM] (58 C)
[    2.253833] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    2.253840] ACPI: Battery Slot [BAT0] (battery present)
[    2.267907] ACPI: Battery Slot [BAT0] (battery present)
[    2.561266] acpi device:0e: hash matches
[    2.667830] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    2.677413] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[    2.677426] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.736569] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    2.736866] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[    2.736877] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[   36.341261] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   36.341267] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   36.507298] asus_wmi: Backlight controlled by ACPI video driver
[   36.955551] ACPI Warning: _BQC returned an invalid level (20110623/video-480)
[   36.955791] acpi device:04: registered as cooling_device4
[   36.956052] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   36.979403] ACPI Warning: _BQC returned an invalid level (20110623/video-480)
[   36.979708] acpi device:47: registered as cooling_device5
[   36.980143] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   38.437017] acpi_call: Module loaded successfully
[   38.438849] acpi_call: Calling \_SB.PCI0.PEG0.GFX0.DOFF
[   38.457897] acpi_call: Call successful: 0x0
```

The notebook itself is Asus U36S.. Any hints? Moving to Suse is not option to me :).

---

