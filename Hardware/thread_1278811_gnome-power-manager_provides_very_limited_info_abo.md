---
title: "gnome-power-manager provides very limited info about battery"
date: 2009-09-30
forum: Hardware
---

### Post by michael37 on 2009-09-30
For some reason, one of my laptops running Jaunty developed a strange behavior.  Normally, gnome-power-manager applet displays the battery status with an option to get extended information if users clicks on the battery icon.

On this particular laptop, the battery icon is correctly displayed (incl when charging/discharging/fully charged).  When I click on the icon, the status is just limited to "Laptop battery: charging" or "Laptop battery: low".  Clicking on that status displays nothing -- usually that's where I get a window with detailed information about the battery.

The text information in /proc/acpi/battery looks normal, but AFAIK gnome-power-manager doesn't use acpi (not 100% sure about that).

---

### Post by X1R1 on 2009-09-30
Indeed, it does provide very limited info, I cant adjust the brightness of the screen to display differently when connected/battery. It will be a really nice addition that you could be able to create battery profile plans, cause I hate to say it, but on vista my laptop battery runs for about 8 hours, and on ubuntu its somewhere around 5 or less, pretty big difference if you ask me. that 3 hour difference its because of battery plans, and the gnome power manager doesnt do that....

---

### Post by michael37 on 2009-09-30
> **X1R1 said:**
> Indeed, it does provide very limited info, I cant adjust the brightness of the screen to display differently when connected/battery. It will be a really nice addition that you could be able to create battery profile plans, cause I hate to say it, but on vista my laptop battery runs for about 8 hours, and on ubuntu its somewhere around 5 or less, pretty big difference if you ask me. that 3 hour difference its because of battery plans, and the gnome power manager doesnt do that....

Hmm. I might be able to help you with the latter.  Click on the toolbar and select "Add to Panel".  Select "CPU Frequency Scaling Monitor".  Left-click on it and you'll see 4 available profiles to choose.

---

### Post by X1R1 on 2009-09-30
> **michael37 said:**
> Hmm. I might be able to help you with the latter.  Click on the toolbar and select "Add to Panel".  Select "CPU Frequency Scaling Monitor".  Left-click on it and you'll see 4 available profiles to choose.

wow.....I completely missed that...I already had the cpu on the panel but completely forgot of that option lol.....thanks for the tip.

---

### Post by mechanic on 2009-10-24
What is the best applet to install for better info about the battery condition? ibam? batmon.app?

---

### Post by michael37 on 2009-10-24
> **mechanic said:**
> What is the best applet to install for better info about the battery condition? ibam? batmon.app?

I have no idea.  I am talking about the applet that is managed by gnome-power-manager.  You should have its icon in the notification area.

---

