---
title: "underclocking ubuntu"
date: 2005-07-24
forum: Hardware &amp; Laptops
---

### Post by pilotcp on 2005-07-24
hello all!

i'd like to know if it were possible to underclock my compaq laptop that is currently running ubuntu.
please don't ask why i would want to do such a thing!  lol!


thanks,
Charlie

---

### Post by jasmuz on 2005-07-24
Dude, all overclocking and underclocking takes place in the BIOS, not the OS.
you must search your BIOS to see if you can adjust the multiplier frecuency for the processor.

---

### Post by pilotcp on 2005-07-24
[QUOTE=jasmuz]Dude, all overclocking and underclocking takes place in the BIOS, not the OS.
you must search your BIOS to see if you can adjust the multiplier frecuency for the processor.[/QUOTE]
 ok, thanks...i had a feeling about that...my friend suggested i do this last night, and i haven't even tried it yet, and i just wanted to know if ubuntu was different in any way...apparently not...thanks for the help!!

---

### Post by slavisa on 2006-11-27
That is not true!

Through the MSR-Module the VID (Voltage identifier) can be set from the OS.

The CPU-frequency-Module does nothing else. It sets some combination of voltage information and frequency-multiplicator.

I found a very simple but functional daemon for that.

[http://www.tuxamito.com.es/cpupw/index.php](http://www.tuxamito.com.es/cpupw/index.php)

This Daemon just sets a lower voltage for every frequency-level. So no performance-loss takes place, but cpu stays much cooler.

When setting to low voltages, the system just hangs, but nothing should be hurt.
Setting too high voltages can be dangerous.

Please use it with caution, and read the manual *realy* carefully.
Nor me neither the developer will take responsibility for any damages on your Hardware.

With Dapper it worked, with Edgy somehow it doesn't.
maybe the msr-module of the new generic-Kernel is not compiled for my architecture.
Will try it with a self-compiled Kernel when I have time left (around 2015).

I waited a long time for something like this daemon. Great work. So please feel free to help the maintainer to develop it further.

---

