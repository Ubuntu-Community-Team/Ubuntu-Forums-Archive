---
title: "ACPI wake up: shutdown vs hibernate"
date: 2008-06-10
forum: Hardware
---

### Post by becvert on 2008-06-10
Hi all,
I'm trying to make the ACPI wake up working under Ubuntu Hardy.
My motherboard is a Asus A8N32-SLI deluxe.
Configured from the bios, the RTC alarm works great but when it comes to let ubuntu update the bios via ACPI there is a hitch.
I've tried pretty much everything that is said in this guide [https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake).
without luck unfortunately.
Well actually my PC does not wake up after a shutdown but
what I found strange though is that it does wake up from hibernation. What I do when going to hibernation is the usual echo to /proc/acpi/alarm and issue the pm-hibernate command which ends up with a full shutdown if I may say from a power perspective. and without problem the computer resuscitates at the given time.
How come?
thanks

---

### Post by becvert on 2008-06-11
I think the power state of shutdown or hibernation is the same. S4 or S5 somthing like that. which means the PC can only be rebooted from the power button, RTC alarm or WOL. do you agree with me? if yes it's definitively a problem into linux/ubuntu.

---

