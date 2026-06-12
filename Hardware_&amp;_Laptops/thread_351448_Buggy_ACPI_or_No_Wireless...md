---
title: "Buggy ACPI or No Wireless.."
date: 2007-02-01
forum: Hardware &amp; Laptops
---

### Post by aastaneh on 2007-02-01
Hi-

I recently moved from Gentoo to Ubuntu to make life simpler... well.. It's not working out that way.

If I boot with normal kernel options, I jump into a buggy DSDT and hal crashes due to my   /proc/acpi/battery/BAT1/ contents that hal does not expect,
([https://lists.ubuntu.com/archives/desktop-bugs/2006-November/062616.html](https://lists.ubuntu.com/archives/desktop-bugs/2006-November/062616.html))
making life unbearable. If I boot with acpi=off, my PCMCIA card no longer works and issues this kernel message:

[   40.298137] cs: pcmcia_socket0: cardbus cards are not supported.

If I can just have ACPI disabled and somehow get my PCMCIA to work, that would be just great.

My laptop is an Acer Aspire 3000 WLCI.

Any ideas?

---

### Post by anjin on 2007-08-19
I had a similar problem and I fixed it by changing my PC Card configuration in BIOS to "Cardbus/16-bit".

You might want to look in your BIOS to see if there is anything there like that.

---

