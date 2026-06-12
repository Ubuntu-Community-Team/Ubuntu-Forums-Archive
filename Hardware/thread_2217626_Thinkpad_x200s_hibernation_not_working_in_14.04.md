---
title: "Thinkpad x200s hibernation not working in 14.04"
date: 2014-04-18
forum: Hardware
---

### Post by donato-sardella on 2014-04-18
It's a fresh install (but hibernation previously worked in 12.04).

Enabled all the energy saving options for the i915 driver as detailed here, used to run them in 12.04 as well
[https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks](https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks)


When resuming the system would lock showing a login screen with no possibility to interact, got a kernel error popup when I rebooted.


Suspecting issues from those settings I deleted them from grub and tried again, this time resuming works but my network cards are dead.


How can I troubleshoot this issue? This is my first ubuntu upgrade after using 12.04 for almost a year and even if I understand that a new release might have rough edges I'm considering to go back to 12.04 and wait a few months of bug fixing...



EDIT
fixed after a clean install

---

