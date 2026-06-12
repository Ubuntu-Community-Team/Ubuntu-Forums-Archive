---
title: "32- or 64-bits?"
date: 2009-02-06
forum: Hardware
---

### Post by dox_drum on 2009-02-06
Hi everybody,

I was just playing arround with the Konsole and run the following command line

```
oscar@dell-desktop:~$ sudo lshw -C memory
```

And here is the result
 
  ```
*-firmware              
       description: BIOS
       vendor: Dell Inc.
       physical id: 0
       version: A11 (06/19/2008)
       size: 64KiB
       capacity: 1984KiB
       capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
  *-cache:0
       description: L1 cache
       physical id: 700
       size: 32KiB
       capacity: 32KiB
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
       size: 2GiB
     *-bank:0
          description: DIMM DDR Synchronous 667 MHz (1.5 ns)
          product: M4 70T2864QZ3-CE6
          vendor: CE00000000000000
          physical id: 0
          serial: 824D0D8E
          slot: DIMM_A
          size: 1GiB
          [COLOR="Red"]width: 64 bits[/COLOR]
          clock: 667MHz (1.5ns)
     *-bank:1
          description: DIMM DDR Synchronous 667 MHz (1.5 ns)
          product: M4 70T2864QZ3-CE6
          vendor: CE00000000000000
          physical id: 1
          serial: 824D0D89
          slot: DIMM_B
          size: 1GiB
          [COLOR="Red"]width: 64 bits[/COLOR]
          clock: 667MHz (1.5ns)
```



I don't know much about this 64-bits structure, but as you can see the laptop has core 2 duo processor. Does the red marked line means that my computer has 64-bits structure? 

Thank you all in advance.

[CENTER]Enjoy![/CENTER]

---

### Post by markbuntu on 2009-02-06
Pretty much every machine made today has 64 bit architecture. It has been around now for 10 years or so. The big problem is that application developers are unwilling to commit resources to make 64 bit applications.

That said, there are many many applications for Linux/Ubuntu that are made to run on the 64 bit operating system. They are much faster than their 32 bit counterparts. A 64 bit OS can also access far more ram more quickly than 32 bit.

---

### Post by rsambuca on 2009-02-06
Yes, Intel Core 2 Duo chips are 64bit.

---

### Post by dox_drum on 2009-02-07
Thank you very much both of you!

But I got another question. Would I change the OS from 32- to 64-bits? or Are there another requirements on hardware for doing that?

Regards.

---

### Post by GammaRay256 on 2009-02-07
As far as I know, there wouldn't be any special hardware requirements above what you have.

I have a Core 2 Duo as well and tried 64-bit (I think it was Ubuntu 8.04).  I didn't notice any better speed.

The software compatibility issues are pretty minor... The biggest problem for me was the Flash plugin in Firefox, and that was before Flash 10 came out I think.  I assume the problem has been fixed since then.

32-bit applications will run in 64-bit, however, if no 64-bit version is available.  But unless you have 4gb or more RAM, I don't think there's too much of a reason to switch right now.

---

### Post by rsambuca on 2009-02-07
> **GammaRay256 said:**
> As far as I know, there wouldn't be any special hardware requirements above what you have.

I have a Core 2 Duo as well and tried 64-bit (I think it was Ubuntu 8.04).  I didn't notice any better speed.

The software compatibility issues are pretty minor... The biggest problem for me was the Flash plugin in Firefox, and that was before Flash 10 came out I think.  I assume the problem has been fixed since then.

32-bit applications will run in 64-bit, however, if no 64-bit version is available.  But unless you have 4gb or more RAM, I don't think there's too much of a reason to switch right now.
Not entirely true.  Depending on what applications you are using, there can be significant performance improvements to be had by moving to 64bit.  CPU intensive tasks such as video editing or 3D rendering can see upwards of 30% improvements.  If you are just using it for email, word-processing, web-browsing, etc, then no, you won't see any difference.

---

### Post by dox_drum on 2009-02-07
Thank you again.

I prefer not to try to change to 64-bits, 'cause I do not run heavy programs... and it is working perfectly.

Best wishes.

---

