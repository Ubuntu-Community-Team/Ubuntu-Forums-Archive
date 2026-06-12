---
title: "Problems with acpi on ubuntu 10.10 on eee-pc 1101HA (system freezes)"
date: 2010-11-22
forum: Hardware
---

### Post by mennowo on 2010-11-22
Hi,

running Ubuntu Netbook Remix 10.10 on my eee-pc 1101HA, I am running into trouble with acpi.

After installing Ubuntu, most things are fine, and I am able to get 1366x768 resolution using the poulsbo drivers. However, the system suddenly hangs after few minutes, not clear when and why. Everythings stops, no response, screen freezes but stays on. Then I can only reboot by pressing the power button for 10 seconds.

I have looked into this, and think the problem is with the way Ubuntu is speaking to the hardware of the laptop, especially the acpi messages between the system and the processor. Removing the "acpi_osi=Linux" flag from /etc/default/grub (or from the boot menu by pressing e and editing the flags) seems to resolve the freezing issue. However, removing this flag also disables almost all acpi binded keys, backlight, speed control. Only volume keeps working.

In the /etc/default/grub file I also added the flag "noapic", to avail as regards the issue of freezing the system. I am using [Jupiter ]("http://sourceforge.net/projects/jupiter/")in conjunction with the eee addon to access to system control form  the system tray.

Any suggestions on how to solve this issue?

Thanks! Menno.

---

### Post by mennowo on 2010-11-22
In case anyone else runs into this issue: I seem to have resolved it by removing the "acpi_skip_timer" flag (without the quotes) from the GRUB_CMDLINE_LINUX="..." line in /etc/default/grub. This keeps the fn-keys for increasing and decreasing screen brightness on the 1101HA active, and the system has not freezed so far. 

I also followed [this thread ]("http://ohioloco.ubuntuforums.org/showthread.php?t=1229345")to edit xorg.conf, though I am not sure if it increases or decreases performance. It does enable me to enable desktop effects though. However I may decide to remove those lines again to try the difference.

What I am still really wondering about: how to decrease minimum screen brightness? Using the fn-keys allows me to decrease the brightness in 15 steps, but the gui that is displayed shows 20 steps, of which 5 below the current minimum, that are shown as I press the keys, but do not affect brightness. 
Consequently, minimum brightness in Ubuntu is much brighter than in Windows XP, which I find a pity, cause I like very low brightness at night or to save battery.
I know it is possible to use dark backgrounds, dark theme, but this is not quite the same, it looks different, and battery life is not expanded.

Help and suggestions on that issue still very welcome (as long the system doesn't freeze, I assume the previous issue resolved...).

Bye, Menno.

---

