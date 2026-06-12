---
title: "Thinkpad extra battery 27++ discharging to 0%"
date: 2011-03-21
forum: Hardware
---

### Post by jolindbe on 2011-03-21
Hi all,

I've got a Lenovo Thinkpad T410, for which I've recently got an extra 9cell battery, since the battery life on the standard 6cell was hopeless (1.5-2 hours at best in normal usage with WiFi enabled). The battery is called 27++, and you can find an image and some specs here: [http://www-307.ibm.com/pc/support/site.wss/MIGR-74450.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-74450.html)

Anyway, first it was not really possible to see any information about the recently attached battery in Ubuntu at all, but using gnome-power-manager and some settings I finally managed to see them as two separate things, and my new battery started to charge.

The trouble is that Ubuntu does not really seem to realise that it is two separate batteries, since it drains the extra battery to 0% before it starts to use my standard battery at all. This is of course not very healthy for the battery. In the settings for gnome-power-manager in gconf-editor, I've set that it should hibernate when a battery is below 5%, but apparently that goes for the last battery - the first battery will discharge completely without any warnings.

Is it possible to write a script or somehow configure Ubuntu to not use a battery below, say 5%?

---

