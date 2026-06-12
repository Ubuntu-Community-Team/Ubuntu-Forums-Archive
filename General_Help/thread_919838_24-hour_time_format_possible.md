---
title: "24-hour time format possible?"
date: 2008-09-14
forum: General Help
---

### Post by grashdur on 2008-09-14
Is there any way to set my default time format to 24-hour? (For example, I got up today at 9:15, and right now it's 14:10.) I can set it this way for my desktop clock, and for certain individual programs, such as Kontact. But elsewhere, such as in the File Browser and Rhythmbox, I'm stuck with AM/PM. I have a hunch Ubuntu doesn't want me to have this option if I select the United States as my region.

---

### Post by chewearn on 2008-09-14
For nautilus file manager, the date setting format is here:
Menu > Edit > Preferences > Display tab

---

### Post by scebert on 2009-01-09
You can edit your time locale separately from other locales. Alt+F2 and type gksudo gedit /etc/environment and paste this line into the file:
 
LC_TIME="en_DK.UTF-8"   # iso-8601, 24h + weeks start Mon + format yyyy-mm-dd HH:MM

Any program that pays attention to your locale should use 24 hour time and ISO 8601 date format.

---

### Post by grashdur on 2009-01-11
That sounded pretty cool, so I tried it out. But after a couple reboots, I still don't see any difference. I see 24-hour times and ISO format, but only in the programs where I've already changed those settings manually. Elsewhere, like OpenOffice, and the date showing at the right of Gnome's top bar are still the same as before: 11/01/09 in OpenOffice, and "Sun Jan 11" on the top bar.

---

### Post by pabloikba on 2009-09-30
> **grashdur said:**
> That sounded pretty cool, so I tried it out. But after a couple reboots, I still don't see any difference. I see 24-hour times and ISO format, but only in the programs where I've already changed those settings manually. Elsewhere, like OpenOffice, and the date showing at the right of Gnome's top bar are still the same as before: 11/01/09 in OpenOffice, and "Sun Jan 11" on the top bar.

Did anyone ever come with a solution for the 24-hour time format for everythng in Ubuntu Jaunty?

Thanks,

Pablo

---

### Post by chewearn on 2009-10-01
I wrote a blog post about changing date format globally in Ubuntu Intrepid.  I am not sure if the same could be applied in Jaunty, but it's quite possible.

Changing the time format is not specifically shown, but you should be able to figure out how after reading.  Hope it helps.

[http://blog.chewearn.com/2008/11/14/change-date-format-globally-in-ubuntu/](http://blog.chewearn.com/2008/11/14/change-date-format-globally-in-ubuntu/)

---

### Post by pembertonq on 2012-01-04
System Settings> Language Support> Regional settings.

Set to what you want, log out, and log back in again.

---

### Post by grashdur on 2012-01-07
That path still doesn't lead to a place to change the time and date format, only to change the locale--as chewearn pointed out, time and date format are just defaults determined by the locale. The only way to change these things currently is in each individual program or applet (including Nautilus), not system-wide.

---

### Post by howefield on 2012-01-07
Thread closed.

---

