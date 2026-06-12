---
title: "unity killed my hard disk?"
date: 2011-06-02
forum: Hardware
---

### Post by ramonf on 2011-06-02
i had this acer laptop for 3 years, running ubuntu since then.
hardware support was incomplete in 8.04 but since 8.10 all worked perfectly.
but in december when i found that unity will be the future and that the netbook edition had it... i give it a try.
i installed ubuntu netbook edition 10.10 in my laptop, everything seemed to work fine but after a couple of days the hard drive was not longer recognized, i had to buy a new one and installed regular 10.10 and all worked fine since then.
until last week, just a week after i installed new 11.04 ubuntu, with unity, my 5 months old hard drive die.
now, i think the unity (or something related to it) killed my last hard disk and my new one, why? well its really strange that both hard disk died just after few days of using ubuntu with unity.
or not?

---

### Post by manfromthezoo on 2011-06-02
It'll be coincidental, buddy.

There's nothing destructive to drive electronics / mechanics / geometry / magnetics in a desktop environment. It's like saying that the block of cheddar cheese in my fridge caused it to rain today. Unrelated. The kernel controls file system I/O anyhow.

Sometimes drives fail; it's an unfortunate tenet of computing and if you feel it didn't have a hard life, it may have had a marginal fault that finally manifested itself in failure.

If you're curious about what caused the failure, it's always worth popping the drive into a computer and running Disk Utility in Ubuntu - you can easily and graphically query the SMART data from there to get an idea (if any faults were detected / logged by SMART).

Another great tool is HDAT2, available all ready to run either separately or as part of the Ultimate Boot CD.

Don't worry yourself about using Unity - as ever, keep backing your data up and you'll be fine in the event of disk failures.

---

### Post by Grenage on 2011-06-02
> **ramonf said:**
> i had this acer laptop for 3 years, running ubuntu since then.
hardware support was incomplete in 8.04 but since 8.10 all worked perfectly.
but in december when i found that unity will be the future and that the netbook edition had it... i give it a try.
i installed ubuntu netbook edition 10.10 in my laptop, everything seemed to work fine but after a couple of days the hard drive was not longer recognized, i had to buy a new one and installed regular 10.10 and all worked fine since then.
until last week, just a week after i installed new 11.04 ubuntu, with unity, my 5 months old hard drive die.
now, i think the unity (or something related to it) killed my last hard disk and my new one, why? well its really strange that both hard disk died just after few days of using ubuntu with unity.
or not?

Humorously enough, one of my hard drives actually caught fire about a week after I installed 11.04.  Coincidences do happen, especially with the components most prone to failure (standard drives).

---

### Post by noeles on 2011-06-14
Hey:
Did you laptop used an nvidia chip?
Cause my hard drive also die when used ubuntu for a couple of days, i think was something with the nouveau drivers, cause i noted the laptop get hotter than usual those days.
My hard drive had like burned paths in the green, some usual silver lines are also like rainbow and dark, can you look at the bottom of your harddrive and tell me if it look the same?
Thx

---

### Post by ramonf on 2011-06-18
> **noeles said:**
> Hey:
Did you laptop used an nvidia chip?
Cause my hard drive also die when used ubuntu for a couple of days, i think was something with the nouveau drivers, cause i noted the laptop get hotter than usual those days.
My hard drive had like burned paths in the green, some usual silver lines are also like rainbow and dark, can you look at the bottom of your harddrive and tell me if it look the same?
Thx

hey,
i look at my hard disk and both are diferent brands and the design is diferent, but in the uncover area of the hard disk (the green part you talk about) i do see some discolored metal lines, i did not notice them.
i take my hard disks to a friends house and he tried, both worked good, too my surprise both were read by an USB/SATA converter by usb, most shocking he conected both directly by sata to his pc, both show up, in fact both be able to boot ubuntu without problems.
i rush to my house and tried in my laptop, same problem,  not recognized, one took a lot of time in the boot hardware screen, the other just wont show up, connected directly in the laptop, even when booting a live cd, they dont show up in gparted, hard disk utility, etc. 
but shocking in live cd with the hard disks in the USB/SATA converter by usb both show in without problems.
now, you talk about nouveau, i in fact always use property drivers as soon as a do a fresh install because the screen resolution otherwise is bad, but with unity screen showed good and i dont installed them, so YES i used nouveau drivers when both hard disks failed.
so now i think maybe unity not killed my harddrives, but nouveau drivers did something to my chipset, the really strange thing is that if nouveau burned something in the hard disks (the discolored paths) by overheating or something, how the hard disk are still usuable in usb and even by SATA in other pc (i cant try the hard disks in other laptop) but in my laptop dont.
i do remember my first disk crash, first one day all of the sudden the laptop shut down (i was watching some videos online) then restart without problems, but since then after several minutes ubuntu became unresponsive windows dissapear, not respond and need reboot (i think in those times the hard disk work for a few minutes and then not) each reboot took more time in the boot check up (i think time after time it become harder to the bios to recognize the hard disk) until one time it simple dont show up anymore.
the second hard disk was more quick, i put an extended job than run for several hours, so i left the laptop on all day, i shut down, the next day trying to boot a few times to fail, some legend that i understand as if the hard disk was suddenly removed, "hda dev disconected" or something like that, then it just not boot anymore.
ANY THOUGTHS?
WHAT DO YOU DO?

---

### Post by walt.smith1960 on 2011-06-18
If the failed drives work and continue to work in another machine, I'd suspect the computer, not the drive.  I've had motherboard SATA controllers become intermittent.

---

