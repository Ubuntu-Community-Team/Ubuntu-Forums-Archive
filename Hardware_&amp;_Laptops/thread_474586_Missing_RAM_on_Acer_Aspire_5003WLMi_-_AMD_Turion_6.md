---
title: "Missing RAM on Acer Aspire 5003WLMi - AMD Turion 64bits"
date: 2007-06-15
forum: Hardware &amp; Laptops
---

### Post by crixtiano on 2007-06-15
Hi,

I have a notebook Acer Aspire 5003WLMi:

I appear to be missing quite a bit of RAM on an x86_64 system. 

I have 512MB installed, with 32MB reserved to video memory, so, I would to have 480MB (because 512-32=480), but 'free' only shows 403MB:

> 
[FONT="Courier New"]
$ free -m
             total       used       free     shared    buffers     cached
Mem:           403        396          7          0          7        125
-/+ buffers/cache:        263        140
Swap:         1090         35       1055
[/FONT]


Consulting dmesg, I could observe Linux is reserving 64MB RAM to "Aperture from AGP".

The part of dmesg that concerns the "Aperture from AGP" is shown below: 

> 
[FONT="Courier New"][   12.286932] Checking aperture...
[   12.286936] CPU 0: aperture @ e0000000 size 32 MB
[   12.286937] Aperture too small (32 MB)
[   12.286942] AGP bridge at 00:00:00
[   12.286947] Aperture from AGP @ e0000000 size 32 MB (APSIZE f38)
[   12.286949] Aperture too small (32 MB)
[   12.286951] Your BIOS doesn't leave a aperture memory hole
[   12.286953] Please enable the IOMMU option in the BIOS setup
[   12.286955] This costs you 64 MB of RAM
[   12.365394] Mapping aperture over 65536 KB of RAM @ 4000000
[   12.372868] Memory: 405760k/490432k available (2217k kernel code, 84284k reserved, 1162k data, 304k init)
[/FONT]

Consulting the BIOS of my notebook, I couldn't find IOMMU option. I can only choice to video memory only 32 and 64MB (off course, I choice for 32MB).

so, I have some questions:

1) Anyone know what's up here? 
2) What is "Aperture from AGP"? 
3) Is this normal for an x86_64 system? 
4) What do I have to do to linux reserve less than 64MB to "Aperture"?

Thank you.

Cristiano

---

