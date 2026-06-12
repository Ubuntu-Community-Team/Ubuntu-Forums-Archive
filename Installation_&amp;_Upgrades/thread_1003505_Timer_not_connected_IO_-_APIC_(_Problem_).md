---
title: "Timer not connected IO - APIC ( Problem )"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by robertson-lee on 2008-12-06
I ordered this free version Ubuntu 7.10 long time ago. Today I installed it into my laptop.( Windows XP ). So I managed to successfully installed this Ubuntu. When I restarted, I clicked on Ubuntu 7.10 - ( from the list of operating systems ) It gave me this error message within a split of, like 1.5 seconds.

Not connected to IO - Apic

and it went blank black screen. I have to turn off from the power manually to restart my laptop again. What do you suggest I can do now?

Thank you very much.

---

### Post by Partyboi2 on 2008-12-08
There are a few things you could try. 
1. You could try booting using noapic as a boot option. You can add this by pressing ESC when booting and at the grub menu highlight the kernel you are going to boot into and press "e" then hight the line starting with "Kernel" and press "e" again then at the end of the line add ```
noapic
``` then press"b" to boot. If this works then you will need to make permanent. 

2. If you are able try disabling IOAPIC  in your bios.
3. Try updating your bios if you are able to.

---

