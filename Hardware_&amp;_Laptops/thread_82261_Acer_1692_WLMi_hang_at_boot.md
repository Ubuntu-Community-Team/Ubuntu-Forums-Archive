---
title: "Acer 1692 WLMi: hang at boot"
date: 2005-10-26
forum: Hardware &amp; Laptops
---

### Post by stefanborremans on 2005-10-26
Hello,

I have an Acer Aspire 1692 WLMi (about 2 months old). I downloaded the last version of Ubuntu, version 5.10 live DVD and I tried to boot. When I press enter at de boot prompt, it crashes at the sentence "Uncompressing linux... ok, booting the kernel". That sentence stays on the screen, and the computer doesn't respond anymore.

Any suggestions?

---

### Post by Muffe on 2005-10-26
Boot with this command: 'linux acpi=off'

That works on my Acer Travelmate 3000.

---

### Post by Zim_ on 2006-03-26
I had the same problem.

Computer: ACER Asprire 1692 WLMi
Ubuntu: 5.10

Turn the computer on, insert the CD and boot it. When you see the screen showing "boot: " enter "linux acpi=off" (without ") as Muffe said. Continue with the installation.

---

