---
title: "Problem after updating BIOS"
date: 2008-01-15
forum: Hardware &amp; Laptops
---

### Post by gaelfx on 2008-01-15
I  am dual-booting Windows XP and Ubuntu 7.10, and I recently upgraded the BIOS from Windows. Windows continues to load just fine, but I can no longer boot Ubuntu properly. Grub gets through just fine, but at some point during the Ubuntu boot, it hangs. This point is not consistent, it seems to change every time I try to start up, but it seems to happen most often right before the Login screen comes, and also very early in the boot process. I tried booting in recovery mode, but to no avail. My system is a Compaq Presario V3000(3169AU). The BIOS is from Phoenix technologies. Can anyone tell me anything about this problem? Sorry if this is the wrong section to post in.

---

### Post by Yellow Pasque on 2008-01-15
Do you have release notes of what the BIOS update changed or "fixed"? That might give you a clue. Also, do you have any settings in your BIOS related to ACPI? Try booting with the noacpi and nolapic options.

---

### Post by gaelfx on 2008-01-15
haha, well, I provided the model number in hopes the specs would be unnecessary, but here goes:

AMD64 Turion 2.1Ghz (iirc)(but I am running the 32-bit verison of Ubuntu)
512MB RAM
NVidia GeForce Go! 6100 (or something like that, point is it's NVidia and the drivers for it are not available on their website)
80Gb HDD
Conexant Audio

Can't remember the rest offhand, but as I said the BIOS is from Phoenix Technologies and the previous version was F.13, current version is F.39

Does this help or do I need to dig further and tell you more?

---

### Post by gaelfx on 2008-01-17
Yeah, I guess the only solution would be to revert at this point, I can't really think of any way that I, with my limited technical knowledge, can full describe the problem to a degree that it will become solveable. Next question is how do I do that? :P Well, it's not that I wanted someone else to look up my system specs, I just figured since it's a motherboard thing, the model would be enough for someone out there to realize which piece is having the problem. Forgive my laziness.

---

