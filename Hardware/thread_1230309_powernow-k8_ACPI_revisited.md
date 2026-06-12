---
title: "powernow-k8 ACPI revisited"
date: 2009-08-03
forum: Hardware
---

### Post by Azuu on 2009-08-03
When I first booted into Ubuntu I had the [double timing bug]("http://ubuntuforums.org/showthread.php?t=75281") which was solved by making grub boot with the command:
acpi=off

This is fine and dandy but I lose the safety and stability of my powerdown. The computer actually cant turn the processor off, it just turns the hardrive and no longer can it hibernate. I found a [clue as to why]("http://ubuntuforums.org/showthread.php?t=1110194&highlight=ACPI+PSS") and would like to see if anyone else still sees this bug:
> Firmware bug powernow-k8 Bios does not provide ACPI PSS objects in a way that Linux understands
On their bootup.

---

