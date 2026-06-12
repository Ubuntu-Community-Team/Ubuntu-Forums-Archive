---
title: "Haier A20 notebook: several probably ACPI-related issues"
date: 2008-05-26
forum: Hardware
---

### Post by rekado on 2008-05-26
Hi, I've bought a new laptop some days ago. Here are the specifications:

Haier A20 notebook
Intel T2370 @ 1.73GHz (Core Duo)
SiS M671 Mirage 3
Synaptics touchpad
Integrated Webcam

I faced severe graphic problems, Ubuntu 8.04 64bit didn't even install at first. Had to start it with the following options: ```
"noapic nolapic acpi=off vga=791"
```
Now I can only boot with the options ```
"noapic acpi=off apm=power_off"
```

I installed the patched open 2D driver as explained here ([http://ubuntuforums.org/showthread.php?t=615094](http://ubuntuforums.org/showthread.php?t=615094)). I'm still facing some difficulties which might be related to ACPI:

[LIST=1]
[*]With self-compiled 2D driver from Chen Chao Yu at SiS (source under GPL license) videos don't play in full-screen, at boot-up the screen's brightness fades from faint to gleaming, showing a turquoise-grayish pale pattern with a cyan rectangle on the left bottom corner of the screen.
[*]CPU load spikes extremely high when doing nothing special but only moving windows.
[*]Sound is very soft; is normal when booting with pci=bios_irq but internet connection will fail and system will run very slowly with this option enabled.
[*]on boot-up, when attempting to reconfigure xserver and when executing displayconfig-gtk the following error occurs:```
FATAL: Error inserting battery (/lib/modules/2.6.24-16-generic/kernel/drivers/acpi/battery.ko): No such device
```
[*]the web-cam (tested in Cheese) obviously is zoomed to maximum; it also seems that some optimizations are turned on which results in a horrible slowly rendering, overly saturated picture. Is there a way to configure the devices parameters somehow?
[/LIST]

Did anyone experience the same weird behavior when using the SiS 2D driver?
Is there any way to get rid of that battery error message?

I would appreciate any help! These errors seem so arbitrary...

BTW: the laptop came with Vista pre-installed and the CPU load also spikes a lot when only moving a window or even doing nothing. But in Vista Aero is enabled - in Ubuntu Compiz doesn't even work because of the missing OpenGl driver, so it may not be a performance problem. Ubuntu 8.04 (i386) works very very well with Compiz on my other Haier notebook (Haier A61 with Intel Celeron 430M @ 1.7GHz [?]) which I bought last year.

---

### Post by rekado on 2008-08-11
I just noticed that Haier A20 is the same as Clevo M721S.

---

### Post by rekado on 2008-09-19
Actually, I think that the problems just come from turning off ACPI at boot time. Without ACPI I also don't have any information about remaining battery life. This notebook is new, so ACPI should be working, shouldn't it?
Is there anything else I could tweak to let Ubuntu boot and keep ACPI support? At the moment when booting with ACPI the boot process hangs when detecting the CPU.

---

