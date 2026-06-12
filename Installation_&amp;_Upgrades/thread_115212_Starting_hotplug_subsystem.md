---
title: "Starting hotplug subsystem"
date: 2006-01-10
forum: Installation &amp; Upgrades
---

### Post by asearle on 2006-01-10
I wanted to test Ubuntu on my Asus Z9200va and so tried to boot with the live CD:  It seemed to go through most of the boot process but then hung at 'Starting hotplug subsystem'.

Does anyone have any idea why this should be?  Is there a switch that I could try so that the boot will carry on past this point?

Any tips or pointers to HOWTOs or tutorials on such boot issues would be a great help.  Indeed, I have heard a lot of good things about Ubuntu and am very curious to try it out :-)

Many thanks,
Alan Searle

---

### Post by nijinsky on 2006-01-10
[QUOTE=asearle]I wanted to test Ubuntu on my Asus Z9200va and so tried to boot with the live CD:  It seemed to go through most of the boot process but then hung at 'Starting hotplug subsystem'.

Does anyone have any idea why this should be?  Is there a switch that I could try so that the boot will carry on past this point?

Any tips or pointers to HOWTOs or tutorials on such boot issues would be a great help.  Indeed, I have heard a lot of good things about Ubuntu and am very curious to try it out :-)

Many thanks,
Alan Searle[/QUOTE]

I have the same problem, however, it is caused by the hootplug system not recognising my USB wifi stick.

If I unplug this the bootting restarts.

Try unplugging any attachments (things that a hotplug will detect) and see if you find the offending bit of hardware.

Cheers
Bob

---

### Post by greenway on 2006-01-10
I have had the same problem on several on of our workstations in our offices. On laptops I was usually able to fix it by adding ACPI=off as a kernel option. On desktops I usually switch to antother kernel or reinstall the same kernel image.

---

### Post by asearle on 2006-03-03
Sorry for the delay in responding but my plate has been a bit full. Anyway ...

I have been experimenting and tried starting with acpi=off (to disactivate automatic recognition, I imagine) and the system still hung at the same place.

Does anyone have any other ideas of things that I might/should check.

I really do hope that I can get this working because I believe that a combination of Ubuntu and VMWare would give me the perfect platform for all my needs.

Many thanks,
Alan Searle

---

