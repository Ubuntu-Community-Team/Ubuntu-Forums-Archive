---
title: "Elitebook lost input focus vs touchpad button"
date: 2011-09-03
forum: Hardware
---

### Post by Blueshell on 2011-09-03
I'm running 10.10 64bit on an HP Elitebook 2530p and have a puzzling problem that I can't find any bug reports about.  This model has a row of lighted touch-sensitive buttons above the keyboard.  If I push the "disable touchpad" button in that row, it disables the touchpad AND my X cursor becomes a hollow rectangle and all keyboard input focus is permanently lost.  if I re-enable the touchpad, I still have no focus.

In addition, left-clicking on Applications, Places, System, or the reboot icon on the right do nothing, but left-clicking on apps stored in that bar launch them.  Right-clicking in that bar also does nothing.

The only way out that I've found is to reboot.

If I turn off the touchpad by saying 'xinput set-prop 11 "Device Enabled" 0', I don't lose focus.  While I could put that in a script and bind it to some other key, I still don't want a situation where an accidental tap in the wrong place on the lighted touch-sensitive buttons means I instantly lose access to the laptop and must reboot, losing any saved editor state, etc.

How can I begin to debug this?

Thanks!

---

### Post by Blueshell on 2011-09-03
Also, as I've just discovered, attempting to suspend hangs instantly with a black screen.  Normally, suspend works just fine.

---

