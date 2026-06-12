---
title: "NVIDIA Driver Problem - BIG problem might effect everyone Vid card fan"
date: 2005-06-26
forum: Hardware &amp; Laptops
---

### Post by ubuntufans on 2005-06-26
I bought parts to built 3 system for my new home.
All of them have nvidia cards (6600GT, 6800GT, and 6600 Non-gt, non ultra)

Motherboard are MSI Neo4 Platinum and Abit AN8 (2 piece on abit)

i built them and install ubuntu, video card fans are running on all 3 system, i installed nvidia drive and then rebooted first computer startup into GDM, while Nvidia logo appear the Vid card fan STOPPED :(

I figured it could be bad card, now 2nd system installed nvidia driver (using APt_GET) it happend too, fan stopped when i got into nvidia logo and never come back on.

3rd system, the same thing happend, so i edit /etc/X11/xorg.coinf and put back nv instead of nvidia, video card fan starts working again.

Now, this is all new hardware, and all 3 of them happend the same way it does to each other, anyone having this problem before? open your case and see if your PCI-Express card does this to you.

My old system with 5200FX (AGP) doesnt have this problem.

Anyone can help me? 

Thank You

UPDATE : i tried using 7664 i downloaded from nvidia site, same problem :(

---

### Post by feld on 2005-06-26
uhm i believe thats the way nvidia drivers work for the 6xxx series. they run much cooler than the 5xxx series so they dont need the fan on until you're gaming


-Feld

---

### Post by ubuntufans on 2005-06-26
hmm it could be true, but the heatsink gets reallyyy hot, i'm a bit worry about it :(

---

### Post by ubuntufans on 2005-06-26
anyone have solution?

Thanks

---

