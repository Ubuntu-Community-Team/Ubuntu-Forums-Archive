---
title: "Booting Stuck At Checking Battery State"
date: 2005-12-24
forum: Installation &amp; Upgrades
---

### Post by jodef on 2005-12-24
I am not entirely sure this is the correct place to post this but since it happened on Kubuntu box placed it here. I did an upgrade from Breezy preview to final and encountered the above problem.

I checked the forums saw a few users encountering the problem but no definitive solution. As some posts indicated may be related to nvidia drivers but I didn't mess with nvidia drivers at all. In addition it sticks whether I am using the old kernel or the upgraded one. The exact message **scheduler....known not to support power-saving**

Any ideas on how I can boot into Kubuntu to solve this problem?

---

### Post by mlomker on 2005-12-26
I'd try disabling APM/ACPI in the machine's BIOS.  There's also some kernel command-line options that you can put into the grub menu, such as **noacpi**.  If you do a search on that you'll find a few threads.

I assume you've already tried Ctrl-C to skip past it?

---

### Post by jodef on 2005-12-26
It seems that all necessary packages weren't updated a subsequent reinstall and update through synaptic worked.

There does seem to be some issue though there are quite a few threads where others experienced the same problem.

---

### Post by trevorhawn on 2006-01-06
I am entirely new to Linux. I just installed Kubuntu on my HP Pavilion with Pentium 4. I had the same problem. One of my friends suggested it might have something to do with my video card. I installed a graphics card (Radeon 9250) for gaming a few months ago. When I switched to my onboard video chip in the BIOS, I booted up with out a snag. Hope this helps.

---

