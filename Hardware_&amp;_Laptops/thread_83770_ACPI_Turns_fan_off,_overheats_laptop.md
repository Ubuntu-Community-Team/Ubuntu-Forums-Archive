---
title: "ACPI Turns fan off, overheats laptop"
date: 2005-10-29
forum: Hardware &amp; Laptops
---

### Post by res_overlord on 2005-10-29
I am currently running Ubuntu 5.10 on an HP TC4200 Tablet.  When I power on the computer and it is running on AC power, Ubuntu hangs during boot.  It also turns the processor fan off, which causes the laptop to overheat.  When the laptop is not connected to the wall, the fans work fine and the boot does not hang.  

I have verified that this is an ACPI problem by booting on AC power with the boot parameter 'acpi=off'.  The system then boots fine but, of course, no longer has ACPI enabled.

ACPI also deactivates the fan whenever the laptop has already booted and I plug in the AC power cord.  This causes overheat after a short period of time.

The only possible reason for this behavior that I can think of is a bios setting that forces the system fan on whenever AC power is connected.  I currently have this setting disabled.  

Any help with this problem would be much appreciated.

Regards, 

Joseph

---

### Post by dangerjunkie2002 on 2005-10-30
Hi there,

Sounds like we both have the same problem [http://ubuntuforums.org/showthread.php?t=83682](http://ubuntuforums.org/showthread.php?t=83682) . You are right. If ACPI isn't enabled the fan works fine under BIOS control but as soon as ACPI kicks in the fan is disabled.

If you look in the /proc/acpi/fan directory does it contain a reference to FAN or is it empty (couldn't detect fan) like mine? Does your /proc/acpi/thermal_zone/THRM/cooling_mode say passive and that it can't be changed like mine?

Just out of interest did you do a clean install of Breezy or did you do an upgrade from Hoary or Warty? I did an upgrade from Hoary and I'm starting to wonder if I have an upgrade-related problem.

All the best,
Paul.

---

### Post by res_overlord on 2005-10-31
To answer your questions: 
 1-I did a clean install of Breezy
 2-The fans are being detected
 3-I can modify the thermal points

The thing that is completely odd about this is the fact that ACPI words **perfectly fine** when I am on battery power.  When on AC...

I found a solution to my problem: Enable the bios setting that forces the fan on when on AC power.  This means that ACPI works normally when I am not on AC power and the fan is forced on when I am on AC power (not that I care, it is a quiet fan).

I would prefer, however, to be able to run on AC power with normal fan operation...

---

### Post by mapapo on 2005-11-01
Same here with a HP NC4200. Works like charme on battery. But on AC the fan seems disabled and booting takes much longer than on battery (seems that the processor steps down because of getting overheated). Turning on the fan in the Bios enables booting with AC, but it still takes much longer than with battery.

Im not very experienced in Linux so I avoid experiments but from my experience it hast to be just a switch or setting because the NC4200 works that well wih battery.

Any help would be great

---

### Post by siennalizard on 2005-12-29
Just a me-too, I'm afraid. I have the same problem, but the laptop runs ok at about 65-70 deg. C, which in my view is far too high. The only way I could get the system to use ACPI was to recompile my kernel without the thermal.ko module. Bizarrely, all the thermal data is available to the system (I'm looking at it now), but the fan directory is empty, although the module is loaded (and I've tried reloading it.

I've got a Phoenix BIOS which is rather sparse and doesn't have options to control any power management, fustratingly...

Oh, and this is almost amusing considering that the laptop has no way to actively cool itself:
```

root@garnet:/home/james# cat /proc/acpi/thermal_zone/THRM/cooling_mode
cooling mode:   active

```

Cheers,
J.

---

### Post by condorloco on 2006-04-28
Does anybody know if this behavior does still exist in 6.06? I had to switch back to Windows after using Ubuntu for 6 month when I bought this laptop and I'm eager to switch back.

---

### Post by parkan on 2007-01-28
i had the same problem on 6.10, problem still not solved it seems
on hoary though it worked fine

---

