---
title: "[Script] Manage Acpi"
date: 2008-07-25
forum: Hardware
---

### Post by Coolaman on 2008-07-25
I made a little script for laptop to manage acpi events because, on my laptop, hal and gnome-power-manager are not working good.

If you want to try it's here : [Script Acpi]("http://coolaman.free.fr/downloads/Script_Acpi.tar.bz2")

 Depends : xscreensaver , kernel's module acpi-cpufreq
 
Default policies :

 - On ac  : Governor cpu ondemand, normal screensaver, disk powermanagemant performance max (if activated).

 - On battery : Governor cpu conservative , cut screen after 5 minutes, disk powermanagement average (if activated )
 	* If battery less than 15%, the governor becomes powersave
 	* extinction after 1200s of inactivity and below 5% battery remaining. 
 	* If vlc or totem running, cut screensaver and governor on demand.
 	* If no battery present, governor cpu on demand

Look at the README file inside the tar.bz2 to install

PS : Sorry for my poor english.

---

