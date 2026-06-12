---
title: "No CPU frequency/voltage scaling in 11.10 / 3.0.0-13-generic? Losing my sanity here!!"
date: 2011-12-08
forum: Hardware
---

### Post by r00x on 2011-12-08
Hey all, I've been trying to do this on my own for weeks (mostly reading, but still) but I'm at the end of my tether and admit I need help, so:

I have an Intel Atom-based SBC (n270) here which I'd very much like to get running with all the ACPI/EIST goodies one can expect from your average Windows install.

However, it's not playing ball, and the system is getting *very* hot for a tiny little Atom machine.

If I pop cpufrequtils on the system I see the system is electing to use the stupid p4-clockmod driver, which as I understand it supports frequency scaling but not voltage control. It blithely states this in the dmesg output, and tells me that I should be using the acpi-cpufreq driver instead.

However, in /lib/modules/$(uname -r)/kernel/drivers/cpufreq *there is no asfafads acpi-cpufreq.ko* module-thing to be found!! In fact, I recall reading somewhere that it had possibly even been REMOVED, and just isn't available any more. It's entirely rage-inducing to read all these posts about how we should simply modprobe acpi-cpufreq and be on our merry.

It seems a ton of the documentation for all things involved in remedying this are out of date/don't apply to the new 3.x.x kernels and Oneiric Ocelot in general. I'm totally lost, so could someone explain to me how on Earth frequency/voltage control is implemented in 11.10??

What should I be looking for? I'm going bonkers here!

I've looked at: 

**+** Checking dmesg for ACPI-related errors. I found:

```
ACPI: no DMI BIOS year, acpi=force is required to enable ACPI
```

Which I had already added to GRUB, so that's fine. 

**+** Disassembling the DSDT table and recompiling to find errors. I found and corrected two, but I got stuck trying to wade through outdated documentation into how to shoehorn a surrogate DSDT into the new 3.0.0-x kernels. Bah. They didn't appear to be crucial errors anyway. I did note that the XSDT, FACP, APIC, MCFG and OEMB were all compiled with the terror-inducing MSFT compiler flag, rather than INTL. Hmm.

**+** Messing around at length with all this cpufreq business. I get the feeling that I should be installing cpufreq-utils on 11.10. Something about all the CPU scaling business now being handled elsewhere? cpufreq-info returns the usual information on my Atom processor, including the correct range of possible frequencies, but also notes that the driver is p4-clockmod and the governor is locked to "performance".

**+** Installing indicator-cpufreq from ppa:artfwo/ppa allows me to set the CPU frequency manually and change governors between performance and powersave. Needless to say as p4-clockmod doesn't support EST the temperatures didn't change and I couldn't select other governors without them defaulting back to 'performance' within a few seconds.

**+** Trying different BIOS revisions. I've tried all revisions available for this board. In each, ACPI was set to the latest version 3.0.

**+** Specifying acpi_osi=\\\"Linux\\\" (which apparently needs that many backslashes) and \\\"Windows 2006\\\" in GRUB, neither of which made any difference.

I also found bug submissions [here ]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/797190")and [here ]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/847134"), are these anything to do with my problem, do you reckon?

HELP :D much appreciated

---

### Post by garyrobertdavidson on 2012-03-19
Did you sort it out? or loose your sanity..

All that I have found on the net is that you should use acpi_cpufreq instead of p4_clockmod but its not there..

I have over 50 mini pc's which are overheating all around the world.. desperately need some help

---

