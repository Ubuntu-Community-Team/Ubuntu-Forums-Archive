---
title: "Asus Mobo Install Error"
date: 2008-01-11
forum: Hardware &amp; Laptops
---

### Post by glubrani on 2008-01-11
Asus M2N-MX
Athlon64 X 2 4400+
2GB G.Skill 6400 DDR2 running in Dual Mode
WD HHD 80GB SATA
Samsung SATA DVD Burner
Windows XP Pro
Cooler Master 550W PSU


getting the following error messages(s) when booting from an Ubuntu 7.04 CD

[22.018009] .. MP-BIOS Bug: Timer Not Connected To IO-APIC
[22.197029] Kernal Panic - Not Syncing: IO-APIC + timer doesn't work
Boot with APIC = DEBUG and send report. then try booting with the
"NOAPIC" option [22.197068]

I couldn't find the "NOAPIC" option when I am booting fro the CD. What's going on here?

Thanks

Tomana

---

### Post by logos34 on 2008-01-11
> **glubrani said:**
> I couldn't find the "NOAPIC" option when I am booting fro the CD. What's going on here?

You have to press F6 and add it to the kernel options line

try

noapic nolapic

---

