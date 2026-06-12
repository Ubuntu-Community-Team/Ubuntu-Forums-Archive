---
title: "Z590 Aorus Elite by Gigabyte"
date: 2021-03-25
forum: Hardware
---

### Post by quickvictor on 2021-03-25
Z590 Aorus Elite by Gigabyte are new motherboards. It has AIM Bios that doesn't recognize single partition and consequently if you use two drives, one for system and another for data - it doesn't work. 
I used Gigabyte for past 10 years with no problems and all of suddenly the expensive expenditure. In this case I use new Intel i9 and Ubuntu 18.04, 
Hope there are some fixes.

---

### Post by CelticWarrior on 2021-03-25
Welcome.

Maybe you need to read this [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) ?
I think your latest Gigabyte was BIOS, everything now is UEFI.

PS - Newer hardware, newer software. If there isn't any special reason to use 18.04 then don't. Use 20.04 instead.

---

### Post by oldfred on 2021-03-25
while we normally suggest LTS versions like 20.04, your hardware is so new, you may need newest revision like 20.10 or even the yet to be released 21.04. Then you have the newest kernel, drivers & support software for new systems. 

When I built my new system in early 2016, I had to install 16.04 from its daily release. Since a pre-release version gets so many updates and some update may temporarily break something, I did a full re-install once released.

---

### Post by laluz2 on 2021-09-18
Any update on the  Z590 Aorus from the owners? I'm on the market for the mobo supporting i7 11700 1200 and this is one of those chipsets. Somehow it is hard to find hardware recommendations for a Ubuntu/Linux system.

---

### Post by linuux on 2021-09-19
> **laluz2 said:**
> Any update on the  Z590 Aorus from the owners? I'm on the market for the mobo supporting i7 11700 1200 and this is one of those chipsets. Somehow it is hard to find hardware recommendations for a Ubuntu/Linux system.It works.   You picked a good combo if going with Intel.

[https://linux-hardware.org/?probe=48d1110975](https://linux-hardware.org/?probe=48d1110975)

I would look at the BIOS settings for the storage devices.   There's also stuff like Secure Boot but I am not too familiar because my computer is much older.

Also, is this a dual boot system or just Linux?   Make sure that it's not in legacy mode but AHCI or whatever it's called.  

If you have an NVME device, there might be some configuration needed in the bios for that, too, not sure.   I found an article for Crucial nvme disks which you might find useful and apply that generally to any nvme disk.  

[https://www.crucial.com/support/articles-faq-ssd/bios-uefi-configuration-optimizing-m2](https://www.crucial.com/support/articles-faq-ssd/bios-uefi-configuration-optimizing-m2)

My wild guess is it's an uefi/bios issue.....don't quote me on it, though.   I think Z590/Rocket lake processors will work fine in Linux (including Ubuntu - I would use, at least, 20.04 or even 21.04.  That linux hardware website listed a number of Z590 motherboards with various processors, working.

---

