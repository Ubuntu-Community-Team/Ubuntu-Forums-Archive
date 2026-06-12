---
title: "Can't boot after enabling XMP"
date: 2009-11-15
forum: Hardware
---

### Post by ad_267 on 2009-11-15
I just bought a new computer. It has an Intel i5 750 processor, a Gigabyte P55A-UD4 motherboard and 4 GB of Kingston HyperX DDR3 RAM.

The RAM supports XMP and can run at 1600 MHz, but runs at 1333 MHz by default. I tried to enable XMP from the BIOS by setting it to profile 1, but then the computer won't pass POST. I get a "no signal" message on my monitor, and next time I boot the BIOS says it failed to boot last time and has reverted to previous settings.

I know this forum section is more about Linux compatibility and this has nothing to do with Ubuntu or Linux, but does anyone have any experience with XMP and know how I can get this working? I have no knowledge about overclocking anything, but was told when I bought the computer that I really should enable XMP.

Thanks,
Adam

---

### Post by ad_267 on 2009-11-17
Bump and here are my RAM settings before and after enabling XMP:
```
XMP Disabled:
System Memory Multiplier (SPD):  Auto
Frequency: 1333 1333
Performance Enhance: Turbo
DRAM timing selectable (SPD): Auto
Profile DDR Voltage: 1.5 V
Profile QPI Voltage: 1.1 V
x Channel Interleaving: 6 Auto
x Rank Interleaving: 4 Auto

XMP Enabled:
System Memory Multiplier (SPD):  Auto
Frequency: 1600 1600
Performance Enhance: Turbo
DRAM timing selectable (SPD): Auto
Profile DDR Voltage: 1.65 V
Profile QPI Voltage: 1.3 V
x Channel Interleaving: 6 Auto
x Rank Interleaving: 4 Auto

Channel A Timings:
          XMP Disabled    XMP Enabled
CAS Latency Time:    9              8
tRCD:                9              8
tRP:                 9              8
tRAS:               24             20

tRC:                33             36
tRRD:                4              5
tWTR:                5              6
tWR:                10             12
tWTP:               21             24
tWL:                 7              8
tRFC:               74             88
tRTP:                5              6
tFAW:               20             24
Command Rate (CMD):  1              1

B2B CAS Delay:       -              -
Round Trip Latency: 46              46

Channel B is the same but round trip latency is 48.

System Memory Multipler Options:
6.0, 8.0, 10.0
Performance Enhance Options:
Standard, Turbo, Extreme
```

---

