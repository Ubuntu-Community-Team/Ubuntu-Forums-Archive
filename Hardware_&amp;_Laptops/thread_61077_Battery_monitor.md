---
title: "Battery monitor"
date: 2005-08-30
forum: Hardware &amp; Laptops
---

### Post by cbudden on 2005-08-30
hey.  I need help with my battery monitor on my acer travelmate 4501.  The battery icon says that im running on battery power but does not display a time left or anything else.  In windows, it works fine.  Anyone got any ideas?

Thanks

---

### Post by bearbigears on 2005-08-30
on mine i just right clicked the battery monitor, hot properties and it gives you options on how you want you countdown to be. hope this helps

---

### Post by cbudden on 2005-08-30
[QUOTE=bearbigears]on mine i just right clicked the battery monitor, hot properties and it gives you options on how you want you countdown to be. hope this helps[/QUOTE]
 Thanks, tried that.  When i hover over the icon, it says battery status unknown.  The only power management it when my battery light starts flashing!

---

### Post by Panthios on 2005-08-30
I also got a problem with the Battey Monitor.
If I plug the AC power connector, and then, when it is recharged unplugged it again, the icon says "Running on AC power" even though it isnt.

I have to kill Gnome, og remove / add the applet to show it correct battery status.

---

### Post by cbudden on 2005-08-30
[QUOTE=Panthios]I also got a problem with the Battey Monitor.
If I plug the AC power connector, and then, when it is recharged unplugged it again, the icon says "Running on AC power" even though it isnt.

I have to kill Gnome, og remove / add the applet to show it correct battery status.[/QUOTE]
 how do you do that?

---

### Post by Panthios on 2005-08-30
[QUOTE=cbudden]how do you do that?[/QUOTE]

Do what?
Kill Gnome?

Well:

sudo killall gdm
or a "lighter" version that doesn't kill ALL of Gnome:
sudo killall gnome-panel && killall metacity && killall nautilus

Best regards

---

### Post by luca_linux on 2005-08-30
Some Acer laptops have a SmartBattery and need this kernel patch: [http://www.google.it/search?hl=it&q=sbs+linux&btnG=Cerca+con+Google&meta=](http://www.google.it/search?hl=it&q=sbs+linux&btnG=Cerca+con+Google&meta=)

---

### Post by cbudden on 2005-08-30
Thanks again Luca but I get stuck on step four of the readme.  I type iasl -d dsdt.dat after having typed make in the compile folder.  I get the message, iasl command not found.  I have untared both the intel compiler download and the sbs download and copied the contents of the intel compiler download to the sbs folder.

---

