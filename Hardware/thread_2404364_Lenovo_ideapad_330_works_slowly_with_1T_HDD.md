---
title: "Lenovo ideapad 330 works slowly with 1T HDD"
date: 2018-10-23
forum: Hardware
---

### Post by ntpndcmb on 2018-10-23
Hello everyone,
It's my the first message on this forum, so I am sorry If some wrong in the post.

Problem: Lenovo ideapad 330 works slowly with 1T HDD
Can you give me some advice to resolve the problem.

I found out "configuration: driver=ahci latency=64" in lshw out.
Maybe it is reason this problem.

Also I found description of problem for window: [https://forums.lenovo.com/t5/Lenovo-IdeaPad-1xx-3xx-5xx-7xx/New-Ideapad-320-really-slow/td-p/3763971](https://forums.lenovo.com/t5/Lenovo-IdeaPad-1xx-3xx-5xx-7xx/New-Ideapad-320-really-slow/td-p/3763971)

>> The link takes you to the speed test for the Lenovo 320 - as you can see, the speed is very patchy and dire at small file sizes.
>> It's even worse at file sizes smaller than 4MB (between 3MB/sec and 5MB/sec in some instances) whereas,
>> for the HP, the slowest speed (1MB file transfer size) is around 15MB/sec and much faster at 2MB, 4MB and beyond.
>> If people want to see the results for file sizes between 1MB and 8192MB, they only have to shout.
>> Do your own tests, though, using ATTO Benchmark (it's free but requires registration) - or your preferred tester.


Parameters of system:

```
Linux: Ubuntu 18.04
> uname -a
4.18.16-041816-lowlatency #201810200431 SMP PREEMPT Sat Oct 20 08:36:51 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

> lshw
  description: Notebook
    product: 81D6 (LENOVO_MT_81D6_BU_idea_FM_ideapad 330-15AST)
    vendor: LENOVO
    version: Lenovo ideapad 330-15AST
    serial: PF170D5B
    width: 64 bits
    capabilities: smbios-3.0 dmi-3.0 smp vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=notebook family=ideapad 330-15AST frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled sku=LENOVO_MT_81
D6_BU_idea_FM_ideapad 330-15AST uuid=1A044387-734E-E811-9379-8C164577AA7B
  *-core
       description: Motherboard
       product: LNVNB161216
       vendor: LENOVO
       physical id: 0
       version: No DPK
       serial: PF170D5B
       slot: Chassis Location Unknown
     *-cache:0
          description: L1 cache
          physical id: 21
          slot: L1 Cache
          size: 160KiB
          capacity: 160KiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: 22
          slot: L2 Cache
          size: 1MiB
          capacity: 1MiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
          configuration: level=2
     *-cpu
          description: CPU
          product: AMD A9-9425 RADEON R5, 5 COMPUTE CORES 2C+3G
          vendor: Advanced Micro Devices [AMD]
          physical id: 20
          bus info: cpu@0
          version: AMD A9-9425 RADEON R5, 5 COMPUTE CORES 2C+3G
          slot: Socket FS1r2
          size: 3689MHz
          width: 64 bits
          clock: 100MHz

....
       *-storage
             description: SATA controller
             product: FCH SATA Controller [AHCI mode]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 4b
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=64
             resources: irq:34 ioport:3118(size=8) ioport:3124(size=4) ioport:3110(size=8) ioport:3120(size=4) ioport:3100(size=16) memory:f0d6c000-f0d6c3ff
...
 *-scsi
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD10SPZX-24Z
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 1A01
             serial: WD-WX51A2890Z1Y
             size: 931GiB (1TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=203b89d8-c5dc-41d2-971c-b7fd754bff6e logicalsectorsize=512 sectorsize=4096
```

---

