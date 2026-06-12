---
title: "How to get the original BIOS supplied DSDT?"
date: 2006-12-08
forum: Hardware &amp; Laptops
---

### Post by saurabhnanda on 2006-12-08
Hi,

I'm booting with the standard Edgy 2.6.17 kernel. The initrd which comes by default has a DSDT embedded in it. This DSDT does not work for my laptop. 

I want to get my hands on the BIOS supplied DSDT so that I can fix it. However, /proc/acpi/dsdt contains the DSDT in the initrd (I know cuz a long time back I had extracted the BIOS supplied DSDT and it was not the one I am getting now).

I don't have any other kernel with me right now. How can I either:

a) Stop the 2.6.17 kernel from loading the DSDT. (acpi=off doesn't help -- it switches of ACPI altogether!)

OR

b) Directly get the BIOS supplied DSDT even after the kernel has laoded its own copy.

Help will be appreciated.

Thanks,
Saurabh.

---

