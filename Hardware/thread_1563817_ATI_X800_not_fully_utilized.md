---
title: "ATI X800 not fully utilized"
date: 2010-08-29
forum: Hardware
---

### Post by jjjjeremy on 2010-08-29
I just pulled my old gaming PC out of the closet after years of neglect. Installing 10.04 went without a hitch, and everything is running fine, except for Hulu in full screen (and anything 3D)

When I put it full screen, the video gets slightly choppy, enough that I can't watch it, and have to use a window about 2/3 the size of the screen. When doing this, my system monitor says that the CPU is at or near 100%.

I find this to be really strange. I installed (or I though I did) the xorg radeon driver. If this is working, Hulu shouldn't be putting this kind of strain on my computer. When I used the computer for gaming in Windows (CS:S) I had no problem running around shooting people in 3D full screen. I would think that streaming video from Hulu at 480p would be a lot less demanding than an FPS at 1024p.

I feel like the video card isn't being used to its full potential, and I need someone to walk me through verifying that the proper drivers are properly installed, and how to install them if they aren't. 

Specs (for now, I'll finish the details when I get home, and post segments of lshw)

ATI Radeon X800 (not GT or anything like that)
AMD Athlon 64 3000+ (I think it's 1.8GHz, but might be 2.0)
2G RAM (I'll post the specs later)
500G WD Caviar (don't think that matters)
onboard sound
1680x1050 monitor

Thanks

PS, because I can find better CPUs on ebay for very little, would upgrading to a 2.2GHz make a significant difference?

---

### Post by Yellow Pasque on 2010-08-29
Full-screen Flash video (like Hulu) is really CPU-intensive, because Flash in Linux is unaccelerated by GPU and even more inefficient than its Windows counterpart. If you can download the video and play it in a video player, it will be much better.

As for 3D, ATI dropped support for this card in its proprietary driver a while ago, so that's as fast as its going to get, unless you try the newer open-source gallium3d-based driver: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by jjjjeremy on 2010-08-29
```
jeremy-desktop            
    description: Desktop Computer
    product: MS-7125
    vendor: MICRO-STAR INTERNATIONAL CO., LTD
    version: 1.0
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1
  *-core
       description: Motherboard
       product: MS-7125
       vendor: MICRO-STAR INTERNATIONAL CO., LTD
       physical id: 0
       version: 1.0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (06/23/2005)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 Processor 3000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: 15.15.0
          slot: Socket 939
          size: 1810MHz
          capacity: 3GHz
          width: 64 bits
          clock: 201MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm
        *-cache:0
             description: L1 cache
             physical id: b
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: d
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back
     *-cpu:1 DISABLED
          description: CPU
          vendor: Unknown
          physical id: 5
          bus info: cpu@1
          version: 15.15.0
          slot: Socket 939
          size: 1810MHz
          capacity: 3GHz
          clock: 201MHz
        *-cache:0
             description: L1 cache
             physical id: c
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: e
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back
     *-memory:0
          description: System Memory
          physical id: 1e
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: DIMM
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 512MiB
             width: 64 bits
        *-bank:2
             description: DIMM
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             size: 512MiB
             width: 64 bits
        *-bank:3
             description: DIMM
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
             size: 512MiB
             width: 64 bits


        *-display:0
             description: VGA compatible controller
             product: R430 [Radeon X800 (PCIE)]
             vendor: ATI Technologies Inc
             physical id: 0
             bus info: pci@0000:05:00.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list rom
             configuration: driver=radeon latency=0
             resources: irq:28 memory:d0000000-dfffffff(prefetchable) memory:fe2f0000-fe2fffff ioport:9e00(size=256) memory:fe200000-fe21ffff(prefetchable)


        *-display:1 UNCLAIMED
             description: Display controller
             product: R430 [Radeon X800] (PCIE) (Secondary)
             vendor: ATI Technologies Inc
             physical id: 0.1
             bus info: pci@0000:05:00.1
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress cap_list
             configuration: latency=0
             resources: memory:fe2e0000-fe2effff
```


Sorry about the previous dump of text. I was in a hurry, and just wanted to post the output of lshw to confirm my hardware specs. Forgot to put the code tags!

---

### Post by Yellow Pasque on 2010-08-29
^Is there a point to that? (and use code tags next time, PLEASE)

---

