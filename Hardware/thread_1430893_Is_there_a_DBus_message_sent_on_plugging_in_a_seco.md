---
title: "Is there a DBus message sent on plugging in a second monitor?"
date: 2010-03-15
forum: Hardware
---

### Post by ekspiulo on 2010-03-15
I've got a Lenovo ThinkPad R61i, and I'd like to write a script to listen to D-Bus for a signal indicating that an additional monitor has been connected to the VGA out, so the script can run xrandr and so forth.

I asked folks in #xorg-devel about D-Bus signals for a connection on the VGA port, and they told me that it probably involves udev and is probably graphics driver specific.  In my case, I'm using an intel integrated graphics chip.  Has anyone else done any video output port interaction over D-Bus?  I'm specifically interested in D-Bus, but if there's another way to fully automate this, I'm still all ears.


Thanks!

---

