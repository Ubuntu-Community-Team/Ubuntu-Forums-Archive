---
title: "touchpad settings reset after poweroff"
date: 2010-04-23
forum: Hardware
---

### Post by bboyreason on 2010-04-23
i have an eee pc w/ 1.6 intel blah blah blah i dont think it will matter as this is pretty noobish;
i googled "touchpad settings reset ubuntu" and various other forms of the same idea to no avail;
i just want to turn of the d5mn tapping=clicking "function" as i am tired of lightly brushing the touchpad and clicking something disastrous;
i am using 10.4;
is there a configuration file i can just permanently change? or some kind of file i really dont know

edit:
just to be clear, i can change the touchpad settings with "touchpad" but they change back to default after poweroff

re-edit: i read something that says i need to put gsynaptics-init in my startup apps, so i hit "add" under startup apps and i get 3 fields:
1) name
2) command
3) description
- i just put "gsynaptics-init" in both name and command and left description blank, but no worky :(
any ideas?

---

### Post by pi/roman on 2010-04-24
alt/f2
type "gconf-editor" enter
in the configuration editor window open "desktop" -> "gnome" -> "peripherals" -> "touchpad"
uncheck the box next to "tap_to_click"

---

### Post by bboyreason on 2010-04-24
amazing, thx so much;
learned another shortcut as well, didnt know about altf2 to run;
and i hadnt found the gtk conf editor yet either, or knew it existed really;
that might solve some other problems i had;
after using only windoze since i was little, computers never really interested me all that much because of the price barriers in place;
ubuntu is like a fresh install for my attitude towards software distribution practices;

---

### Post by bboyreason on 2010-04-24
actually they reset again;
i will try it again and see if i missed some option to "save" or something

edit:
weirdness;
i right clicked the setting in gconfeditor and set the unchecked "tap to click" to a default setting, this was the closest i saw to "save"
when i restarted the system, at the login screen the "tap to click" still was on, but after login, it was off;
i guess because i havent chosen to start a gtk session and i was editing my gtk settings to change the touchpad settings;
so i guess this is solved, but i am not sure;
it seems so to me because i assume the 'tap to click' is just like a button on a regular mouse that will be detected by the OS during boot and could be changed for each OS after the fact, but will always be detected by a fresh install under any modern OS;
am i correct in these assumptions?

---

