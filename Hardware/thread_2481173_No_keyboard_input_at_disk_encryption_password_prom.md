---
title: "No keyboard input at disk encryption password prompt"
date: 2022-11-21
forum: Hardware
---

### Post by thomasthomas332 on 2022-11-21
**SOLUTION: adding i8042.direct i8042.dumbkbd i915.enable_psr=0 as a boot parameter to GRUB file or to kernelstub (sytemd) i.e.:**
**sudo kernelstub -o "i8042.direct i8042.dumbkbd i915.enable_psr=0"**

Hello,

I have this weird and annoying issue, which I tried solving by myself to no avail. After turning on my new laptop with a freshly installed Ubuntu 22.04.1 LTS, at the "Please unlock disk encryption" prompt the keyboard never works from the start, meaning that around 20 seconds pass until I am able to enter the password and sometimes it doesn't start providing input at all. The keyboard backlighting works and the keyboard works as intended before and after the encryption password prompt including the UEFI and on Windows (Live USB). However, the same issue occurs after the laptop has been suspended and awakened on the login screen. My wireless keyboard works flawlessly as well so I reckon it must be connected to the internal keyboard driver.

I have found others with similar issues but no solutions e.g.
[https://www.reddit.com/r/pop_os/comments/s7po8l/lenovo_laptop_keyboard_not_working/](https://www.reddit.com/r/pop_os/comments/s7po8l/lenovo_laptop_keyboard_not_working/) 
[https://askubuntu.com/questions/1316686/keyboard-not-working-on-lenovo-ideapad-slim](https://askubuntu.com/questions/1316686/keyboard-not-working-on-lenovo-ideapad-slim) 
[https://forum.manjaro.org/t/keyboard-takes-time-to-startup-on-boot-and-login-after-long-intervals/89030](https://forum.manjaro.org/t/keyboard-takes-time-to-startup-on-boot-and-login-after-long-intervals/89030) 

Things I have tried:
[LIST]
[*]Clean re-install + all possible updates + xserver-xorg-input-all (1:7.7+23ubuntu2)
[*]UEFI/BIOS update
[*]Checking keyboard localisation
[*]Disabling slow keys
[*]Switching input devices during the disk encryption prompt (Fn + spacebar)
[*]trying other distros (PopOS, Manjaro) -> same issue!
[*]trying another Laptop: still the same issue(!) on an Asus Vivobook S13X
[/LIST]

Considering all the above it would be safe to assume that the keyboard has no defect and that this issue only appears on Linux.  

OS: Ubuntu 22.04.1 LTS
Laptop: Lenovo Yoga Slim 7 Pro 14IHU5 O
BIOS Version: FJCN72WW
BIOS Revision: 1.72
Firmware Revision: 1.32

I would greatly appreciate any other suggestions to solve this...

---

