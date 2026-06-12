---
title: "CPU frequency scaling unsupported - HP EliteBook 8560w"
date: 2012-03-15
forum: Hardware
---

### Post by McGee23 on 2012-03-15
Hi!

I know, there are a lot of threads about CPU frequency scaling, I've read all I found.

Here's the problem: When I try to use CPU frequency scaling (ie. the gnome applet), I get an error message "CPU frequency scaling unsupported".

The hardware is a HP EliteBook 8560w, with Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz processor. I already updated bios to the latest version (68SVD Ver. F.22) but it didn't help.
The log says "[Firmware Bug]: BIOS needs update for CPU frequency support".

Does anyone know how to solve this? Is tweaking the DSDT an option? If so, how is this done?

Thanks a lot in advance.

[update:]
Experimenting with the kernel modules shows some new error messages:
* using acpi-cpufreq.ko shows "[Firmware Bug]: ACPI: Invalid BIOS_PSS frequency: 0x80000000 MHz" in the log and "Input/output error" on the terminal,
* using p4-clockmod.ko gives "[Firmware Bug]: ACPI: BIOS_OSI(Linux) query ignored" in the log and "Invalid argument" on the terminal

Hope That helps anybody giving me a hint what to do...

---

### Post by haines.justin on 2012-04-04
McGee,
I've encountered the same problem on my 8560w (though mine has the i7-2720QM).  The problem arose after I updated my BIOS from F.03 to F.25.  The problem does not exist with BIOS F.03 and earlier.  Unfortunately, due to some changes in BIOS security in F.20, you cannot downgrade below F.20.  I'm currently running with F.20 and CPU scaling is not working.

I spent a long time chatting with HP support yesterday and finally got the answer out of them:  Intel TurboBoost was causing overheating issues, so they disabled it in F.20.  Somehow this breaks the ACPI stuff, so Linux can no longer perform *any* CPU scaling.

As of right now, Windows is capable of underclocking the CPU, but not overclocking.  Linux can't do either.  It would probably be possible to make changes to the acpi_cpufreq module to achieve the same functionality as Windows, but this is way out of my abilities.

HP told me that there isn't anything that they can do to fix the problem.  They hope to provide a BIOS update in the future that re-enables TurboBoost and hopefully fixes this problem.  I was told that they can't release such an update until Intel pushes a fix to them... I don't know if they are passing the buck here or not...

Please do post if you find a fix or workaround, but for now I don't think we have any choice but to wait for a future BIOS update.

---

### Post by Wolfgang Eibner on 2012-05-23
Hi!

There is an ACPI patch available which seems to solve the problem:
[http://www.spinics.net/lists/linux-acpi/msg35575.html](http://www.spinics.net/lists/linux-acpi/msg35575.html)

But to use it one must compile an own kernel. I tried it and now cpufreq-info shows frequency information. I'll give it a try and test it for some days.

Yours,
Wolfgang

---

### Post by McGee23 on 2012-08-02
Hi Wolfgang,

you're the man! Unfortunately I almost gave up on that issue accepting the higher cpu frequency and therefore didn't read your post until today.

I compiled my own kernel and now CPU frequency scaling works as it should.

Thanks a lot,
McGee23

---

