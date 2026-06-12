---
title: "Ram?"
date: 2008-02-13
forum: Hardware &amp; Laptops
---

### Post by joshdudeha on 2008-02-13
I'm thinking of upgrading my RAM from 512mb to 1-2GB ram.
But, I can't remember my ram interface.
How do I found out without opening the box up.
Because i dont really wanna open it at the moment.
thanksx

---

### Post by hyperair on 2008-02-13
System->Administration->System Monitor. The 'System' tab and the 'Resources' tab should show you your RAM size. You could also go hunt down your RAM in System->Preferences->Hardware Information, but that's harder and more complex.

---

### Post by joshdudeha on 2008-02-13
I know how much ram i have
just dont know what interface it is.
I.e. DDR or w/e
Can someone tell me if it is possible to find this out?

---

### Post by Fechter on 2008-02-13
Sysinfo?

---

### Post by oldsoundguy on 2008-02-13
alternate route .. plug the FCC number into the FCC search site and get the PDA of the MANUAL. That should tell all!

---

### Post by Yellow Pasque on 2008-02-13
THis might give you enough of a clue:
```
sudo lshw -C memory
```
Here's mine. As you can see, it's using a 333 MHz clock (666Mhz double data rate), so I can identify it as DDR2-667
```
dan@harvest:/etc/modprobe.d$ sudo lshw -C memory
  *-firmware              
       description: BIOS
       vendor: American Megatrends Inc.
       physical id: 0
       version: V1.5 (10/15/2007)
       size: 64KB
       capacity: 960KB
       capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
   *-memory
       description: System Memory
       physical id: 29
       slot: System board or motherboard
       size: 2GB
     *-bank:0
          description: DIMM Synchronous 333 MHz (3.0 ns)
          product: PartNum0
          vendor: Manufacturer0
          physical id: 0
          serial: SerNum0
          slot: DIMM0
          size: 1GB
          width: 64 bits
          clock: 333MHz (3.0ns)
     *-bank:1
          description: DIMM Synchronous 333 MHz (3.0 ns)
          product: PartNum1
          vendor: Manufacturer1
          physical id: 1
          serial: SerNum1
          slot: DIMM1
          size: 1GB
          width: 64 bits
          clock: 333MHz (3.0ns)

```

---

### Post by joshdudeha on 2008-02-14
Heres my out put:
  ```
  *-firmware              
       description: BIOS
       vendor: IBM
       physical id: 0
       version: 24KT25AUS (08/08/2002)
       size: 111KB
       capacity: 448KB
       capabilities: pci pnp apm upgrade shadowing escd cdboot edd acpi usb agp ls120boot zipboot smartbattery biosbootspecification
  *-cache:0
       description: L1 cache
       physical id: 5
       slot: L1 Cache
       size: 8KB
       capacity: 16KB
       capabilities: asynchronous internal write-back
  *-cache:1
       description: L2 cache
       physical id: 6
       slot: L2 Cache
       size: 512KB
       capacity: 512KB
       capabilities: burst internal write-back
  *-memory
       description: System Memory
       physical id: 1f
       slot: System board or motherboard
       size: 512MB
       capacity: 2GB
     *-bank:0
          description: DIMM DDR Synchronous
          physical id: 0
          slot: J6J1
          size: 256MB
          width: 64 bits
     *-bank:1
          description: DIMM DDR Synchronous
          physical id: 1
          slot: J6J2
          size: 256MB
          width: 64 bits

```
Guess that means i have DDR memory (:
Thanks for helping

---

