---
title: "Loss of keypad functionality (Lucid Lynx 10.04 LTS)"
date: 2011-10-18
forum: Hardware
---

### Post by Master One on 2011-10-18
I recently updated my installation (I am used to use "aptitude update" and "aptitude full-upgrade"), rebooted, and now the keypad on my IBM PS/2 keyboard is not working any more.

I can switch on/off NumLock, the LED shows the chosen status correctly. I always have NumLock enabled, for using the actual number and calculation keys, not the navigation functionality, but it is not working any more.

So NumLock is enabled, the NumLock LED is on, but when I press 2 / 8 / 4 / 6 it moves the mouse pointer instead.

I have no idea, what has gone wrong, I did not change any keyboard settings, which I already checked, and have no influence on that issue.

The NumLock + keypad is working correctly in a virtual console, just not in the graphical environment.

Any clue, how to fix that problem?

---

### Post by Bmonsterboy on 2011-10-18
Hmmm, driver re-install maybe?

---

### Post by Master One on 2011-10-18
Do you mean the keyboard driver? I have no idea, how to check which keyboard driver is in use, and how to reinstall or configure it.

System->Settings->Keyboard->Configuration shows the usual "Generic PC-Keyboard with 105 Keys (Intl)", so nothing that can be done with the keyboard-configuration-GUI.

This issue is totally annoying, because I am so used to use the keypad for entering numbers.

---

### Post by Bmonsterboy on 2011-10-18
Yeah, maybe try googling for the drivers for your keyboard brand and model. Have you tried searching for a fix for your problem on google?

---

### Post by Master One on 2011-10-19
I would not know what to google for, because I did not change anything here on my machine, and it worked as supposed to before. I don't recall any xorg-updates recently, so I have no idea, what exactly is broken now.

The keyboard is still working as usual, just the keypad part (% / x / - / + / , / 0-9) is not although NumLock is activated, the keypad is operating as mouse replacement now.

---

### Post by astef on 2011-10-24
I want to confirm this. Lucid Lynx 10.04 LTS installation, no changes or additional software installed. Num Lock LED is working fine, keyboard is good on another OS. The numeric keypad doesn't work. When I press "5" on the numeric key it has the same functionality as "right-click" or the "menu key", everything else doesn't seem to work.
It must be a bug in one of the updates from what I can tell.

---

### Post by Master One on 2011-10-24
Yes, totally annoying, didn't find a solution for that problem, except to avoid using the keypad, which is totally unacceptable in my line of work.

What do I use a LTS release for, which should stand for its stability, if an unidentified update can break such fundamental functionality, and nobody cares?

That's really frustrating, especially because it was not intended to upgrade to a newer version at that point.

---

### Post by astef on 2011-10-24
Numeric keys work at login (in the username field for example), after Gnome loads the they lose functionality. 
Also everything works as it should if I use **CTRL + SHIFT + NUM LOCK** instead of NUM LOCK to activate the numpad.

---

### Post by Master One on 2011-11-03
This is crazy! In the meantime I did two updates, after the first one (I usually reboot after an update, which I normally only do once in a while, on all other occasions I always hibernate that machine) it worked again, and I thought the problem has been solved! Yesterday I did another reboot after an update, and now it is again not working.

So what is going on here?

---

