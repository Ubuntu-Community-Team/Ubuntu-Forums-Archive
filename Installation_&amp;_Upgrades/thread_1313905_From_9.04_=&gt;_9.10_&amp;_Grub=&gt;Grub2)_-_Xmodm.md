---
title: "From 9.04 =&gt; 9.10 &amp; Grub=&gt;Grub2) - Xmodmap does nothing :/"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by darkcarnival on 2009-11-04
Hey, I've had numerous issues with the upgrade in general, but most has been resolved by now, this, however is *really* getting on my nerves.

I've got a Mac, and as such I've got a different layout than most. Further, I don't use the standard Mac layout but a variant of a normal layout.

```
keycode 108 = Delete
keycode 134 = ISO_Level3_Shift ISO_Next_Group
```

I usually run this via a startup script in gnome or via a terminal like so:
xmodmap .Xmodmap

where .Xmodmap is the file containing the above instructions.

Only in 9.10, Ubuntu/Xorg/Compiz/Whatever has decided to *completely* ignore this.
I've checked with xev, the keycodes still match as they should (doubt they ever could change, anyway), but it won't get me anywhere.

I'm stumped. I wasn't much into the idea of finding the X11 keyboard layouts and changing it directly and the console seems to have one (and ONLY one!) keyboard layout to tinker with so that was a no-go too.

Anyone ? I just want this damned install to accept my xmodmap file! :/

**PS!**
It seems like the changes work under virtual consoles like xterm and gnome-terminal, but anything else just fails

---

### Post by darkcarnival on 2009-11-04
I still don't know exactly why the old stuff no longer works or what I've cooked up but this will work (for me)

```

remove mod4 = Super_R
remove mod5 = ISO_Level3_Shift
keysym Super_R = ISO_Level3_Shift
keycode 108 = Delete

```

Keep in mind, this was with a MBP 5,1 running 9.10 upgraded from 9.04 using the generic 105-key (Intl) PC keyboard model and the layout 'Denmark'.

(Settings checked via gnome's System => Preferences => Keyboard)

---

