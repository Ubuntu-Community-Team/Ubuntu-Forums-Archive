---
title: "GNOME setting? X setting?"
date: 2007-09-13
forum: Hardware &amp; Laptops
---

### Post by threefcata on 2007-09-13
I mapped the right alt key on my X31 using the method mentioned in another post here by changing my xorg.conf, and restart X..

but after I got in X again I got this window prompt me:

The X system keyboard settings differ from your current GNOME keyboard settings.

Expected was model "pc105", layout "us" and option "lv3	lv3:ralt_switch", but the the following settings were found: model "pc105", layout "us" and no options.

Which set would you like to use?

Then there are two buttons "Use X settings" and "Keep GNOME setting"

I tried clicking both of them, both works....

So I'm confused..which one is X setting and which one is GNOME setting?
If two of them work, why is it prompt me?
And that dialog box is badly designed too, I don't even know which is which...

any answers?

thx in advance...

---

### Post by jocko on 2007-09-13
The "X settings" are the ones specified in /etc/X11/xorg.conf.
"Gnome settings" are set through gnome-keyboard-properties (System-->Preferences-->Keyboard).

---

### Post by pikespeakhiker on 2007-10-21
> **jocko said:**
> The "X settings" are the ones specified in /etc/X11/xorg.conf.
"Gnome settings" are set through gnome-keyboard-properties (System-->Preferences-->Keyboard).

Mine are exactly the same in the two sources above, yet I still get this warning dialog.  Both sources list pc105.  But my dialog says expected was "pc101" ...  could this be in yet another config file somewhere?

---

