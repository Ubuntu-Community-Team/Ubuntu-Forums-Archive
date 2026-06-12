---
title: "cannot deactivate power management?"
date: 2006-06-27
forum: Hardware &amp; Laptops
---

### Post by Prinz Igor on 2006-06-27
hello community :)

i have a problem with my 4 1/2 years old notebook. it is a toshiba satellite 2800-100.

well .. i am not sure if it is a special laptop issue.

i want to deactivate any action like screensaver or power management when i close the lid or just let the laptop alone for a while. so i have deactivated all actions and i have deactivated the screensaver.

although the screen is getting white or more precisely: sometimes it is white completely, sometimes it looks like a broken tv screen and sometimes it is white with grey horizontal bands.

when i then use any key it is gone - like a screensaver.

how can i fix this? i just wanna happen nothing(!) when i leave my laptop alone.

regards,

prinz igor

---

### Post by Teleyinex on 2006-06-28
When you close the lid, the ACPI support will get the event and then execute some commands. Probably there is the actions that you have to modify. The files are in: /etc/acpi/lid.sh

Cya!

---

### Post by Prinz Igor on 2006-06-28
thank you for the hint. i have now uncommented the "action line" in /etc/acpi/events/lidbtn. now all actions are deactivated when i close my lid.

but when i leave my laptop alone for a while (with an open lid) the problem is just there. i now know that this is the command that must be executed to reproduce the phenomenon:

xset dpms force off

is there any script which is executed when i leave my laptop alone for a while?

---

