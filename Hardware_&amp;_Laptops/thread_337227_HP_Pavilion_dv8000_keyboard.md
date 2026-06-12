---
title: "HP Pavilion dv8000 keyboard"
date: 2007-01-12
forum: Hardware &amp; Laptops
---

### Post by simonsimon on 2007-01-12
Hello

I have an HP Pavilion dv8000 laptop that works pretty good but I have three problems (on Edgy).

1)  I can't get the calculator key to open a calculator.  If I press it in the keyboard shortcuts it doesn't register.  So in the meantime I use the windows key.  

2)  There is an led at the base of my monitor.  In XP this comes on at startup and stays on.  In Edgy it blinks slowly when I'm connected to a wired lan and it blinks rapidly when I'm connected wirelessly.  This is pretty irritating.  

I've seen some posts about a wireless LED and getting it to work but this isn't a wireless LED.  I just want it to stop blinking.

3)  My mute led does not work.  I've seen some posts about this but none that I can follow to a resolution.

If anyone could help me get started towards a resolution of these problems i would appreciate it.

Thanks.

---

### Post by ghansel on 2007-01-13
I have a dv8000 as well, and similar issues, but I don't think I find them as much of a problem as you do.

The LED at the base of the monitor is indicating status of the wireless connection. When idle (not connected, not searching), it blinks quickly but infrequently. When searching but not connected, it blinks rapidly. When connected, it is solidly lit (as it always is in Windows). I find this indication more useful than its behavior in Windows. If you are not using a wireless connection, and want the LED off completely, press the switch about a quarter inch away from it to entirely disable the wireless. The LED will correspondingly turn off.

My calculator button does work, in Gnome when using Metacity (the default) but not Beryl, which is odd. I don't recall if it initially worked to run the calculator application; I remapped it to open a terminal (which I use more often than the calculator). Go to System/Preferences/Keyboard Shortcuts and "Launch calculator" should be mapped to 0xa1, which (I presume) is the hardware address of the button.

You are correct that the Mute light does not work. The button, however, does. I don't think there is a solution to this (or ever will be, unless a bored developer has a dv8000 and some time) as the hardware address of that light (and the QuickPlay buttons) is most likely specific to this computer and would require reverse-engineering (in Windows) to figure out. 

Good luck,
George

---

### Post by simonsimon on 2007-01-13
I got the calculator to work in Beryl.  In the Config Editor at apps/gnome_settings_daemon/keybindings  there's an entry for the calculator.  If I fix it there rather than at system/preferences/keyboard shortcuts then it works.  It only opens the app.  It doesn't toggle it on and off.

Does anyone have any idea where I can start poking around for the mute led issue?

---

### Post by simonsimon on 2007-01-13
Upgrading my router firmware fixed the blinking wifi led (for some reason).  

I downloaded the upgrade from [http://openwrt.org]("http://openwrt.org") and recommend it to anyone using a compatible router.  My download speeds doubled!  Hurray!

---

### Post by gibuntu on 2008-02-26
If anyone knows how to turn off these lights, that would be great. I use my system a lot and im getting deadspots in my vision from the super bright blue lights, :(

---

