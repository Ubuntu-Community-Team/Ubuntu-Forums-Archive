---
title: "turn off touchpad on Vaio VPCF116FX"
date: 2012-02-11
forum: Hardware
---

### Post by youWho on 2012-02-11
Just a quick note to say that for me trying to turn off the touchpad while typing using the menu item System->Preferences->Mouse, then the "Touchpad" tab and "Disable touchpad while typing" didn't work. Accidentally touching the touchpad kept moving the curser around frunstratingly whenever I was typing. What did work for me though was to use Applications->System Tools->Configuration Editor (the GUI for gconf-editor, which you might or possibly might not have installed), under "/desktop/gnome/peripherals/touchpad" and to turn off "touchpad_enabled".

This is Ubuntu Natty, 64-bit, on a Vaio VPCF116FX.

Hopefully that helps somebody. Cheers.

---

### Post by youWho on 2012-02-19
huh. An update to say that actually that didn't solve it. And I don't know how to turn off the touchpad when I'm using a mouse. Kind of annoying that it moves the cursor around. I wonder how to do it???

Also I wonder how to remove the "solved" status???

---

