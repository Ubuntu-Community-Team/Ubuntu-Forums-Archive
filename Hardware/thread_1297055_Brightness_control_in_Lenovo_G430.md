---
title: "Brightness control in Lenovo G430"
date: 2009-10-21
forum: Hardware
---

### Post by jefri_of_azure_sea on 2009-10-21
Dear everyone
I'm using Karmic Beta, and this problem that I got still linger in ubuntu 
I couldn't change the brightness of my laptop
in Intrepid and Jaunty I can use a command to make the brightness control work 
( xrandr --output LVDS --set BACKLIGHT_CONTROL native)
But after I switch to karmiC, I can't use the command anymore

Could anyone give me some solution please?

---

### Post by im2061 on 2009-12-18
I found a solution at [http://ubuntuforums.org/showthread.php?t=1321403](http://ubuntuforums.org/showthread.php?t=1321403) 
   Edit /etc/default/grub as root.
Add 'nomodeset acpi_backlight=vendor' to the GRUB_CMDLINE_LINUX_DEFAULT line.
Lastly, run update-grub as root after saving the file.

---

### Post by jefri_of_azure_sea on 2009-12-20
i dont understand
where i should put that line actually?
sorry I'm a real noobs

---

