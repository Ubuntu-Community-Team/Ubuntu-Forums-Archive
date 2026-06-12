---
title: "deactivate asus ambient light sensor"
date: 2008-01-13
forum: Hardware &amp; Laptops
---

### Post by ermin on 2008-01-13
Is here any1 who knows how to deactivate the ambient light sensor on my asus laptop?
It's just bothersome.

Or how to manually set the brightness? I tried the Fn-keys, /proc/acpi/asus/brn and /proc/acpi/video/VGA/LCDD/brightness, but it didn't work.

Thanks in advance.

---

### Post by Charlie Chuno on 2008-04-29
I found the following commands worked fine on my ASUS M50Sv-A1. Type this into the terminal as you see it here all at once or line by line if your prefer.You must be in sudo to perform the commands, of course.

cd /sys/devices/platform/asus-laptop
chmod 755 ls_level
chmod 755 ls_switch
echo 4 > ls_level



* You can substitute '4' in the last command for numbers 1-15 to adjust brightness.
* 'echo 1 > ls_switch' and 'echo 2 > ls_switch' toggle the light sensor on and off.

The Only problem I'm having is getting it to stay this way after rebooting. A similare fix was applied here ( [http://bbs.archlinux.org/viewtopic.php?id=38935](http://bbs.archlinux.org/viewtopic.php?id=38935) ), but the M50 doesn't have these directories. :/ Ergh

---

### Post by rogosh55 on 2008-05-03
wow. this works perfectly for adjusting the brightness. a little too much work but i guess i will have to settle with this till they fix it properly. thanks for the solution

---

