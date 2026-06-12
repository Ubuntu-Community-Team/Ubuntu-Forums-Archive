---
title: "Unplug ac result in computer hang"
date: 2010-03-06
forum: Hardware
---

### Post by jukoz on 2010-03-06
Hey everyone!

I am using Ubuntu 8.04 64bit on an HP nx6125, kernel 2.6.24-26-generic

I need some help, before I go completely mad...

Since sometime last year (I believe with the upgrade of gnome-power-management, but not sure – also cannot find older package to check), I am experiencing a strange problem with my laptop. The problem comes and goes, cannot find the reason, nor the pattern.

Normal boot, logged in the system with X, normal use:
If I unplugged it from AC, the laptop works OK for about 10 seconds, then it hangs. The led for the disk is lit, the disk makes no noise or anything. Nothing in /var/log/messages, nothing in dmesg

At boot time:
If AC not plugged in, it says "stopping anacron" and later hangs, sometimes it boots fine in gdm.

Normal boot, not logged in the system, gdm running:
If booting with AC, and then switching to console with ctrl+alt+f1, and then unplugging AC, I get the message of stopping anacron, and the computer sometimes works OK.

Since the most obvious sign of a problem is the hdd led, I assumed there must be something wrong with the hdparm settings acpi daemon does. I followed the instruction on the ubuntu howto page regarding this, but unfortunately to no success.

I dissabled all hdparm settings in laptop-mode.conf, in /etc/acpi/start.d/90-hdparm.sh and in /etc/acpi/power.sh

The only way to be sure the laptop wont hang, is by stopping acpid with /etc/init.d/acpid stop

Now, I assume there must be something wrong with the acpi settings, but I cannot find what.
One more important information: I replaced the disk since this problem happened first, so I assume the disk is not the problem. Both disks were made by Samsung, first 120GB, current 160GB IDE

Regards

---

### Post by jukoz on 2010-03-06
Another strange thing:
if I stop acpid, the laptop still suspends AND wakes up.
Is this supposed to happen?

---

