---
title: "suspend/wakeup problems"
date: 2009-05-27
forum: Hardware
---

### Post by feh on 2009-05-27
Hi folks.

I think this is actually the case for all variants, but my specific case is kubuntu:

I've got a new install of Kubuntu 9.04 on an ASUS M3N78-VM motherboard, and I can't get the machine to suspend/wake properly.

This is a desktop system - I've installed several power management packages, but none of them work as desired. What I want:

- suspend to RAM (I believe this is state S3), where the fans, CPUs and drives shut down, and the machine wakes up for either a myth recording, or from a key press or mouse event

In other words, not hibernate, but a very low power state where the machine is usable within a few seconds after waking.

To answer some initial questions you may have:

[LIST]
[*]acpid is running
[*]S3 is supported in the BIOS
[*]when I suspend now (either pm_suspend, kpowersave, whatever), the screen goes black, but the fans don't stop, and there's no way to get the machine to respond to any input at this point I have to reset it
[/LIST]

However, I have found that the /etc/acpi/sleep.sh command actually is able to put my machine to sleep (suspend to ram). If I run that command without arguments, nothing happens, but if I use the "force" argument, the machine does suspend.

The problem is that it doesn't resume properly. It tries to wake up, but it spews a bunch of error messages regarding my root filesystem, and then unmounts it, requiring a reset of the machine.

I've done some googling, and I'm wondering if this is an XFS problem. Are any other folks using XFS and are able to get their machine to suspend/wake?

Thanks!

---

