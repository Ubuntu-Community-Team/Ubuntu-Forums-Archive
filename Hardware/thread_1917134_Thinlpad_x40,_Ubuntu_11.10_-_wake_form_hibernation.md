---
title: "Thinlpad x40, Ubuntu 11.10 - wake form hibernation - a random event?"
date: 2012-01-29
forum: Hardware
---

### Post by deckoff on 2012-01-29
Thinkpad x40.

Ubuntu 11.10.

Kernel - 3.2 (installed form deb)

Video drivers from xorg-edgers ppa.

The machine will wake up OK from hibernation most of the time. Sometimes, though, the PC will start the waking up, but will stop, and the caps lock indicator will flash on and off (kernel panic???) I have to power off the PC, and restart after first boot, for hibernation to work properly.

It seems the problem happens when the laptop is unplugged( battery only). The battery has power enough power left for the machine to work.

I found this article [here]("http://www.thinkwiki.org/wiki/How_to_make_ACPI_work"), (ACPI S4 hardware signature mismatch part) but not sure what to do, do I have ACPI in kernel or not. 
Edit: Adding ```
acpi_sleep=s4_nohwsig
``` in grub to kernel boot options does not make any difference

Sometimes, the PC will fail to hibernate and the PC will stay on, but I assume the problems are unrelated.

Swap is 4GB, ram - 1GB, this should be more than enough.

Any ideas?

---

### Post by deckoff on 2012-01-29
I installed uswsusp.
Running 
```
s2disk
``` 
will result in 
```
s2disk: Could not lock myself. Reason: Cannot allocate memory
```

---

### Post by deckoff on 2012-01-30
Most probably the reason was a hardware issue - I changed the motherboard and cannot reproduce the issue anymore.

---

