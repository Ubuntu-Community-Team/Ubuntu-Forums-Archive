---
title: "Thinkpad T21 suspend does not work"
date: 2006-07-02
forum: Hardware &amp; Laptops
---

### Post by mjgumbley on 2006-07-02
Suspend on a Thinkpad T21 Model 2647-6BG does not work. Could anyone tell me why?

The system appears to go into standby fine (I get the half-moon 'I'm in standby' indicator) - but it refuses to come out of it by pressing the usual 'Fn' key. Caps lock makes the caps lock indicator toggle though, when it's in standby. To get any response from the system, I have to remove the battery, replace it, and reboot.

I've tried adding 'noacpi' to the kernel boot options via grub - had no effect.
I've tried the following changes to /etc/default/acpi-support:
* uncommenting ACPI_SLEEP=true and this had no effect.
* changing ACPI_SLEEP_MODE from mem to standby, and the only difference was a different series of beeps as the system went into suspend.
* I've tried both combinations of these changes - to no effect.

Hibernate doesn't work either, but I'll get suspend working first. (Unless you know a 100% safe way of getting hibernate working - yes, I do have enough swap space available)

---

