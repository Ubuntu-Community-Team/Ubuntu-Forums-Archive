---
title: "? Sony Vaio SZ - L2 Cache disabled !"
date: 2009-02-15
forum: Hardware
---

### Post by zongpog on 2009-02-15
Just noticed that the output of lshw lists the Sony Vaio SZ as having the L2 cache disabled.

I would be grateful if another owner would verify this for me so that I can work out if it is unique to mine, more general, or the tool is misreporting the information:

Tool is available from here, 
[http://ezix.sourceforge.net/software/lshw.html](http://ezix.sourceforge.net/software/lshw.html)
but on Ubuntu one can type :  # apt-get install lshw

# uname -a
Linux mynaffpc 2.6.24-23-generic #1 SMP Mon Jan 26 00:13:11 UTC 2009 i686 GNU/Linux

Output on mine is:
```

# lshw
mynaffpc                       
    description: Notebook
    product: VGN-SZ90PS
    vendor: Sony Corporation
    version: J001G09L
    serial: removed-removed
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31 smp-1.4 smp
    configuration: boot=normal chassis=notebook cpus=2 uuid=removed-removed-removed-removed
  *-core
       description: Motherboard
       product: VAIO
       vendor: Sony Corporation
       physical id: 0
       version: N/A
       serial: N/A
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: R0073N0 (04/14/2006)
          size: 110KiB
          capacity: 960KiB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect edd int9keyboard int10video acpi usb agp smart
battery biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Genuine Intel(R) CPU           T2600  @ 2.16GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          slot: N/A
          size: 2167MHz
          capacity: 2167MHz
          width: 32 bits
          clock: 166MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts ac
pi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc up arch_perfmon bts pni monitor vmx est tm2 xtpr cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1 DISABLED
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: burst internal write-back data
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3 Cache
             capabilities: burst data
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical

```

---

