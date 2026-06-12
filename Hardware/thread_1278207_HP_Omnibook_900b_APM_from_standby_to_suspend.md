---
title: "HP Omnibook 900b APM from standby to suspend"
date: 2009-09-29
forum: Hardware
---

### Post by jur on 2009-09-29
Hello all,

I do hope someone can provide a solution to (what seems) a relatively simple problem with the BIOS APM of my HP Omnibook 900b laptops (anno 1999). 

I have 2 of these laptops (for home and office use), one with Ubuntu 7.04, the other with Xubuntu 7.04 (kernels 2.6.20-17-generic), both with acpi disabled and apm enabled (through /boot/grub/menu.lst and /etc/modules). ACPI never worked well  (probably due to the age of the laptops), anyway I prefer APM. 

The BIOS (= Phoenix 4.0 rev. 6.0) has adjustable APM time out power settings, i.e. standby after X minutes / suspend after Y minutes / hibernation after Z hours (via lphdisk to an aO-partition). Also these powerstages can each be enabled manually by Fn-keys. In standby- or suspend-mode the on-light turns orange (from green); when hibernating of course it goes completely off. 

Now, according to the HP-manual each stage (when left in quiet) should be automatically followed by the next, so in the order standby-suspend-hibernation.  This works OK from suspend towards hibernation. 

However,  from standby to suspend consistently fails. Instead of going into suspend after those Y minutes, the screen lights up spontaneously again like it was before standby, so back to square one. Then after X minutes standby starts once more, but again ends after Y minutes without going into standby. The same happens when standby has been entered manually (Fn-s).

It seems as if somehow the standby-to-suspend transition is thwarted by some other proces, which kicks the laptop back into fully  active mode. I disabled and even uninstalled screensavers, tried all sorts of other different settings, and searched/googled extensively, but couldn't find any clear explanation as to why and how to solve this issue, so am now hoping that forum members might help me out?

Thanks in advance,

Jur

---

### Post by ralph-d on 2009-10-24
I cannot offer a solution, but maybe some help: I'm writing this on a 900b "running" 9.10-rc (kernel 2.6.31-14). Booting with "acpi=force" gives me very unreliable power management support, so I'm willing to change that, if you tell me:

[LIST=1]
[*]how to enable APM without disturbing the system clock (it ran at double speed, when I plugged in the power supply under 6.06; that's why I'm trying 9.10 and ACPI now).
[*]how to provide a hibernation partition (lphdisk worked, but the red boot warning is still there).
[/LIST]

When I'll have successfully switched to APM, I'll investigate about the standby-suspend transition.

---

### Post by jur on 2009-10-28
Thanks Ralph,

Enabling APM:
instead of 'acpi=force': add 'acpi=off apm=on noapic nolapic' to the kernel in /boot/grub/menu.lst
add 'apm' to /etc/modules
create file in /etc/modprobe.d (called i.e. 'power') + add: 'options apm power_off=1 realmode_power_off=1'

Some of these may prove to be unnecessary or even too much for 9.10, in that case just delete something and try again.

APM shouldn't disturb the system clock. For hibernation you first have to make an a0 (Thinkpad) partition (use fdisk or cfdisk) starting right at the beginning of the disk, then run lphdisk.

Meanwhile, I discovered that disabling standby in the BIOS (thus skipping the X minutes wait),   enables automatic suspend after Y minutes. So the problem must be somehow in the standby-to-suspend transition ...

---

