---
title: "&quot;io scheduler cfg registered (default)&quot; crash"
date: 2006-10-27
forum: Hardware &amp; Laptops
---

### Post by esemba on 2006-10-27
Hi, yesterday I've installed 64bit version of Edgy Eft, tried to boot the live cd, but ubuntu hanged on. The error line above is a bit mystery for me, so I googled and found I should boot the live cd with **noapic** and **acpi=off** parameters. So I did that, the login screen was ugly, but ubuntu booted up. But after the installation, when I tried to boot, error screen occured again. Don't know why. 
Btw: I'm installing ubuntu on asus notebook and I used Dapper Drake before, with no problems.

Any suggestions? Please!

---

### Post by zgornel on 2006-10-27
Seems to be a problem with the IO Scheduler. Try adding "elevator=deadline" in your kernel parameter list (no quotes) and removing any "elevator=cfq" you encounter. The boot options are available in /boot/grub/menu.lst

---

### Post by esemba on 2006-10-27
thanks, but unfortunately, doesn't work. I've partially solved that by adding "noapic" and "acpi=off" to the kernel boot parameters in menu.lst. It looks like it works fine, but I don't know what can happen, when acpi is off. Does it affect behavior of my notebook, battery lifetime etc? And I don't know, how to get rid of the ugly ubuntu boot screen...

---

### Post by zgornel on 2006-10-27
Apic does not affect the laptop. acpi=off does, it manages standby states as well as the power management options. For mor information of ACPI, [http://www.acpi.info/](http://www.acpi.info/) . I have no idea whatsoever why it displays a IO scheduler error if disabling ACPI resolves the hang...

---

