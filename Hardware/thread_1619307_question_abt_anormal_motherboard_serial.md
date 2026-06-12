---
title: "question abt anormal motherboard serial"
date: 2010-11-11
forum: Hardware
---

### Post by Elie-M on 2010-11-11
I wanted to know the serial number of my motherboard. my result was:

Motherboard serial: Base Board Serial Number


this is of course anormall....

so I logged on my ubuntu and did: sudo lshw and I got this:
[I]
description: Notebook
    product: Satellite A305
    vendor: TOSHIBA
    version: PSAG8U-03L01E
    serial: X8631002Q
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=normal chassis=notebook uuid=43D2ADA0-9FF4-11DD-A70E-001E33754FDB
  *-core
       description: Motherboard
       product: Base Board Product Name
       vendor: Intel Corp.
       physical id: 0
       version: Base Board Version
       serial: Base Board Serial Number
       slot: Base Board Chassis Location[/I]


so I wanted to make sure: is "serial: Base Board Serial Number" = "serial: X8631002Q"?? and what's the hell with that *"serial: Base Board Serial Number?" *why doesn't it just display the serial directly?

---

