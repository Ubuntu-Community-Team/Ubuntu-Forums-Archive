---
title: "FATAL: Error inserting fan / thermal"
date: 2006-01-28
forum: Installation &amp; Upgrades
---

### Post by wfjm on 2006-01-28
After installing Breezy I get when booting
```
Loading please wait...
FATAL: Error inserting fan: No such device
FATAL: Error inserting thermal: No such device
```
This was observed by others, see
   [http://www.ubuntuforums.org/showthread.php?t=95715](http://www.ubuntuforums.org/showthread.php?t=95715)
   [http://www.ubuntuforums.org/showthread.php?t=106260](http://www.ubuntuforums.org/showthread.php?t=106260)
   [http://www.ubuntuforums.org/showthread.php?t=104489](http://www.ubuntuforums.org/showthread.php?t=104489)
but no resolution was posted to the best of my knowledge.

Does anybody have a hint on how to fix this ?

---

### Post by alloydog on 2006-05-12
I have got back to situation where this happened again - I'm using a remaster of [**_BeatrIX_**](http://www.watsky.net) called [**_BFX_**](http://bea.cabarel.com/) with is a Debain/Ubuntu based distribution.

I just updated the kernel from 2.6.7 to 2.6.12-10-686, from the *Breezy* repository, and again got the messages:
```
FATAL: Error inserting fan (/lib/modules/2.6.12-9-686/kernel/drivers/acpi/battery.ko): No such device
FATAL: Error inserting thermal (/lib/modules/2.6.12-9-686/kernel/drivers/acpi/thermal.ko): No such device 
```

Previously, I found the [**_laptop_**](http://bea.cabarel.com/modules/PunBB/viewtopic.php?id=33) would not boot unless I had the boot options **noacpi** and **acpi=off** in **/boot/grub/menu.lst**.
Searching around this time, I read that the laptop might be trying to run APM and ACPI at the same time, and that you can ensure APM is disabled the same way as done with ACPI.
I changed the boot options to **noapm** and **apm=off**.

The laptop booked OK.  Also, previously the **Battery charge monitor** that comes with **Gnome** did not work - it always gave *N/A* as the state of the battery.  I tried it this time and now it reports the battery status correctly.

---

