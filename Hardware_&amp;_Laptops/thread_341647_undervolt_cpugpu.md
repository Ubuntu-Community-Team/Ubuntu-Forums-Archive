---
title: "undervolt cpu/gpu"
date: 2007-01-18
forum: Hardware &amp; Laptops
---

### Post by FFfanatic on 2007-01-18
I've searched the forums and googled trying to undervolt my cpu/gpu but nothing quite works. I'm wondering if there is now a linux based program (or one that runs under wine) that will change my cpu/gpu receiving voltages to extend my battery life. I have an AMD Turion64x2 cpu and an ATI Radeon Xpress 1100 recognized as a Radeon Xpress 200M. Also, I'm not able to access any voltage setting from BIOS. Hope that helps.

---

### Post by 23meg on 2007-01-18
> nothing quite worksWhat did you try, and how did it fail? I'm not familiar with undervolting AMD processors but may help if you point to the instructions you followed.
> (or one that runs under wine)
You can't use Windows software to access kernel resources related to the CPU. 

Based on personal experience, I'd advise you to steer clear of undervolting altogether. I burned the motherboard and CPU of a precious laptop when I tried it. It doesn't mean you will as well; actually chances are pretty low that you will, but it can happen. Undervolting is a gray area where there are no guarantees of safety and stability, since you're operating outside the manufacturer's specifications. In my case, things were working nicely with one kernel version, and when I tried the exact same thing with another, following the instructions to the letter, I damaged the computer.

---

### Post by Johan! on 2007-01-18
dmesg|grep powernow : 
```
[17179653.936000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.60.2)
[17179653.936000] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x6 (1400 mV)
[17179653.936000] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x8 (1350 mV)
[17179653.936000] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xa (1300 mV)
[17179653.936000] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12 (1100 mV)
```

Cool & Quiet works out of the box.:) 

I don't know if it's possible to undervolt in Linux.
You could try to change the voltage settings in the BIOS. (DANGEROUS)

---

### Post by 23meg on 2007-01-18
> I don't know if it's possible to undervolt in Linux.With Linux PHC it's possible with Pentium M series; I don't know about the rest.

---

### Post by Johan! on 2007-01-18
[http://wejp.k.vu/projects/howto_cnq_athlon_64_x2/](http://wejp.k.vu/projects/howto_cnq_athlon_64_x2/)

This could work, but you'll have to build your own kernel.:-k

---

### Post by FFfanatic on 2007-01-20
Too complicated for me, I'll just see if my processor supports ACPI so I can try to use athcool from synaptic.

---

### Post by mcduck on 2007-01-20
> **FFfanatic said:**
> Too complicated for me, I'll just see if my processor supports ACPI so I can try to use athcool from synaptic.

Athcool doesn't need ACPI as far as I know. The way it works is that every CPU cycle when there's nothing to do it sends your CPU instruction to turn itself off (just like cpuidle does in windows). I'm not sure if athcool works with other CPU's than Athlons though, but I suppose it doesn't hurt to try.

---

### Post by FFfanatic on 2007-01-20
Athcool does require ACPI support, and if you don't have it, bad things can happen:

tool to enable powersaving mode for Athlon/Duron processors
athcool is a small utility for enabling/disabling Powersaving mode
for AMD Athlon/Duron processors.

By enabling Powersaving mode you can lower power consumption and
CPU temperature when the CPU is idle.

Powersaving works only if your kernel supports ACPI (APM does not
work), because athcool does only (un)set the "Disconnect enable when
STPGNT detected" bits in the Chipset's Northbridge. To really save
power, the STPGNT signal has to be sent when the CPU is idling. This
is done by the ACPI subsystem when C2 state entered.

!!!WARNING!!!
Depending on your motherboard and/or hardware components, enabling
Athlon powersaving mode sometimes causes:

 * noisy or distorted sound playback,
 * a slowdown in harddisk performance,
 * system locks or instability,
 * massive corruption of the filesystem (observed at least once).

If you met those problems, you should not use athcool. Please use
athcool AT YOUR OWN RISK.

If athcool works fine for you, and you want it to run automatically
on startup, please read the /usr/share/doc/athcool/README.Debian
file.

So... I need to know how to find if my stuff supports ACPI.

---

