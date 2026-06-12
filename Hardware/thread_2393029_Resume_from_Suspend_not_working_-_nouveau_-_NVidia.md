---
title: "Resume from Suspend not working - nouveau - NVidia GTX765M MSI GS70"
date: 2018-05-28
forum: Hardware
---

### Post by Emilie on 2018-05-28
I have spent many hours trying to get Suspend to work on my MSI GS70 ([https://www.msi.com/Laptop/gs70-stealth.html](https://www.msi.com/Laptop/gs70-stealth.html)) with either the nouveau or nvidia drivers. It is an optimus laptop with Intel i915 and NVidia GTX 765M.

Hibernate works.  Suspend seems to work, but instead of resuming, it reboots.

Have tried with multiple versions of both the closed source nvidia drivers (latest try was 396.24) and nouveau (1.0.15-2). I would prefer the nouveau drivers because it seems like Prime and some intelligent fan-control is now working but would be happy with either.

Following: [https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend) the "freezer" step works (device suspends and resumes. pm-suspend.log says resume=success). But when doing the "devices" step pm-suspend.log claims the suspend was successful but on resume the screen turns on but everything is locked up (no keyboard, mouse input, cannot change to terminal, etc.).

This makes me think some device is not resuming correctly.  Unfortunately the "magic" reporting is not very informative:
```
[    0.912360] evm: HMAC attrs: 0x1
[    0.913548]   Magic number: 9:928:176
[    0.914269] acpi device:39: hash matches
[    0.914947] acpi device:0c: hash matches
```

I cannot find anything that matches 39 or 0c if I use the "acpi=off" kernel parameter the computer locks up on boot.  With "acpi=oldboot" and "acpi=ht" it boots but exhibits the same problem.

I have tried blacklisting every module possible to ensure it was not the soundcard, bluetooth, network, etc. causing the resume issue but no difference (see lsmod.txt for remaining modules shown in lsmod).

There are no BIOS updates from MSI. After decompiling the DSDT I found there was a LINUX flag in it, so I am now booting with acpi_osi=Linux (also tried "Windows 2013" as that was in the DSDT as well), no difference.

Attaching relevant logs here, would love any help.

For all of these tests I am using: 
```
sudo sh -c "sync && echo 1 > /sys/power/pm_trace && pm-suspend"
```
and "resuming" by pressing the power button.

[LIST]
[*][ATTACH]279899[/ATTACH] = /proc/acpi/wakeup 
[*][ATTACH]279900[/ATTACH] = pm-suspend.log after "freezer" test 
[*][ATTACH]279901[/ATTACH] = pm-suspend.log after "platform", "devices" test or regular resume (always says success) 
[*]Linux Tehanu 4.15.0-15-generic #16-Ubuntu SMP Wed Apr 4 13:58:14 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux 
[*][ATTACH]279902[/ATTACH] = lspci -nn 
[*][ATTACH]279903[/ATTACH] = minimal lsmod 
[/LIST]

---

