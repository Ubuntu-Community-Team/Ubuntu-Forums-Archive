---
title: "Unbuffered DDR2 ECC in an older AMD 780G desktop 'board?"
date: 2015-10-13
forum: Hardware
---

### Post by bcschmerker on 2015-10-13
I am currently looking into the problem of proper memory support for LinUX 3.*n*, as I noticed the "non-ECC" warning during the boot process.  The Gigabyte® GA-MA78GM-S2HP in the Hot Rod gPC™ (running Ubuntu® 12.04.5-LTS with upgraded Kernel to 3.13 stable) has only non-ECC memory modules in the QVL, with 1 GiB per module the apparent sweet spot.  Advanced Micro Devices' Socket AM2/+ CPUs are rated to support both ECC and non-ECC memory, provided that it is unbuffered (Intel FCLGA 1150 MPU's are the same way for DDR3, with the Pentium G3200 and Core i3-4400/i5-4600/i7-4700 series requiring unbuffered RAM and the Xeon E3-1000v3 series buffered/registered RAM).

Anybody have experience running unbuffered ECC in a desktop 'board; and if so, what make and model, what performance limitations, &c.?

---

### Post by Yellow Pasque on 2015-10-13
If you're referring to the message below, it's a common informative message on AMD motherboards. It doesn't mean you need to buy/use different RAM.
```
[   13.809666] EDAC amd64: DRAM ECC disabled.
[   13.809673] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
                Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
```

---

