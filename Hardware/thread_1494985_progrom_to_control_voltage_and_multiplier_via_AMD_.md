---
title: "progrom to control voltage and multiplier via AMD CnQ like crystal CPUID does"
date: 2010-05-27
forum: Hardware
---

### Post by taltamir on 2010-05-27
I have an older laptop (HP Pavilion ZV6000) I want to put Ubuntu on, it has a full sized desktop socket 939 AMD athlon64 CPU in it. It was amongst the very first 64bit laptops on the market. It is also very loud and hot, and it got worse over the years.
To control the noise I am using [http://crystalmark.info/software/CrystalCPUID/index-e.html](http://crystalmark.info/software/CrystalCPUID/index-e.html) which allows me to set the voltage and multiplier (the BIOS does not allow me to change those directly, it is stripped down).
This has allowed me to underclock and undervolt it, resulting in much quieter operation (and longer battery too).

Actually, crystal let me set several presets with the ability to dynamically switch between them based on the current % usage reported by windows... its all very nice and advanced. Although this feature I can live without.

Is there a similar program for ubuntu that will let me likewise use AMD CnQ to undervolt and underclock a CPU that from within the OS in a mobo whose bios does not normally allow such operations? I Would love to use ubuntu on this laptop but I cannot bear the noise.

I have done what I can hardware wise. I actually replaced the CPU with one I got off of ebay... it is limited on what it could take but it could still take an upgrade and is less power hungry now; also cleaned out the fans and applied newer and better thermal paste after removing the old one with arctic cleaner. Replacing the entire thermal array would be 60$ and I don't think it would help much anyways... the undervolting & underclocking solution works wonders anyways and I would like to keep it.

---

### Post by taltamir on 2010-05-28
nobody knows?

---

### Post by taltamir on 2010-06-04
pardon my bump

---

### Post by taltamir on 2010-06-08
another week another bump

---

### Post by oOarthurOo on 2010-06-18
For undervolting you want to look for phc-linux. I am unaware of how well it works with your cpu, or even if it is supported. It tends to only support the newer processors.

---

