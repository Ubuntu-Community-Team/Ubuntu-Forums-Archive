---
title: "AMD Athlon64 x2 dual cores"
date: 2005-08-17
forum: Hardware &amp; Laptops
---

### Post by shadeland on 2005-08-17
I recently built up a new system:

AMD Athlon64 x2 4200+ (dual 2.2 GHz cores)
[Gigabyte GA-K8N Ultra-9](http://www.newegg.com/Product/Product.asp?Item=N82E16813128283) 
2 GB dual-channel RAM
nVidia GeForce 6800GT (dual DVI out, PCI-Express)

Getting Ubuntu to see dual cores was a bit of a challenge.  Here's how I did it:

First, I had to go to F5 on my motherboard BIOS.  Pretty easy, took 5 minuts to flash.

Loading up Ubuntu 5.04 was easy.  Audo worked, and it picked up one of the network cards with the forcedeth nForce driver (dual Gigabit Ethernet, although they're two different chipsets).   

The only problem was that the installed smp kernel did not see two cores.  The dual core system should look like a regular dual-proc box.  I loaded up the 2.6.11-1-amd64-k8-smp kernel, but it panic'd upon boot.  

I downloaded a stock 2.6.12.5 kernel for kernel.org, complied, made an initial ramdisk, and the system booted fine.  Also, I see two cores.

To check, look in /proc/cpuinfo.  You should see two processor listings:

```

cat /proc/cpuinfo | grep processor
processor       : 0
processor       : 1
```

If you don't, you're using just one of the cores.

---

