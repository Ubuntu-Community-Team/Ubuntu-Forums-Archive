---
title: "tracing volume keybindings"
date: 2006-01-09
forum: Hardware &amp; Laptops
---

### Post by pgf on 2006-01-09
i'm trying to figure out how the volumeup and volumedown buttons work.  i'm running breezy.

when i push one of these "special" keys on my asus z33, the corresponding script under /etc/acpi gets run.  that script, in turn, calls "acpi_fakekey" to inject the proper keycode into the system.

the next step, as i understand it, is handled by the mapping that i see in the gnome "keyboard shortcuts" applet, available under System-->Preferences.  there, i see that those two up and down keycodes (0xb0 and the other one i forget) are bound to volume up and volume down actions.

but then, the trail goes cold.  :-)

when i use one of those keys, i get a small popup in the center of the screen showing a slider that moves as i repeatedly hit one key or the other.  (or mute.  i haven't mentioned mute, but it's one of the set.)   where does that little popup come
from?  where is the actual commandline that represents what gnome is doing when that popup runs?

paul

---

