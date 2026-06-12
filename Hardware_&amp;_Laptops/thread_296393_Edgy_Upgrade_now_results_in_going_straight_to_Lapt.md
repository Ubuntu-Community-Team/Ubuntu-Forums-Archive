---
title: "Edgy Upgrade now results in going straight to Laptop Suspend mode"
date: 2006-11-09
forum: Hardware &amp; Laptops
---

### Post by bluegecko73 on 2006-11-09
I just upgraded from Dapper 6.06 to Edgy yesterday and after rebooting I get the new splash screen with progress bar, but soon after that my machine powers off to what I think is Suspend to Ram mode because if I try to power on I just get a black screen, shortly followed by it turning off again.
The only way I've managed to get some success is to boot into recovery mode, login as root and then run startx to get X windows up. Switching to my user account and trying to start X Windows fails with permission problems.

I've seen the Known Issue about laptops and dual batteries, but my laptop (a Dell L400) doesn't have dual batteries, but it does sound as though its some power management issue. This happens if I'm running off my battery of the power lead.

Anyone have any ideas as to how to get round this or fix it?

---

### Post by bluegecko73 on 2006-11-11
Managed to get things working again by disabling acpi in the boot menu. After adding "noacpi acpi=off" to the end of the appropriate boot option it booted up fine. Hopefully a fix to acpi at some point will allow me to re-enable acpi later on.

---

