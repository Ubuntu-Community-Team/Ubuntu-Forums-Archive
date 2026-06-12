---
title: "Can not read my Memory"
date: 2011-01-14
forum: Hardware
---

### Post by Pollyanna1 on 2011-01-14
I have 2 slots for the memory on the motherboard, each one has 1GB installed. When I checked the hardware specification it showed me only 1GB and half... But where is the other half or is that normal??? Here is the result of lshw for the memory

```
  *-memory
          description: System Memory
          physical id: 1c
          slot: System board or motherboard
          size: 1GiB
          capacity: 1536MiB
        *-bank:0
             description: DIMM
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 512MiB
        *-bank:1
             description: DIMM
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 512MiB
        *-bank:2
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2

```

Also, When I checked the System Monitor I see that only 1001.3 MB for the Memory.
BTW I swap the memory between the slots and I got the same result.

---

### Post by IcarusR on 2011-01-14
According to lshw you have three memory slots, two of them have 512Mb in & third is empty. Maximum memory is 1536Mb = 3 x 512Mb.

It would seem that it does not support 2Gb of memory so it sees the maximum of 512Mb in each slot.
Check your manual.

What make & model is the machine & / or motherboard ?

---

### Post by Pollyanna1 on 2011-01-14
Well, I do not have three spots on my machine for the RAM!!!! Unless it is hidden some where else???

here is the other specification for the machine 

```
 description: Desktop Computer
    product: DA192A-ABA 734n
    vendor: HP Pavilion 06
    version: 05/1211RE101SALSA
    serial: MX307A1131 NA920
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=A0E0A710-8C3E-D711-8E28-ED1367DDBD55
  *-core
       description: Motherboard
       product: KM266-8235
       physical id: 0
       serial: 132858-30514542
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: AM37308 (12/16/2002)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 2400+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.8.1
          slot: Socket A
          size: 2GHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up

```

---

### Post by Pollyanna1 on 2011-01-14
Yes, I think each slot can read 512MB maximum. Because I tried 512MB and 1GB and it reads 512MB for each one. But what about the third slot..!!!

---

### Post by IcarusR on 2011-01-14
> But what about the third slot..!!! 

No ideas really.

Might be able to flash bios with a later version that may support more ram.

---

### Post by cascade9 on 2011-01-15
@ IcarusR- good point. I dont know if it wiould work, and gettign the BIOS update could be hellish, but you never know... 

@ Pollyanna1- that chipset should use 1GB sticks. I tried going to the manufacturers site to see if I coudl see anythign about single sided/double sided RAM (normally more of an issue with SDRAM systems, but I've heard of problems with double sided DDR sticks on some boards). But, suprise suprise, MSI (microstar international) dont have anythign about that in the spec page- 

[http://www.msi.com/product/mb/MS-6390.html#/?div=Detail](http://www.msi.com/product/mb/MS-6390.html#/?div=Detail)

From the memory module support it seems they only test 512MB stcks as well. 

Its possible that given the 'right' memory module, you could get 1GB sticks working, but finding that memory could be a real PITA. Or MSI might have put in some artifical BIOS limit of 512MB sticks......

---

### Post by IcarusR on 2011-01-15
cascade9

> Its possible that given the 'right' memory module, you could get 1GB sticks working

Yes the mobo might not 'like' that make of ram. I would suggest trying, buying or borrowing a good brand of ram such as kingston.

---

