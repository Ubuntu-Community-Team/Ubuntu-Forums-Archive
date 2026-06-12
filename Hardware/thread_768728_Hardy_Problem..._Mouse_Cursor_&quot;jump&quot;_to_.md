---
title: "Hardy Problem... Mouse Cursor &quot;jump&quot; to corner"
date: 2008-04-26
forum: Hardware
---

### Post by csete on 2008-04-26
I'm hoping that someone can help me out with this one.  I just upgraded to Hardy for Gutsy and in general things are looking good.  I'm running on a Dell E1505/6400 and I have one extremely annoying issue with Hardy.  My mouse cursor keeps jumping down to the bottom left hand corner (the hide/show all windows button).  So... I move to click on something and then end up clicking on that button.  It *seems* to happen more often when I quickly move to a position on the screen using the touchpad and then stop.  I can't tell if it jumps right away in the case or when I try to click.  Either way, it is killing me and I don't know how to fix it.

I read somewhere about "evdev" usage, but I don't see that being used in my xorg.conf.  I'm not sure if I'm missing it or if it isn't getting used.  I did have some trouble during my upgrade, so perhaps something didn't get installed quite right.

Please help!
Thanks,
Craig

---

### Post by csete on 2008-04-26
I did a dpkg-reconfigure on the xserver and things seem to have improved.  Hopefully that was all that it takes.

---

