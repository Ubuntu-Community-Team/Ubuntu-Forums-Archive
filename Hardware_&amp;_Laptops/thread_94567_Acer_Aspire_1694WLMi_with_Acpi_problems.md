---
title: "Acer Aspire 1694WLMi with Acpi problems"
date: 2005-11-24
forum: Hardware &amp; Laptops
---

### Post by fogNL on 2005-11-24
I have an acer aspire 1694WLMi laptop with 1gig ddr2 ram.  I'm having some problems getting acpi support to work.  I followed directions in different posts as well as different websites, but can't seem to solve this problem.

I downloaded the DSDT file from acpi.sf.net, however, whenever i boot up, i get a kernel panic on a unknown block.  I'm not sure if i'm doing this right or not.

I have tried this with Breezy and Dapper, using stock ubuntu kernels (2.6.12) and custom built (2.6.14.2).  I download my DSDT.asl file and put it in /boot  then configure grub with "initrd  /DSDT.asl", however, it kernel panics and says something like unknown block (0,0).

Any ideas?

---

### Post by strandlooper on 2005-11-27
try this one

[https://wiki.ubuntu.com/ACPIBattery?highlight=%28acpi%29](https://wiki.ubuntu.com/ACPIBattery?highlight=%28acpi%29)

very straight forward howto

---

