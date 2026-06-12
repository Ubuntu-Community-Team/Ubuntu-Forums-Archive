---
title: "Toshiba Laptop Overheating : Failed to set trip_points for starting fan"
date: 2011-02-06
forum: Hardware
---

### Post by girishadat on 2011-02-06
Hi,

My Toshiba Portege M900 Laptop started showing high temperature again after some upgrades in Kernel.

```
girish@girish-laptop:~$ cat /proc/acpi/thermal_zone/TZ0/*
0 - Active; 1 - Passive
<polling disabled>
state:                   ok
temperature:             96 C
critical (S5):           108 C
passive:                 101 C: tc1=30 tc2=30 tsp=50 devices=CPU0 CPU1 
active[0]:               98 C: devices=FAN0 
active[1]:               90 C: devices=FAN1 
active[2]:               80 C: devices=FAN2 
active[3]:               70 C: devices=FAN3 
active[4]:               60 C: devices=FAN4 
active[5]:               50 C: devices=FAN5
```

I think the removal of support for changing trip_points badly affected my machine. :(
Reference: [https://lwn.net/Articles/244595/]("https://lwn.net/Articles/244595/")
"That capability no longer exists, though; it was removed in the 2.6.22 kernel."

In my case:
```
girish@girish-laptop:~$ uname -a
Linux girish-laptop 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64 GNU/Linux
```

I need some help to set the active[0] to some lower value.

Now my CPU is @ ~96 degrees, as the fan works only @ 98 degrees.

---

### Post by girishadat on 2011-02-06
It looks like some serious discussion is going on @ [http://www.kerneltrap.org/mailarchive/linux-kernel/2007/8/2/154656](http://www.kerneltrap.org/mailarchive/linux-kernel/2007/8/2/154656)

---

### Post by girishadat on 2011-02-06
But wherever the discussion go, they should take some step, to avoid a linux user to say "linux sucks"! ;)

I cannot waste my money and my laptop. Also, I cannot start loving Windows over Linux... :(

---

### Post by tpprynn on 2011-02-06
Different model of Toshiba but maybe there is a shared value in doing what this thread of mine led me to do:

[http://ubuntuforums.org/showthread.php?t=1637561](http://ubuntuforums.org/showthread.php?t=1637561)

That acpi... line really did help with the heat(despite the temporary partial help of compressed air), which went back to 55 degrees on average, when it had hit 98 at times, and this reasonable temperature remained. As far as I understand, it leads the BIOS to control the fan rather than Ubuntu.

---

### Post by girishadat on 2011-02-19
Thank You!

But the options "acpi_osi=Linux" or "acpi=copy_dsdt" didn't work for my Toshiba Portege M900.

What worked for me is "acpi.power_nocheck=1". Now the fan is on for most of the time and it is adjusting the speed (and of-course, noise!) according to the temperature. Now the temperature remains from 45 to 60; usually @ 50 degrees.

---

### Post by girishadat on 2011-08-15
After a few updates nothing seems to work for my Toshiba with Ubuntu 11.04, except a manually initiated sleep and wake up immediately after booting into it, to start the fan working. I think another user (c00lwaterz) with same problem as mine is also doing this technique.

The cause for this issue is to get this corrected in BIOS, in the SSDT. I can see an error in loading SSDT in the dmesg as following.
```
[    0.311181] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.311184] PCI: not using MMCONFIG
[    0.311185] PCI: Using configuration type 1 for base access
[    0.320120] bio: create slab <bio-0> at 0
[    0.321611] ACPI: EC: Look up EC in DSDT
[    0.420144] ACPI Warning: Incorrect checksum in table [OEMB] - 0xC9, should be 0x93 (20110112/tbutils-314)
[    0.420389] ACPI: SSDT 00000000bfda0240 0023D (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.420728] ACPI: Dynamic OEM Table Load:
[    0.420731] ACPI: SSDT           (null) 0023D (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.420851] ACPI: SSDT 00000000bfda0510 00594 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.421177] ACPI: Dynamic OEM Table Load:

```

What I could find as a reason is from this article - [http://lwn.net/Articles/244595/](http://lwn.net/Articles/244595/). Setting the trip points by the user is now removed from the kernel; and it was the only cleaner way to get the fan working, from a user's point of view. :(

Its sad that kernel people are now trying to correct the world, to correct the BIOS/hardware manufacturers, making a lot of victims who cannot live without setting the trip points... Any thoughts?

---

### Post by girishadat on 2011-08-15
Forgot to mention one of the after effects of this sleep and wakeup technique.

After above mentioned wakeup, my lap is unable to detect the power state - I mean, if it is online or on battery. And hence, without any indication, the laptop simply poweroffs immediately once the battery is exhausted, without letting me to save my works / to ask me to connect to charger.

Did anyone face this problem? Any solution or advice?

---

