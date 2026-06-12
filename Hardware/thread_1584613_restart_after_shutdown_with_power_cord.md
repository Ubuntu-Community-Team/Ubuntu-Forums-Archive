---
title: "restart after shutdown with power cord"
date: 2010-09-29
forum: Hardware
---

### Post by Zorzo on 2010-09-29
I have a Toshiba laptop A300-157 and Ubuntu 9.10. At the shutdown of the computer system is restarted. **_Only when the power cord off system shut down normally_**.
 I tried version 10.04 and the same is happening. 

uname-r
2.6.31-22-generic-pae

BIOS version is V 1.9

I tried:

1. remove the "splash screen" in grub,
2. sudo shutdown-h
3. sudo halt
4. sudo shutdown-h-P
5. acpi_osi = Linux
6. adding acpi = force in rough
7. after adding "reboot = no Shutdown = no" ---  system restarts again

with: sudo gedit / etc / default / halt
and fail to mention adding a line that looks like this:
# Default behavior of shutdown-h halt. Set to &quot;halt&quot; or &quot;PowerOff.
/ Sbin / rmmod snd_hda_intel
HALT = PowerOff

with: Alt + SysRq +o  the system is restarted again.

Does anyone any suggestions to solve this problem?
Thanks

---

