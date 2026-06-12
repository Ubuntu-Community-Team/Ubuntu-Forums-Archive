---
title: "Display brightens when it should dim (on battery power)"
date: 2008-04-12
forum: Hardware &amp; Laptops
---

### Post by vladk2k on 2008-04-12
I've searched the forum and couldn't find anyone with a problem similar to mine

I have a Fujitsu Siemens Esprimo mobile V5545 notebook. It has an ATI Mobility Radeon HD2400 graphics chip (I don't think anything else is worth mentioning)

Ubuntu Gutsy running, with the appropriate graphics driver (so that the resolution is 1280x800, hardware acceleration) everything runs smooth. Except the dimming when inactive feature (which is enabled by default) and brightness in general.

When on AC power, The slider in Power Management Prefernces works very well between 25 - 100 %)
Below 25%, it is full brightness, which is odd.

when on battery power, the slider reverses. 0% is full brightness, and increasing the slider to about 75% actually darkens the screen. Between 75 and 100% the screen is full lit.

Because of this, when dimming, the display actually gets brighter, and when touching it it darkens to whatever the precentage was set.

Do you have any idea why this happens, and what can be done about it?

---

### Post by shearn89 on 2008-04-26
*bump* - i can't even find the slider. How do you get to the power management prefs? If i right click on the tray icon, no brightness slider is available.

---

### Post by shearn89 on 2008-04-29
Just to let vlad know - i found it. You have to use gconf-editor, but i can't remember which bit. There's a power settings page, and one of those values works.

---

### Post by bindatype on 2008-04-29
By the way, make sure that your hardware brightness setting is set to 100%. Its usually a Fn+(some key). I adjusted mine and now it works as expected. 

The absent slider thing (which was present for <=7.10) is a pain--requiring the user to open gconf-editor is awkward. Isn't there another way?

[COLOR="Silver"]
I am using hardy and have the same problem.

Accessing the brightness level through the gnome-power-manager (a la gconf-editor) does provide a method for changing the brightness for AC/Battery states. However, the interface appears to be flaky. Changing the settings doesn't have any effect on the screen brightness. 

I previously ran gutsy on this machine and the dimming feature worked flawlessly. This version of hardy is a fresh install--I didn't do a direct upgrade.[/COLOR]

---

### Post by shearn89 on 2008-04-29
I found i had to reboot to get gconf to pick up the brightness setting properly. Probs a nicer way, but it was quicker just to reboot. AFAIK, there's no other way to set it atm. I'm not sure why they took it out - its a pretty essential feature of power management for laptops...

---

