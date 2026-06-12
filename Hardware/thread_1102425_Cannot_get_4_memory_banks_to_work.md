---
title: "Cannot get 4 memory banks to work"
date: 2009-03-21
forum: Hardware
---

### Post by dargaud on 2009-03-21
Hello all,
a bit offtopic, this is a pure hardware question (although Ubuntu runs on this system).

I have a problem with a Tomcat K8E S2865 motherboard. I can get it to work with 2x1Gb in slots 1 and 2, or in slots 3 and 4. But if I fill all 4 banks with 4x1Gb, I get long post beeps and the system refuses to boot.

I've tried with Corsair CM72SD1024-3200/S and CT2KIT12872Z40B. Both sets are DDR400 PC3200 ECC unbuff 128-bits 3,1T and the user's manual specifies ([ftp://ftp.tyan.com/manuals/m_s2865_110.pdf](ftp://ftp.tyan.com/manuals/m_s2865_110.pdf) page 28 ) that it should work as long as the mems are 128-bits. So what is wrong ?

```

# lshw
machine
    description: Desktop Computer
    width: 64 bits
    capabilities: smbios-2.3 dmi-2.3 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: NF-CK804
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (11/14/2006)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13
floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+
          slot: Socket 939
          size: 2200MHz
          capacity: 3GHz
          width: 64 bits
          clock: 201MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht s
yscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow rep_good nopl pni lahf_lm cmp_legacy cpufreq
        *-cache
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
     *-cache
          description: L1 cache
          physical id: 4
          slot: External Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back
     *-memory:0
         description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM [empty]
             physical id: 0
             slot: A0
             width: 64 bits
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: A1
             width: 64 bits
        *-bank:2
             description: DIMM
             physical id: 2
             slot: A2
             size: 1GiB
             width: 64 bits
        *-bank:3
             description: DIMM
             physical id: 3
             slot: A3
             size: 1GiB
             width: 64 bits
     *-memory:1 UNCLAIMED
          description: Memory controller
          product: CK804 Memory Controller
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:00.0
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0

```

Why does it say 64 bits for the memory width when the chips are 128 bits ?

Thanks...
-- 
Guillaume Dargaud
[http://www.gdargaud.net/](http://www.gdargaud.net/)

---

### Post by AgentZ86 on 2010-04-28
Reviving and old post -

This board from your .pdf that you posted says that the memory must be 128bits to use all 4 slots

I'm not sure but I don't think there is really any 128bit ddr's I think the fact that there is 2 x 64 bit with 2 memory controllers is what makes it 128bit but I could be wrong.

Anyhow, this board also requires NON-registered memory.

If it has a small chip in on the memory stick along with the 8 memory chips then it's probably registered memory and won't work with all 4 slots.

I'm having trouble confirming if these 2 chips you posted are non-registered or not.
But one thing I see is that they are 128x72 which I'm not sure if that would create a problem but crucial recommends for the memories for this board to be 128x64's

see the link here:
[http://www.crucial.com/store/listparts.aspx?model=S2865%20Tomcat%20K8E](http://www.crucial.com/store/listparts.aspx?model=S2865%20Tomcat%20K8E)

I sounds like the ones your posting are suppose to be non-registered, but looking at some images on google I see a small black chip on the CT2KIT12872Z40B, and no other confirmation on the other one, which sort of leads me to think it's registered memory which won't work, but I could be wrong, however I can't seem to confirm this subject.

Anyhow I don't know for sure, but thats what it sounds like.
And also all the chips must be the same from what I understand in the manual.

It does sound strange though.


I hope this helps.

---

### Post by dargaud on 2010-04-29
Fortunately, since 2006 when I orginally posted this, I got it to work. It's just difficult to remember how since a remote family member now uses that mobo. I think I used a different set of mems as those wouldn't work.

---

