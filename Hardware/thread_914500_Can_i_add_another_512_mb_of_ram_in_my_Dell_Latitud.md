---
title: "Can i add another 512 mb of ram in my Dell Latitude D800?"
date: 2008-09-08
forum: Hardware
---

### Post by tdawg on 2008-09-08
Can i add another 512 mb of ram? or do I need to take the existing 512 out and put in a 1 gig by itself? here is code from lshw -C memory

```
*-firmware              
       description: BIOS
       vendor: Dell Computer Corporation
       physical id: 0
       version: A10 (07/08/2004)
       size: 64KiB
       capacity: 448KiB
       capabilities: isa pci pcmcia pnp apm upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
  *-cache:0
       description: L1 cache
       physical id: 700
       size: 8KiB
       capacity: 8KiB
       capabilities: internal write-back data
  *-cache:1
       description: L2 cache
       physical id: 701
       size: 2MiB
       capacity: 2MiB
       clock: 66MHz (15.0ns)
       capabilities: pipeline-burst internal varies unified
  *-memory
       description: System Memory
       physical id: 1000
       slot: System board or motherboard
       size: 512MiB
       capacity: 1GiB
     *-bank:0
          description: DIMM DDR Synchronous 266 MHz (3.8 ns)
          physical id: 0
          slot: DIMM_A
          size: 256MiB
          width: 64 bits
          clock: 266MHz (3.8ns)
     *-bank:1
          description: DIMM DDR Synchronous 266 MHz (3.8 ns)
          physical id: 1
          slot: DIMM_B
          size: 256MiB
          width: 64 bits
          clock: 266MHz (3.8ns)

```

Thank you.

-tdawg:guitar:

---

### Post by tdawg on 2008-09-08
So if I'm reading it correctly, it says I have 2  256 Mb's in there now? If that is the case, can I add two 512s or should I get 1 gig?

---

### Post by Therion on 2008-09-08
> **tdawg said:**
> So if I'm reading it correctly, it says I have 2  256 Mb's in there now? If that is the case, can I add two 512s or should I get 1 gig?
It appears you have two DIMM slots.  Each slot currently has a 256MB module in it.  You can install up to 1GB of system RAM.  I would suggest using two 512MB modules in place of the two existing 256MB modules.

---

### Post by tdawg on 2008-09-08
And I just almost bought 2  1 gig sticks, thank you for the quick reply.
:guitar:

-tdawg:guitar:

---

### Post by Therion on 2008-09-08
In looking at some websites that show the specs for your Dell, it appears it WILL support 2GB.  The report above indicates one, but 2GB is pretty standard for notebooks these days.

---

