---
title: "Speedstep not working"
date: 2008-06-03
forum: Hardware
---

### Post by indifference on 2008-06-03
Hello,

I'm trying to run acpi-cpufreq in my laptop, but without sucess.
In Ubuntu Feisty everything works fine, but not in Hardy (in Gutsy I didn't test it).

When I try load the module acpi-cpufreq it shows:

> FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.24-17-generic/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device

In the boot messages:

> 
[    9.118245] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
....
[   31.884921] ACPI Exception (processor_perflib-0234): AE_NOT_FOUND, Evaluating _PSS [20070126]
....
[  269.465523] ACPI Exception (processor_perflib-0234): AE_NOT_FOUND, Evaluating _PSS [20070126]
[  503.785571] ACPI Exception (processor_perflib-0234): AE_NOT_FOUND, Evaluating _PSS [20070126]

My hardware:

> description: Notebook
    product: TravelMate 2300
    vendor: Acer
    version: Rev 1
    serial: LXT73050254470732EEM00
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: boot=oem-specific chassis=notebook uuid=601B72A8-32DA-D811-9837-00C09F676B74
  *-core
       description: Motherboard
       product: TravelMate 2300
       vendor: Acer
       physical id: 0
       version: Rev 1.0
       serial: LXT73050254470732EEM00
     *-firmware
          description: BIOS
          vendor: ACER
          physical id: 0
          version: 3A07 (08/03/2004)
          size: 106KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb sm
artbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.50GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.13.6
          slot: uFCPGA2
          size: 1500MHz
          capacity: 1500MHz
          width: 32 bits
          clock: 400MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts est tm2


Can you help me?

Thanks for reading,

Pedro Saraiva

---

