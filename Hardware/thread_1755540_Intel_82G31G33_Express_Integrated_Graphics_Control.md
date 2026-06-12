---
title: "Intel 82G31/G33 Express Integrated Graphics Controller"
date: 2011-05-11
forum: Hardware
---

### Post by PCZahra on 2011-05-11
It worked up to 10.10, doesn't work in 11.04.
There is no Unity on my desktop until this is fixed.
Where once there was wobbly windows and rain effect and desktop cube and all the glitzy special effects, now there is a box that moves.
It tells me I don't have the hardware to run Compiz, but it is the same hardware that was running Compiz before the upgrade.
Warzone 2100 won't open.
Blender won't open.
The screensaver crashes in the config panel, and freezes the entire desktop when it activates or when you lock the screen to switch user.
I'm stuck with Unity 2D, which is clunky itself.

Someone tell me there is a way to fix this.

---

### Post by TheNerdAL on 2011-05-11
Did you install the drivers? 

[http://www.intel.com/support/graphics/sb/cs-010512.htm](http://www.intel.com/support/graphics/sb/cs-010512.htm)

---

### Post by PCZahra on 2011-05-11
I tried. I can't find anything on that site that looks like an installer download. It mentions that [ubuntu] should provide the drivers in its repositories anyway, and those I have installed and uninstalled and reinstalled multiple times with no effect.

---

### Post by PCZahra on 2011-05-14
bump.

---

### Post by PCZahra on 2011-05-19
bump

---

### Post by PCZahra on 2011-05-25
Still no idea what to do...

---

### Post by PCZahra on 2011-06-03
Guys, the driver DOESN'T WORK! The repositories don't have it, PPA version didn't solve the problem, and compiling from source requires packages that are not available. Is ANYONE paying attention here?

---

### Post by PCZahra on 2011-06-07
64-bit live CD works... 32-bit live CD works... think think think DIFFERENCE what is the difference... can you switch an existing install from 32 to 64 without starting fresh? It's definitely a configuration thing, perhaps the packages but which ones...?

---

### Post by PCZahra on 2011-06-07
OK, I removed hal, fglrx, xserver-...-nv, -amd and some other one that isn't showing up on the `dpkg --get-selections` list anymore, as well as a bunch of x11proto-* stuff. The crashing screensavers problem seems to be fixed and I can switch users safely. I still don't have the full graphics capabilities that the CD has, though. Does anyone know where I should look next?

---

