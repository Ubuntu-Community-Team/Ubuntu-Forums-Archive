---
title: "upgrading ram on hp omnibook xe3"
date: 2009-04-23
forum: Hardware
---

### Post by lunaz on 2009-04-23
i'm wanting ot max out the ram on the server. crucial says that i can only go up to 512mb but lshw shows otherwise:

[http://crucial.com/store/listparts.aspx?model=Omnibook%20XE3%20Series%20(133MHz](http://crucial.com/store/listparts.aspx?model=Omnibook%20XE3%20Series%20(133MHz))

```

luna@teh-serverer:/var/log$ sudo lshw -C memory
  *-firmware
       description: BIOS
       vendor: Phoenix Technologies LTD
       physical id: 0
       version: GF.M1.09 (05/10/2002)
       size: 107KiB
       capacity: 448KiB
       capabilities: pci pcmcia pnp apm upgrade shadowing cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery
  *-cache:0
       description: L1 cache
       physical id: 8
       slot: L1 Cache
       size: 32KiB
       capacity: 32KiB
       capabilities: asynchronous internal write-back
  *-cache:1
       description: L2 cache
       physical id: 9
       slot: L2 Cache
       size: 256KiB
       capacity: 512KiB
       capabilities: burst external write-back
  *-memory
       description: System Memory
       physical id: 1b
       slot: System board or motherboard
       size: 256MiB
       capacity: 1GiB
     *-bank:0
          description: SODIMM SDRAM Synchronous
          physical id: 0
          slot: DIMM0
          size: 128MiB
          width: 32 bits
     *-bank:1
          description: SODIMM SDRAM Synchronous
          physical id: 1
          slot: DIMM1
          size: 128MiB
          width: 32 bits

```
halp? :)

---

### Post by HankB on 2009-04-24
Why not download the manual from HP and see what it says? Or perhaps HP sells accessories and upgrades and might list available RAM.

-hank

---

