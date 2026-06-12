---
title: "Starting hotplug subsystem... nothing? (fresh install of Ubuntu)"
date: 2006-01-14
forum: Hardware &amp; Laptops
---

### Post by happogiri on 2006-01-14
Hello!

I just installed Ubuntu 5.10 i386 on my Asus S5A laptop. I took the CD-rom out of the drive when asked and booted. Everything went fine untill after 'setting up network' or something like that,  came the "Starting hotplug subsystem" and the machine just waits and waits... I can write but nothing happens. Is there anything to do? Before installation I tried the Live-cd (same version) and everything worked fine. :(

---

### Post by 23meg on 2006-01-14
Try booting with the following kernel options: **noapic**, **pci=noacpi**, **acpi=off**, **noacpi**. Choose the kernel you normally boot with in the GRUB menu, hit E, scroll to the main boot line (the longest one) and enter one of these, hit Enter and then B.

Try them one by one, and if they still fail, try permutations.

---

### Post by happogiri on 2006-01-15
I booted couple of times, and then just waited (actually I was here writing that firs post) and it went past that. Now it's been working ever since with no waiting! \\:D/

---

