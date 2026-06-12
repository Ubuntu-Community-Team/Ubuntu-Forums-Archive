---
title: "Feisty only recognizes half of 512MB memory card"
date: 2007-08-30
forum: Hardware &amp; Laptops
---

### Post by nsbrown on 2007-08-30
I have an Emachine M2350 with Feisty installed.  It originally had 256MB non-removable memory and 256MB removable memory.  I replaced the 256MB with a 512 MB card.

After booting up the Bios shows 458 MB and lshw -class memory gives the following:
  *-firmware              
       description: BIOS
       vendor: Phoenix
       physical id: 0
       version: 0008 (03/10/2004)
       size: 104KB
       capacity: 448KB
       capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot bootselect socketedrom acpi usb agp smartbattery biosbootspecification netboot
  *-cache:0
       description: L1 cache
       physical id: 5
       slot: L1 Cache
       size: 128KB
       capacity: 128KB
       capabilities: synchronous internal write-back
  *-cache:1
       description: L2 cache
       physical id: 6
       slot: L2 Cache
       size: 512KB
       capacity: 512KB
       capabilities: synchronous internal write-back
  *-memory:0 UNCLAIMED
       description: Flash Memory
       physical id: 7
       slot: System board or motherboard
       capacity: 512KB
     *-bank UNCLAIMED
          description: Chip FLASH Non-volatile 8 MHz (125.0 ns)
          physical id: 0
          slot: System Board
          size: 512KB
          width: 16 bits
          clock: 8MHz (125.0ns)
  *-memory:1
       description: System Memory
       physical id: 8
       slot: System board or motherboard
       capacity: 1GB
     *-bank:0
          description: DIMM DRAM Synchronous 266 MHz (3.8 ns)
          physical id: 0
          slot: U5
          size: 256MB
          width: 64 bits
          clock: 266MHz (3.8ns)
     *-bank:1
          description: DIMM DRAM Synchronous 266 MHz (3.8 ns)
          physical id: 1
          slot: U6
          size: 256MB
          width: 64 bits
          clock: 266MHz (3.8ns)
  *-memory:2 UNCLAIMED
       physical id: 1
  *-memory:3 UNCLAIMED
       physical id: 2

I'm perplexed.  Shouldn't the card work or not work.  Why would it only be showing half of its memory?

---

