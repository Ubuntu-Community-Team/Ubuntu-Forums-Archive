---
title: "HP dv6: i5 cpu is supported by ubuntu?"
date: 2010-11-30
forum: Hardware
---

### Post by mebitek on 2010-11-30
Hello I have an i5 M430 cpu on my HP dv6 laptop.
My question is if i5 cpu are fully supported on ubuntu (generally in linux).
I ask this cause my cpu seems to not work properly.

1° the kernel detects only 1 physical core, not 2 as intel specs ([http://ark.intel.com/Product.aspx?id=43537](http://ark.intel.com/Product.aspx?id=43537)). In fact I have 4 logical cores (threads) and just one physical as dmesg says:

[    0.000213] CPU: Physical Processor ID: 0
[    0.000214] CPU: Processor Core ID: 0
[    0.000229] mce: CPU supports 9 MCE banks
[    0.000240] CPU0: Thermal monitoring enabled (TM1)
........
[    0.061392] CPU0: Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz stepping 02
[    0.167920] Booting Node   0, Processors  #1
[    0.178107] Initializing CPU#1
[    0.260740]  #2
[    0.270956] Initializing CPU#2
[    0.353550]  #3
[    0.363765] Initializing CPU#3
[    0.444415] Brought up 4 CPUs
[    0.444418] Total of 4 processors activated (18087.19 BogoMIPS).

2° in /proc/acpi/processor I get:

mebitek@marmidha:/proc/acpi/processor$ cat CPU*/info
processor id:            0
acpi id:                 1
bus mastering control:   yes
power management:        no
throttling control:      yes
limit interface:         yes
processor id:            1
acpi id:                 2
bus mastering control:   yes
power management:        no
throttling control:      yes
limit interface:         yes
processor id:            2
acpi id:                 3
bus mastering control:   yes
power management:        no
throttling control:      yes
limit interface:         yes
processor id:            3
acpi id:                 4
bus mastering control:   yes
power management:        no
throttling control:      yes
limit interface:         yes

so I do not have cpu power managment that means a poor battery life (I have about 1h 20mins)

3° Intel Corporation 5 Series/3400 Series chipset do not have sensors. I used a patch found on lm_sensors page to get support for P55 chipset and now I get:

intel-pci-00fe
Adapter: PCI adapter
thermal sensor:      +122.0°C                                    
core 0:               +55.5°C                                    
processor:            +58.0°C                                    
internal temperature: +62.0°C

really strange value for thermal sensor.

4° I have no fan. I can load the module but /proac/acpi/fan directory is empty.

5° i7z reports good values for number of physical cores, turbo mode and frequencies.

I notice that I have disassebled my DSDT, correct all errors and warnigns (I alsa tried to merge DSDT and SSDT table with acpi_no_auto_ssdt) but what I get is only a kernel panic at boot.

Someone can help me?
thx a lot
Claudio

---

