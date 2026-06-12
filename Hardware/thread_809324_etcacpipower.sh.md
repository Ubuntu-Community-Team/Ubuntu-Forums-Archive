---
title: "/etc/acpi/power.sh"
date: 2008-05-27
forum: Hardware
---

### Post by afterkelsen on 2008-05-27
I've been playing a bit with laptop-mode today and stumbled upon the /etc/acpi/power.sh script... This script is run when laptop-mode is enabled and disabled. What worries me about the script is the following lines:

In the function laptop_mode_enable:
$HDPARM -S $SPINDOWN_TIME /dev/$drive 2>/dev/null
$HDPARM -B 1 /dev/$drive 2>/dev/null

and

In the function laptop_mode_disable:
$HDPARM -S 0 /dev/$drive 2>/dev/null
$HDPARM -B 255 /dev/$drive 2>/dev/null

Do these hdparm settings overwrite the settings laptop-mode sets? To me it looks like it.

If it overwrites then it is of course a serious problem since -B 1 really is very rough on the hard disk. And "-B 255" is the same as "-B 1" on some disks. Even if these lines do not overwrite what laptop-mode-tools does shouldn't they still be removed since they then serve no purpose? At least I can't see sense in setting the hdparm settings twice, whether the values are wrong or not.

Anyone?

---

### Post by Jacdeb6009 on 2008-05-28
> **afterkelsen said:**
> I've been playing a bit with laptop-mode today and stumbled upon the /etc/acpi/power.sh script... This script is run when laptop-mode is enabled and disabled. What worries me about the script is the following lines:

In the function laptop_mode_enable:
$HDPARM -S $SPINDOWN_TIME /dev/$drive 2>/dev/null
$HDPARM -B 1 /dev/$drive 2>/dev/null

and

In the function laptop_mode_disable:
$HDPARM -S 0 /dev/$drive 2>/dev/null
$HDPARM -B 255 /dev/$drive 2>/dev/null

...snip...

You may want to take a look at:

[http://ubuntuforums.org/showthread.php?t=805570](http://ubuntuforums.org/showthread.php?t=805570)

This doesn't directly answer your question, but it will provide an insight into another, more serious issue that you should be aware of.

Your assessment of the overwriting of parameters is AFAIK correct.  The question about "-B 255" is not so clear.  On some drives "-B 255" will turn of the power management and never park the heads, on others you need to use "-B 254" instead.

Anyway, there more detail in the link.

---

### Post by afterkelsen on 2008-05-28
Jacdeb6009: I am aware of the issues with many laptop hard drives. It's a mess ;) So far I just set the -B values in power.sh to the values I already set in laptop-mode.conf. At least this insures that power.sh doesn't overwrite laptop-mode and make the disks run with -B 1, which would brutally kill my disk in only a couple of months.

---

