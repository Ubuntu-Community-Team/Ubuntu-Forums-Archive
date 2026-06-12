---
title: "USB Gamepad as MIDI controller?!?"
date: 2011-01-06
forum: Hardware
---

### Post by MeGodzillaUDead on 2011-01-06
Hi everyone!  Hope this is the right category, I have a Gravis GamePro USB gamepad that I would like to use as a MIDI controller for triggering drum events in Hydrogen and recording/whatnot in SooperLooper among other things.  I don't think any kind of mouse/keyboard mapping solution will work because I want this one controller to affect different programs without having to manually switch focus; the only way I can see to do this is set the appropriate MIDI bindings in each application.    Where I am right now is: Xorg automagically detects the gamepad and lets me use it to control the mouse but treats it as a three button mouse and not a 10-button MIDI controller =).  I have been told you can use a program called MIDI yoke to do this in Winblowz, but I would much prefer not to have to boot that wretched excuse for an OS.  If I cat /dev/input/js0 to STDIN i get different random characters for each different button press so it seems like the device and kernel are playing nice, but I am totally lost other than that.  If anyone has any suggestions/advice/man pages I can read I would really appreciate it!  Thanks for your time, MeGodzillaUDead

---

