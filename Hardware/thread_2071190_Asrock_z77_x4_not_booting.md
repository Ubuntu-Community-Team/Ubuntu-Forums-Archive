---
title: "Asrock z77 x4 not booting"
date: 2012-10-14
forum: Hardware
---

### Post by benj23673 on 2012-10-14
I tried to install a Nvida Geforce gt on my asrock extreme 4  z77 mobo and now it wont read my hard drive. I inserted a live ubuntu disk and  it said I had a 2tb hard drive I am using a 2tb green seagate. I don't  know what to do. The computer was working before all this happened,  where should I go from here?
I think it is because the hard disk takes 10 seconds to boot since it is green? I am currently downloading 12.04 64bit in case I have to do a fresh install but I would at least like some of my files back from there.

---

### Post by oldfred on 2012-10-15
LIveCD or USB should boot and show files on hard drive. If you have a new x77 board it is UEFI but you may be booting in either UEFI or BIOS mode.

When booting from liveCD or USB you need to boot in same mode as current install if reinstalling. Otherwise I think you can boot in either mode. You have to use UEFI and choose. Ubuntu liveCD should show two choices - efi or AHCI/BIOS/legacy or whatevey Asrock uses.

---

