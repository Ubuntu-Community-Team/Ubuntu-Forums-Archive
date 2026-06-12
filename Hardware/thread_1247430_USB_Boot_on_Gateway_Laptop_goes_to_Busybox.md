---
title: "USB Boot on Gateway Laptop goes to Busybox"
date: 2009-08-22
forum: Hardware
---

### Post by pcawdron on 2009-08-22
I have a very nice LT3106 Gateway laptop

[http://au.gateway.com/products/product.html?prod=LT3106a](http://au.gateway.com/products/product.html?prod=LT3106a)

And would like to run Ubuntu on it in stead of Vista Home. I'm running Ubuntu on another laptop so downloaded the latest ubuntu-9.04-desktop-i386 ISO and used **USB Start Up Disk Creator** change the boot sequence on the laptop and got to the first screen in Ubuntu.

If I click on the try-without-installing option, the laptop boots into busybox with the following error messages... 

> 0.752002 MP-BIOS bu:8254 timer not connected to IO-APIC
3.604011 ata1: softreset failed (device not read)
modprobe: FATAL: Could not load /lib/modules/2.6.28-11-generic/modules.dep: No such file or directory
6.316776 powernow-k8: BIOS error no PSB or ACPI _PSS objects 
Loading, please wait...

BusyBox v1.10.2

Can anyone decipher this and provide some direction? Is it worth trying wubu?

Thanks,
Peter

---

