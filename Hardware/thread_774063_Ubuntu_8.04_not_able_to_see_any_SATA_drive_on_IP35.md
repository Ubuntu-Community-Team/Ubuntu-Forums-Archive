---
title: "Ubuntu 8.04 not able to see any SATA drive on IP35-E"
date: 2008-04-29
forum: Hardware
---

### Post by nyker on 2008-04-29
Hi I have Abit IP35-E, 2x SATA II drive and trying to install Ubuntu 8.04. But it doesn't seem to see anything at the partition stage. No drive or partition is listed - just blank. Can someone with experience on this help? thanks!

Oh, I think IP35-E only has IDE mode. Not the ACHI mode for SATA controllers.

---

### Post by hermes0710 on 2008-04-29
In which mode is the drive set in bios? (ide,raid,achi)

---

### Post by nyker on 2008-04-29
I actually got it to install by using acpi=off option and run perfectly except that now I have no suspend nor hibernate options at all. This is very troublesome, don't really want to boot up clean every single time.

Anyways. It looks like an acpi problem. I also tried all_generic_ide irqpoll options, also boots up but as before no ACPI worked. when I suspend I get errors waking up the computer.

any advice?:confused:

---

