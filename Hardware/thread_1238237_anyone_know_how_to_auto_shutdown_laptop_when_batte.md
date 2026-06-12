---
title: "anyone know how to auto shutdown laptop when battery is at 15% ?"
date: 2009-08-12
forum: Hardware
---

### Post by kraymore on 2009-08-12
anyone know how to auto shutdown laptop when battery is at 15% ?  

i get a warning at 15% but no shutdown.  i hear 15% for a li-on battery is a good cut off point for preserving the life of the battery.  i do not necessarily need a warning, just a shutdown at 15%, simply since i'm usually having a cup of coffee when the battery goes down that much.  anyone know hot to accomplish this ?

thank you

---

### Post by sergiom99 on 2009-08-12
In Kubuntu, you click the battery icon in systray and there you can define what to do.
The only thing is that it measures battery life in minutes and not %.
But you can tell it to shutdown, hibernate, poweroff when it reaches n Minutes left.

Same thing must be available in Gnome.

---

### Post by ddixonr on 2009-08-12
In gnome, under the battery tab in power preferences, the only setting for this is to select shutdown for when "battery is critically low." Not sure how low, but I believe this will do the trick for ya.

---

### Post by harry2006 on 2009-08-14
any conclusive answer on making the system go down once the charge reaches below some X%???

---

### Post by sdennie on 2009-08-14
Hit Alt-F2 and type gconf-editor.  Then navigate to /apps/gnome-power-manager/general and uncheck "use_time_for_policy".  Then, navigate to /apps/gnome-power-manager/thresholds and set the various "percentage_*" values to whatever you like.  After that, the actions set in the gnome-power-manager application should use your percentages rather than its internal "time left" to trigger.

---

### Post by sergiom99 on 2009-08-14
> **sdennie said:**
> Hit Alt-F2 and type gconf-editor.  Then navigate to /apps/gnome-power-manager/general and uncheck "use_time_for_policy".  Then, navigate to /apps/gnome-power-manager/thresholds and set the various "percentage_*" values to whatever you like.  After that, the actions set in the gnome-power-manager application should use your percentages rather than its internal "time left" to trigger.

Un grosso!
:guitar:

---

