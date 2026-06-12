---
title: "screens and graphics preferences (re external lcd projector)"
date: 2008-01-16
forum: Hardware &amp; Laptops
---

### Post by johnwren on 2008-01-16
I cannot get an external lcd projector working on my Dell latitude D531 laptop.  The answer may lie in the System-Administration-Screens and Graphics Preferences menu.  Can anyone point me to documentation on the choices here?  That is, what they really do.  And/or if anyone has information on using an external lcd projector (for a presentation) on the D531, please let me know.
Thanks

---

### Post by johnwren on 2008-01-16
Thanks adept.  The appropriate key combination on the Dell D531 is Fn-F8, marked as CRT/LCD on the keyboard.  This key works as a simple toggle when running off the live install CD, that is, it switches between the laptop screen and the lcd projector, and back again.  There is no option to 'mirror' the laptop screen and have both displays show the same thing, but it would still be workable.

Unfortunately, after you install the system, it doesn't work.   After all updates are loaded and installed, FnF8 has no effect at all.  With the fglx ati driver installed (chipset is azalia) Fn-F8 is similarly unresponsive.  If you do a CTL-ALT-backspace to restart x-server/gnome, both laptop and lcd projector come up with a blank srceen (this is true if you reboot with the lcd projector attached) and the only thing that can get you back (that I have found so far) is to power off and/or use CTL-ALT-DEL.  Sadly, everything works as expected in VISTA.

I will experiment with the analog RGB connector to see if that is a possible solution, but I really would like any suggestions/guidance from the community.  Thinking together is a powerful way to solve problems!  

In general, I'm very happy with the D531.  This is the only major problem I have left.  It will be sad if I can't use the laptop to do presentations under gutsy.

---

### Post by johnwren on 2008-01-16
reply to my own post.  The S-video output works under ubuntu on this D531 laptop, and is one possible wat to connect to an external lcd projector

---

