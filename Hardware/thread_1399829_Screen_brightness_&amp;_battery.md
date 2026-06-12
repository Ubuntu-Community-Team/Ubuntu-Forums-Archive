---
title: "Screen brightness &amp; battery"
date: 2010-02-06
forum: Hardware
---

### Post by Gailen on 2010-02-06
Hi everybody.

I just reinstalled Ubuntu 9.10 in my Samsung R60 Plus laptop. It's not the first time I've gone thrugh Ubuntu, in fact, I first had Ubuntu 8.04 on that laptop, but then reinstalled Vista and XP so that I could get Wireless conectivity with Eduroam (WPA2-Enterprise). These beginnings were quite hard: wifi not working, Radeon X1250 not working and many other issues.

Well, now everything seems to work OK out of the box (I was surprised the X1250 worked and offered 3D acceleration), but I've found a small issue with the screen brightness:

When I unplug the AC charger, the screen brightness drops to 50%. Manually adjusting it with the Fn keys works, but the problem is that the keyboard freezes: I can't use any key (it simply does not work) except the arrows. The Ubuntu menus (the one that is above, showing the Wireless, clock...) also gets locked and can't be used..... but the Touchpad/Mouse and the applications opened continue working normally. This is the first issue.

So, the Fn keys not being the solution, I tried to modify the ACPI and APM modules, as I saw in the event log how configurations changed. Nothing related with screen brightness on these files.

The I tried configuring the advanced options with  (sudo) **gconf-editor** and then going to "Power". I found there the options related with the screen brightness.

I made the next changes
-Disabled the screen darkening directly
-Changed the battery brightness level from %50 to %100, as on AC.

Well, while the configuration file seems OK, this DOESN'T WORK: when I unplug the AC charger, brightness keeps falling.

Anyone has any idea about this?

Thank you very much

---

