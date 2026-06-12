---
title: "Critical Temperature Issue SOLVED Fan on always!"
date: 2005-02-17
forum: Hardware &amp; Laptops
---

### Post by mhancoc7 on 2005-02-17
I finally found a way to force my laptops fan to stay on while running Ubuntu. I tried to use ACPI and APM, but I kept having overheating issues. The solution was to force the fan to stay on by adding noacpi apm=off acpi=off no-hlt to the #kopt line in the /boot/grub/menu.lst file and then do a sudo update-grub. Now the fan runs constantly. The downside is that I lose battery indicator, etc, but at least my laptop is not overheating.

Thanks, Jereme

---

### Post by nocturn on 2005-02-17
[QUOTE=mhancoc7]I finally found a way to force my laptops fan to stay on while running Ubuntu. I tried to use ACPI and APM, but I kept having overheating issues. The solution was to force the fan to stay on by adding noacpi apm=off acpi=off no-hlt to the #kopt line in the /boot/grub/menu.lst file and then do a sudo update-grub. Now the fan runs constantly. The downside is that I lose battery indicator, etc, but at least my laptop is not overheating.

Thanks, Jereme[/QUOTE]

Strange, the FAN is now always on, but your CPU will be much hotter too (try checking with lm-sensors).

Maybe the hotter CPU triggers the FAN to stay on.

---

### Post by mhancoc7 on 2005-02-17
How do I check with lm-sensors? I am a newbie, and am stell learning. 

My laptop does not seem to be running any hotter than before. The only difference seems to be that now the Fan stays on to help cool it down. Before I made the change the fan was not kicking on when the laptop got hot so it would just heat up to the Critical Temp and shutdown.

Is there a problem with forcing the fan to stay on? Will it cause some other issue that I am not aware of?

I would prefer that ACPI or APM would just work and turn the fan on as needed, but I have been unsuccessful so far with that.

Thanks, Jereme

---

### Post by mhancoc7 on 2005-02-17
I have been testing out this approach and have noticed that now that I have acpi and apm turned off the fan is coming on and off as needed. The laptop is staying relatively cool too.

Jereme

---

