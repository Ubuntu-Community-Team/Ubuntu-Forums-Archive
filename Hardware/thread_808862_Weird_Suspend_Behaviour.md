---
title: "Weird Suspend Behaviour"
date: 2008-05-26
forum: Hardware
---

### Post by em4r1z on 2008-05-26
MSI M670X nForce chipset | Mobile AMD Sempron 3500 | NVIDIA GeForce Go 6100 (256 Mb shared) | 2 Gb of RAM | Ubuntu 8.04 64 bits | Latest NVIDIA drivers | Compiz disabled

The current system's layout doesn't use a swap partition for I have yet to see more than 40% of memory usage when working. "Swappiness" was set to 0. Hence I've never tried to hibernate the laptop.
The discussed issue also existed when there was a swap partition, though.

The BIOS has two power management related options, 'PowerNow' and 'Enhanced power saving', which can be enabled/disabled. I've tried the four different permutations and the results are the same.

I've tried different workarounds (most of them suggesting to edit /etc/default/acpi-support and /etc/X11/xorg.conf) with no positive results.

1. I can suspend to RAM once (per restart) but the system cannot re-establish the wired connection upon resume. I can establish a wireless connection, though.

2. If I try to suspend again the screen goes black and after a few seconds the system fails to suspend and the session is restored. This makes it impossible to restart (the system will terminate all applications and turn off the screen but it's unable to halt.)

I don't know if this is related but if I set the screen to standby after X minutes within the Power Saving Options, the screen goes black and there's no way back.

Any leads on how to solve this issue?

---

### Post by em4r1z on 2008-09-23
Four months later, I'm still unable to suspend my laptop. I lost interest several weeks ago but since I never got a reply to my original question, I decided to resurrect the thread.

---

