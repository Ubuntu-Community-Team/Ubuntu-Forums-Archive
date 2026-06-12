---
title: "CPU fan won't slow down"
date: 2009-11-04
forum: Hardware
---

### Post by me13221 on 2009-11-04
Hello everyone,  ACPI troubles seem to crop up every upgrade cycle.  Just installed 9.10 on a brand-new computer with AMD Athlon 5050e processor and 780G chipset.  lm-sensors is configured properly.  Load is 0.00 and the CPU temp is only 40C, but the fan is turning at full speed, starting from boot.  It never slows down.

There are a number of tips recommended by various forum posts: 
[LIST]
[*]Check BIOS settings (AMD CoolnQuiet is enabled -- I can't find any other relevant settings)
[*]Install and configure powersaved (done - no effect)
[*]add acpi_osi="Linux" to grub menu.lst (this advice no longer applies to 9.10)
[/LIST]

As far as editing the grub menu, I tried making changes to /etc/default/grub so that it now includes:

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=linux"

```

ran update-grub, rebooted.. no effect.

so I've tried everything I can and the fan continues to spin at full speed.  This is not going to work for an HTPC.

Can anyone step me through the process of getting my fan speed to adjust to CPU temp?  I've noticed a number of other people complaining about their CPU fans misbehaving, but most of the forum threads come up empty.  So, I'm making a new one.

thanks in advance. :D

---

### Post by demikid on 2009-11-06
Same case here. I have a sahara laptop that worked fine with previous releases.Ubuntu 9.10 kernel issues. I booted the live cd using acpi=off nolapic noapic options as nothing else would work.
After installation i had to pass those same parameters again.
The fan now runs at full speed making loud noises :confused:. i have explored other options, like leaving out acpi=off - this makes the system to freeze after awhile. 
How can i slow the fan down.As things stand, i am back to Jaunty.

---

### Post by archie.maskill on 2009-11-06
[Edit: I don't think this is the same issue that other people are experiencing.  A reboot cleared up the problem]
I'm also having fan-related issues in 9.10, which I definitely didn't have in 9.04.  I'm using an aging Dell laptop, and the fan is fine for about 5 minutes after waking it up from standby.  Once it's warmed up a bit, the fan kicks in.  The CPU cools, but the fan does not switch off.  'top' does not reveal any significant CPU usage.

---

### Post by danastasio on 2009-11-13
i dont know what the problem is, my first thought was gnome itself honestly. and when i moved to arch linux (totally against my will btw!! ...i hit enter a few too many times in the partition autoconfig *sob*) i have the same problem. whats strange is that it starts on full just after GDM is loaded, and after five minuets or so slows down to a more managable speed

---

