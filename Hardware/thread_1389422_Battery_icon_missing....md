---
title: "Battery icon missing..."
date: 2010-01-24
forum: Hardware
---

### Post by deez on 2010-01-24
I'm running Ubuntu 9.10 64 and my battery icon is not working properly.  The software never recognizes that the battery is discharging, i.e., the computer has been unplugged.  In trying to get an icon to work through Gdesklets, I saw this error. > invalid literal for float(): cat: /proc/acpi/battery/C11F/state: no file or folder of this type   

When looking at my file system, I see that /proc/acpi/battery/C11F does not exist.  Instead it's /proc/acpi/battery/BAT1.  Upon further investigation, I see that the 'state' file within this BAT1 folder does change depending on wheter or not the computer is plugged in.  So it looks to me as if there's a miscommunication problem: perhaps gnome power manager is looking for the battery in a place that doesn't exist?  

I was going to try to change the name using <sudo nautilus>, but the GUI doesn't open the /proc folder.  The cursor changes, makes that little 'processing' circle and that's that.  nothing else.  I've uninstalled and reinstalled gnome-power-manager with no change in status.  I've also tried kpowersave, but that doesn't change anything either.  

Any ideas?  

Cheerios!

Deez

---

### Post by deez on 2010-01-25
Bump...

---

### Post by D3V11 on 2010-01-25
Did you set the power manager to always show in the notification tray? system > preferences > power management. the default, i believe, is set to only show when the battery is charging or discharging.

---

### Post by deez on 2010-01-25
Yeah, I have it to show always.  Right now there is a plug icon b/c it's plugged in, but when I unplug it, it doesn't change at all.  As I said in original post, it seems like it's a miscommunication issue.  I've tried to change the name of the aforementioned folder, but I get an error that says 'no file or folder of this type.'

---

### Post by D3V11 on 2010-01-25
mine does the same thing. it takes it a while for it to update the battery status sometimes. I don't worry about it but i can see where it would be annoying.

---

### Post by deez on 2010-01-25
How long does it take to update the battery status?  Mine doesn't update at all.

---

### Post by deez on 2010-01-25
bump

---

