---
title: "Need help upgrading processor"
date: 2009-02-19
forum: Hardware
---

### Post by chez17 on 2009-02-19
I am looking to install Ubuntu Studio on an old box I have. I need to upgrade the processor and I am trying to get information on my motherboard. Here is the result of lshw:

```

    description: Desktop Computer
    product: EN995AA-AB1 v1311kr
    vendor: HP Pavilion 061
    version: 0301211RE101GYPSU00
    serial: CNN5480HF7 KO540
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=desktop uuid=CCD715B6-765B-DA11-9EB7-10D7AF8BFE3B
  *-core
       description: Motherboard
       product: Gypsum
       vendor: MSI
       physical id: 0
       version: 3.11
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 3.11 (10/27/2005)
          size: 64KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.06GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          slot: CPU 1
          size: 3059MHz
          capacity: 3059MHz
          width: 64 bits
          clock: 532MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc up pni monitor ds_cpl tm2 cid cx16 xtpr

```

I can't find anything about this motherboard, how can I tell if it can handle a dual core processor? Any help is much appreciated.

---

### Post by NexusZA on 2009-02-20
Did you try googling for "HP Pavilion 061 specifications". I did just that and got loads of hits on specifications on that computer such as:

[http://minpaso.goga.co.jp/pc.php?id=902](http://minpaso.goga.co.jp/pc.php?id=902)

That should give you information on the motherboard model which you can then use to google for the motherboard itself and so get specifications on that.

---

### Post by jespdj on 2009-02-20
What's the exact name of the model of the computer? Is it "Pavilion 061" or something else? The "061" in the name is kind of strange for the HP Pavilion range of computers.

Go to [HP Support](http://www.hp.com/#Support) and search for the exact model name, and you'll most likely find manuals and other technical information which might include information about what processors the motherboard supports.

Older Pentium 4 motherboards usually do not support Core 2 Duo processors; despite the fact that the socket is the same (Intel socket 775), Core 2 Duo processors require different power circuitry, and older motherboards might not have that. You might be able to put a dual-core Pentium D processor on it.

---

### Post by Squid Spectre on 2009-02-20
I don't know that you can/want to upgrade that. P4s usually used the 478 model socket on motherboards, which means you probably have something that either is a 478 socket or something thats backwards compatible with one. Without being certain you can only really assume the former.With that in mind the only way to really upgrade with a guarantee that it will is to go above 3.0 ghz on a P4 chip and unfortunately no such CPU core exists. P4 cut out at about 3.0 Ghz. 

I would really try to figure out what kind of socket you do have on your motherboard before you invest, and as far as I know there is now way to get that from the terminal.

Edit: I could be wrong on the socket number.

---

### Post by stchman on 2009-02-20
I think a 3.0GHz P4 will be plenty fast for Studio.

---

### Post by youph on 2009-02-20
> **stchman said:**
> I think a 3.0GHz P4 will be plenty fast for Studio.

I agree, for sound/music work maybe, but not for video.

IMHO, if you need a CPU upgrade go with a new platform. You could get a pentium D used probably for pennies on the dollar on ebay but honestly if you need more horsepower get a phenom II 2.8 for $190, a cheap AM2+ mobo (say $70) and some (still pretty cheap) DDR2 memory ($40 for 4 gigs last I checked) and for $300 you have a quad core monster ready to rip through whatever you can throw at it. Core 2 Duos are also fine processors if you needed faster single thread performance you could grab a 3ghz wolfdale core2 for like $165, but your p4 @ 3.06ghz is gonna be right on the heels of a similarly clocked core2 in single threaded performance. Or even better an amd windsor athlon @ 3ghz with 2x1MB l2 for $90, plus the AM2 motherboards for this chip are dirt cheap.

So, my suggestion depends on what your workload is. If your apps scale well to 4+ threads, I'd go for the phenom II; its the best value for a quad core at the present time IMHO. If you are limited more by single threaded performance, the fastest core2 duo or athlon x2 you can afford is the way to go (if you're open to overclocking, the core2 duos are infamous for hitting 4ghz easily with proper air cooling.) But then again, your p4 3.06ghz is very respectable in most image/video/sound single thread workloads, so if you are limited to single threaded apps, don't expect that much of an increase in performance unless you overclock. The fastest core2 tops out @ 3.33ghz and amd's athlon @ 3.2. Clock for clock the core2 will beat the p4, but we're only talking humble improvements like 1-25% as well as the addition of more l2 cache.

CPU shopping is fun, enjoy!

---

### Post by chez17 on 2009-02-24
After some more research and the helpful people here it seems that my processor is fast enough for what I want to do. My next question is how do I determine if the mother board will support more ram? I was thinking of getting this:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16820231098](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231098)

however in the product page someone warns:

"Before buying this RAM, make sure your mobo supports RAM voltages of 1.9. Memory voltage must be set to 1.9 to run dual channel mode."

Here is the result of lshw:

```

*-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 512MB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 512MB
             width: 64 bits
        *-bank:1
             description: DIMM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1

```

It seems it won't work on my motherboard because of SDRAM is different than DDR2(I think). My next question is how do I determine the right ram to buy? Newegg has different types of SDRAM with different number of pins, how do I figure that out?

---

