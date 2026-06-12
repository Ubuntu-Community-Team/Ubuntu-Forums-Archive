---
title: "laptop stalls at &quot;uncompressing linux...ok, booting the kernel&quot;"
date: 2006-01-17
forum: Installation &amp; Upgrades
---

### Post by tihom on 2006-01-17
pls help. i tried to install ubuntu both in live and install modes but my laptop just hangs. from the beginning this is what happens

as the computer starts

[B]this is the ubuntu live cd
press f1 for help and advanced options

for the default live system, press enter
boot:_[/B]
after i press enter

[B]loading /install/vmlinuz.........................
loading /install/initrd.gz...............................

ready.
uncompressing linux...ok, booting the kernel.[/B]_

after this there is no response. i have waited for half an hour. i tried doing expert option and the normal install CD but the result is exactly the same.

need help....have read so much..and now really want to get into action.

---

### Post by dcstar on 2006-01-17
[QUOTE=tihom]pls help. i tried to install ubuntu both in live and install modes but my laptop just hangs. from the beginning this is what happens

as the computer starts

[B]this is the ubuntu live cd
press f1 for help and advanced options

for the default live system, press enter
boot:_[/B]
........[/QUOTE]
Try this at the boot prompt:

linux acpi=off

---

