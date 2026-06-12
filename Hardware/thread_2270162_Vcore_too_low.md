---
title: "Vcore too low?"
date: 2015-03-20
forum: Hardware
---

### Post by vitaoma on 2015-03-20
Hello there,

Recently, I have used "sensors" for verifying my CPU temperature, which turned out to be ok. However, I found out that my Vcore is perhaps too low.

```
vitaoma@vitaoma:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +40.0°C  (crit = +75.0°C)


nouveau-pci-0200
Adapter: PCI adapter
temp1:        +61.0°C  (high = +95.0°C, crit = +145.0°C)


atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.14 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +3.33 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +5.08 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +11.90 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     2136 RPM  (min =    0 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM)
CPU Temperature:    +48.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +49.0°C  (high = +70.0°C, crit = +125.0°C)

```

Is my CPU underclocking? What is happening, and how may I undo it?

Well, some more information (hope it helps):

```

[FONT=arial]vitaoma@vitaoma:~$ cat /proc/cpuinfo[/FONT]
[FONT=arial]processor       : 0[/FONT]
[FONT=arial]vendor_id       : GenuineIntel[/FONT]
[FONT=arial]cpu family      : 15[/FONT]
[FONT=arial]model           : 6[/FONT]
[FONT=arial]model name      : Intel(R) Pentium(R) D CPU 3.20GHz[/FONT]
[FONT=arial]stepping        : 5[/FONT]
[FONT=arial]microcode       : 0x7[/FONT]
[FONT=arial]cpu MHz         : 2400.000[/FONT]
[FONT=arial]cache size      : 2048 KB[/FONT]
[FONT=arial]physical id     : 0[/FONT]
[FONT=arial]siblings        : 2[/FONT]
[FONT=arial]core id         : 0[/FONT]
[FONT=arial]cpu cores       : 2[/FONT]
[FONT=arial]apicid          : 0[/FONT]
[FONT=arial]initial apicid  : 0[/FONT]
[FONT=arial]fdiv_bug        : no[/FONT]
[FONT=arial]hlt_bug         : no[/FONT]
[FONT=arial]f00f_bug        : no[/FONT]
[FONT=arial]coma_bug        : no[/FONT]
[FONT=arial]fpu             : yes[/FONT]
[FONT=arial]fpu_exception   : yes[/FONT]
[FONT=arial]cpuid level     : 6[/FONT]
[FONT=arial]wp              : yes[/FONT]
[FONT=arial]flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov[/FONT]
[FONT=arial]pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr pdcm lahf_lm[/FONT]
[FONT=arial]bogomips        : 6399.48[/FONT]
[FONT=arial]clflush size    : 64[/FONT]
[FONT=arial]cache_alignment : 128[/FONT]
[FONT=arial]address sizes   : 36 bits physical, 48 bits virtual[/FONT]
[FONT=arial]power management:[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]processor       : 1[/FONT]
[FONT=arial]vendor_id       : GenuineIntel[/FONT]
[FONT=arial]cpu family      : 15[/FONT]
[FONT=arial]model           : 6[/FONT]
[FONT=arial]model name      : Intel(R) Pentium(R) D CPU 3.20GHz[/FONT]
[FONT=arial]stepping        : 5[/FONT]
[FONT=arial]microcode       : 0x7[/FONT]
[FONT=arial]cpu MHz         : 2400.000[/FONT]
[FONT=arial]cache size      : 2048 KB[/FONT]
[FONT=arial]physical id     : 0[/FONT]
[FONT=arial]siblings        : 2[/FONT]
[FONT=arial]core id         : 1[/FONT]
[FONT=arial]cpu cores       : 2[/FONT]
[FONT=arial]apicid          : 1[/FONT]
[FONT=arial]initial apicid  : 1[/FONT]
[FONT=arial]fdiv_bug        : no[/FONT]
[FONT=arial]hlt_bug         : no[/FONT]
[FONT=arial]f00f_bug        : no[/FONT]
[FONT=arial]coma_bug        : no[/FONT]
[FONT=arial]fpu             : yes[/FONT]
[FONT=arial]fpu_exception   : yes[/FONT]
[FONT=arial]cpuid level     : 6[/FONT]
[FONT=arial]wp              : yes[/FONT]
[FONT=arial]flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov[/FONT]
[FONT=arial]pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr pdcm lahf_lm[/FONT]
[FONT=arial]bogomips        : 6399.48[/FONT]
[FONT=arial]clflush size    : 64[/FONT]
[FONT=arial]cache_alignment : 128[/FONT]
[FONT=arial]address sizes   : 36 bits physical, 48 bits virtual[/FONT]
[FONT=arial]power management:

[/FONT][FONT=arial]vitaoma@vitaoma:~$ sudo dmidecode -t 2[/FONT]
[FONT=arial]# dmidecode 2.11[/FONT]
[FONT=arial]SMBIOS 2.4 present.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Handle 0x0002, DMI type 2, 8 bytes[/FONT]
[FONT=arial]Base Board Information[/FONT]
[FONT=arial]        Manufacturer: ASUSTeK Computer INC.[/FONT]
[FONT=arial]        Product Name: P5VD2-X[/FONT]
[FONT=arial]        Version: 1.XX[/FONT]
[FONT=arial]        Serial Number: 123456789000[/FONT]

```

Thank you.

---

### Post by weatherman2 on 2015-03-20
Vcore is a voltage set automatically by the motherboard - unless you manually tried to change it to overclock.  If you are not having any issues, don't worry about it.

---

### Post by Yellow Pasque on 2015-03-21
> **vitaoma said:**
> Is my CPU underclocking? What is happening, and how may I undo it?

Yes, modern CPU's underclock and undervolt themselves at idle to save power (and cut down heat and fan noise).

---

