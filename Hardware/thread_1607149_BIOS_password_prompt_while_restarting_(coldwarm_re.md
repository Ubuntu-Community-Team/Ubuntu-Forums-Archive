---
title: "BIOS password prompt while restarting (cold/warm reboot)"
date: 2010-10-27
forum: Hardware
---

### Post by Oleq on 2010-10-27
Hi!

I would make it clear at the beginning - **I don't want to disable or recover BIOS my password**.

My laptop is **HP 6720S**.

The problem is as follows:
[LIST]
[*]When I boot my laptop - BIOS prompts for the password - **That's fine.**
[*]When I reboot Windows (XP) OS, BIOS never shows an `enter password` prompt - **That's fine as well - I'd like it to be the default reboot behavior - it's so much comfortable.**
[*]When I reboot any Linux (especially Ubuntu) OS - BIOS prompts for the password just like it was a regular *cold boot* - **That's bad!**
[/LIST]

I agree that the default cold-reboot behavior may be important for computer security, but it's annoying if you reboot very often. I was looking for grub2 boot parameters but neither **reboot=acpi,warm** nor **reboot=warm** work properly. All those parameters are listed in following source file: [http://lxr.linux.no/#linux+v2.6.30/arch/x86/kernel/reboot.c](http://lxr.linux.no/#linux+v2.6.30/arch/x86/kernel/reboot.c)

Is there any possibility to force Linux to do warm (Windows-like) reboot without BIOS asking for password?

Thanks in advance!

---

