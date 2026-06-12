---
title: "Fans go wild after Ubuntu 10.04  Updated itself"
date: 2010-06-05
forum: Hardware
---

### Post by Snapdog on 2010-06-05
Okay so moments ago I was normally working on my ASUS K70I laptop and then I noticed
that Ubuntu wanted to do an update. Something with linux-headers etc. So naturally I let it update itself but right after it did and asked me to restart the fans started going wild.
And Its not just Ubuntu... The fans started going wild right after I start my laptop! Even in the BIOS menu. I tried to load Windows7 too (dual-boot) and the fans go wild there as well.

So I'm completely in the dark here, could somebody shed some light on this case?

Specs:
Intel Pentium        Dual Core T4400  2200 MHz
4GB of DDR3
nVidia GT 320M

---

### Post by BoneKracker on 2010-06-05
Maybe it got hot.

---

### Post by Snapdog on 2010-06-05
It was around 40 ºC ( 104 ºF )

---

### Post by BoneKracker on 2010-06-05
I'd have guess some kind of linux ACPI problem, but it's happening in Windows too.

Mysterious.

Incidentally, when you said, "fans go wild", I thought you were talking about "and the fans go wild" (like when Ozzie Osborne ate a live bat on stage).
```
[B]
Ubuntu updates itself, and the fans go wild!
\o/  \o/  \o/  \o/  \o/  \o/  \o/  \o/  \o/[/B]  <-- fans going wild... "woooooot"
```

---

### Post by Snapdog on 2010-06-05
hahahaha :D! I wish it be like that but no :P

Anyways

My both cores seem to run normally, no over-heating. Both are 34-35 C
The Fan keeps on pushing air out like a maniac after starting up
It was really silent a couple of hours ago.. And the laptop is pretty new too, 
I've had it around two weeks

Any good fan-control/regulation programs available? I read something about eee-control
but i couldn't get the ppa working to download it -.-

---

### Post by BoneKracker on 2010-06-05
> **Snapdog said:**
> hahahaha :D! I wish it be like that but no :P

Anyways

My both cores seem to run normally, no over-heating. Both are 34-35 C
The Fan keeps on pushing air out like a maniac after starting up
It was really silent a couple of hours ago.. And the laptop is pretty new too, 
I've had it around two weeks

Any good fan-control/regulation programs available? I read something about eee-control
but i couldn't get the ppa working to download it -.-

If this is happening in both Linux and Windows, I would first carefully review the hardware documentation and BIOS settings.  Verify that the behavior is actually abnormal, and verify that it is not a result of some change you made outside the operating system level.  For example, if you flashed the BIOS for some ill-advised reason, are you absolutely certain you put the right BIOS on there?  If you "tweaked" BIOS power management, thermal control settings, voltages, or frequencies, did you screw something up?  If you used some kind of overclocking or power/performance tuning utility provided by the manufacturer of the board or the CPU, did you shoot yourself in the foot?

Also, check other forums pertaining to your hardware, and have you reviewed any support information produced by the hardware manufacturers (i.e., the mainboard and laptop manufacturers).  Again -- since this behavior seems to have not been occurring before, but is occurring now in both Linux and Windows, it would seem logical to me that the problem is some kind of change that has occurred outside the operating system.

---

