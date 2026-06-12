---
title: "More options on Cpu frequency scaling with Intel core 2 duo t5600"
date: 2009-10-30
forum: Hardware
---

### Post by Lantius on 2009-10-30
hi guys ! 

I have been looking for information about scaling cpu. 

I have a intel core 2 duo t5600 working under a toshiba u200-196 ( [http://es.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=ES&BV_UseBVCookie=yes&PRODUCT_ID=120535](http://es.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=ES&BV_UseBVCookie=yes&PRODUCT_ID=120535)) with bios 3.70, running ubuntu 9.04.

I am able to scale the cpu but in windows it has 5 levels, in linux I can decide only between 1.83, 1.33 and 1.0 ghz. 

I would like to decide something lower, I don't know if it's something possible with this CPU.

I have been googling information, but I only find ways to make the cpu scaling works, no to increase the range of speeds. 

Does anyone know if it is possible to gain more speeds of processor?

PD:
lshw with important information about cpu

> fulgor                    
    description: Notebook
    product: SATELLITE U200
    vendor: TOSHIBA
    version: PLUA0E-06H031SP
    serial: X6644903G
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=notebook frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled uuid=AFFFC480-267B-18F4-8010-C80686644903
  *-core
       description: Motherboard
       product: Portable PC
       vendor: TOSHIBA
       physical id: 0
       version: Version A0
       serial: $$C06XPAWA
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: Version 3.70 (06/04/2007)
          size: 128KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing vesa cdboot bootselect edd int13floppytoshiba int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          slot: uFC-PGA Socket
          size: 1GHz
          capacity: 1830MHz
          width: 64 bits
          clock: 166MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall x86-64 constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow cpufreq
        *-cache:0
             description: L1 cache
             physical id: 12
             slot: CPU Internal
             size: 128KiB
             capacity: 128KiB
             clock: 1GHz (1.0ns)
             capabilities: internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 13
             slot: CPU Internal
             size: 2MiB
             capacity: 2MiB
             clock: 1GHz (1.0ns)
             capabilities: internal write-back unified


---

