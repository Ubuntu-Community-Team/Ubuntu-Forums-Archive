---
title: "boot to black screen after update to 16.04 xenial"
date: 2016-08-25
forum: Hardware
---

### Post by uwes on 2016-08-25
Hi,

after the update to ubuntu 16.04, my laptop (Samsung NP305E5A) boots to a black screen. The boot process continues since it is obviously reading from the hard drive and also playing the drums sound for the login-window after a while. However, the screen remains black from right after the grub-screen is gone and stays like that. Ctrl+Alt+F2 also does not take me to a usable command line. I found no way for the screen to show anything.

However, I did find something one might call a workaround. If I kill the booted laptop by pressing the power button for several seconds and then try the boot process again, ubuntu works absolutely fine with one notable exeption: grub gives me 30 seconds to choose my boot options instead of the regular 10s. This "workaround" also works if I kill the OS while it is still booting to a black screen and then boot again.  However, it is hardly a satisfactory solution to always boot the laptop twice.

I am not a newbie but also not very deep into ubuntu and I kinda ran out of google phrases to describe this problem. I did a clean new install of the system which did not help. Before this reinstall, I found an error message  in syslog or dmesg which said something about acpi and that the backlight brightness could not be set or determined. Unfortunatetly, I can't find this error message again after the reinstall. Well, I did dig into dsdt disassembly and assembly via iasl and might have detected an error, which I did not know how to resolve:

```

sudo cat /sys/firmware/acpi/tables/DSDT > DSDT.aml
sudo cat /sys/firmware/acpi/tables/SSDT1 > SSDT1.aml
sudo cat /sys/firmware/acpi/tables/SSDT2 > SSDT2.aml
iasl -da -dl *.aml
iasl -tc DSDT.dsl

Intel ACPI Component Architecture
ASL+ Optimizing Compiler version 20160108-64
Copyright (c) 2000 - 2016 Intel Corporation

Compiler aborting due to parser-detected syntax error(s)
DSDT.dsl   6433:                 If (LEqual (STCL, 0x0101))
Error    6126 -                  ^ syntax error, unexpected PARSEOP_IF

DSDT.dsl   6940:
Error    6126 - syntax error, unexpected PARSEOP_SCOPE, expecting $end and premature End-Of-File

ASL Input:     DSDT.dsl - 6940 lines, 320755 bytes, 2585 keywords
Hex Dump:      DSDT.hex - 203 bytes

Compilation complete. 2 Errors, 0 Warnings, 0 Remarks, 0 Optimizations 


```

However, it does not seem to be the core issue for my problem, as the boot error is still there after the reinstall but I cannot find an acpi error message in dmesg or syslog any longer...

I am quite lost now and would appreciate any hints on how to start tracing down the problem.
Thanks
Uwe

PS:
```

lspci | grep VGA
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek [Radeon HD 6520G]
02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Seymour [Radeon HD 6400M/7400M Series]

```

---

