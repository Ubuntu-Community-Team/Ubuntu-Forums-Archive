---
title: "Getting suspend to work with fglrx"
date: 2008-10-24
forum: Hardware
---

### Post by mkoonstra on 2008-10-24
Hi all, I am trying to get suspend and hibernate to work on my system.

This is my setup:

MSI K9A Platinum
AMD Athlon X2 4800+
Ati Radeon X1950 Pro

I am using kernel 2.6.24-21-generic and the fglrx 8.10 release (newest).

What I want is suspend and hibernate to work on this system. It is working under Windows XP but not with the opensource radeonhd driver nor binary fglrx driver.

Suspending is broken, hibernating works most of the time. 

I have tried running "/etc/acpi/sleep.sh force" as suggested in some topics on this forum to suspend and resume the system, but it did not work as expected. Maybe anyone else can provide some tips to get suspend to ram to work?

---

### Post by ezzieyguywuf on 2008-10-26
i've just now discovered a fix for this and posted it [here]("http://ubuntuforums.org/showthread.php?p=6034984#post6034984") i hope that helps you

---

