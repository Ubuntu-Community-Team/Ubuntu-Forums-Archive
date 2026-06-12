---
title: "Asus eeepc 1101ha ram problem"
date: 2009-10-24
forum: Hardware
---

### Post by gnutheory on 2009-10-24
Hello,
I upgraded my 1gb ram to a S&#305;ngle slot 2gb SO-DIMM.However,I couldn't define the ram.Despite of the fact that bios recognized 2 gb Free's showing me that I have got 982068
What is your suggestion about this problem.I'd searched from google and I found this :
[http://www.ultramobilegeek.com/2007/11/howto-recompiling-eee-kernel-to-enable.html](http://www.ultramobilegeek.com/2007/11/howto-recompiling-eee-kernel-to-enable.html)
Is there an another sollution apart from recompiling the kernel.
I already updated my bios to the newest version and I'm using ubuntu 9.10 with all updates
Thanks for your advice and sorry for my poor English I'm in Prerparatory School
Edit:
I'm using asus eeepc 1101ha

---

### Post by powertower on 2009-10-24
What results do you get from:

sudo lshw -C memory

---

### Post by gnutheory on 2009-10-24
It gives;
 *-firmware              
       description: BIOS
       vendor: American Megatrends Inc.
       physical id: 0
       version: 0317 (09/24/2009)
       size: 64KiB
       capacity: 960KiB
       capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
  *-cache:0
       description: L1 cache
       physical id: 5
       slot: L1-Cache
       size: 24KiB
       capacity: 24KiB
       capabilities: internal write-back data
  *-cache:1
       description: L2 cache
       physical id: 6
       slot: L2-Cache
       size: 512KiB
       capacity: 512KiB
       capabilities: internal write-back unified
  *-memory
       description: System Memory
       physical id: d
       slot: System board or motherboard
       size: 2GiB
       capacity: 2GiB
     *-bank
          description: SODIMM DDR2 Synchronous
          product: ModulePartNumber00
          vendor: Manufacturer00
          physical id: 0
          serial: SerNum00
          slot: DIMM0
          size: 2GiB
          width: 64 bits
mustafa@mustafa-laptop:~$ 
So is there a hope?

---

