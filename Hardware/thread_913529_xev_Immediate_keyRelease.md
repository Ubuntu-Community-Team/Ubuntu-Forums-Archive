---
title: "xev Immediate keyRelease?"
date: 2008-09-07
forum: Hardware
---

### Post by NickLanam on 2008-09-07
Hello, I am new to this forum, and relatively new to Ubuntu.
I decided about a week ago that I needed to upgrade my operating system from Fedora core 8 (I've been using Fedora since 6, so I know my way around well enough). Instead of going to Fedora 9, I decided I'd give Ubuntu 8.04 a spin.

So far, I'm loving it, down to every last detail (and Compiz has had it's share of upgrades, gotta have that.)
Except for one thing:

xmodmap and metacity's keybindings don't play fair anymore, in addition to a problem I've been having with keys emitting release events prematurely.
In Fedora, I could, using xmodmap, bind a keycode to no value, and it still had a keysym that metacity could listen to.

Using this system, I could use my Ideazon MERC's numerical keys on the built-in gamepad as application shortcuts fairly easily, and on-the-fly, have the roman numerals switch to my gaming setup (the numbers behave as WoW bindings in game mode).

Now, if I bind a keycode to nothing, it has no keysym to listen to in metacity (all unbound are treated as 0x0), but if I bind them, then Metacity sees them as something useful and thus doesn't do anything.

The other problem I'm having is a whole lot more annoying: The red keys and multimedia keys emit a keyRelease event at the exact time they emit the keyPress (same timestamp down the the millisecond!).

If anyone knows how to get my poor red keys working again without returning to Fedora, Please speak up and earn my eternal gratitude! (Bonus points for telling me how to get Metacity's keybindings working again, I'm so used to switching bindings on the fly and opening everything from calculator to gconf to Firefox and banshee with those numbers!)

---

### Post by NickLanam on 2008-09-08
Bump.
Please, does anyone know how to make Xev on Ubuntu play as nice as it does on Fedora?

---

### Post by NickLanam on 2008-09-09
I cant seem to keep this on the first three pages!
Bump again :-\"

---

### Post by NickLanam on 2008-09-09
Less than 9 hours before i go to the 4th page, wow.
Bump again as I ponder if I should post this in a less trafficked category

---

