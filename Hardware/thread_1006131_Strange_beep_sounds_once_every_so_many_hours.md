---
title: "Strange beep sounds once every so many hours"
date: 2008-12-09
forum: Hardware
---

### Post by robenroute on 2008-12-09
Hi there people,

I've noticed a rather weird (and slightly distorted) little beep occurring once every so many hours. I'm currently using Intrepid on an HP 6710b, but when using Hardy, the same thing happens. Strangely enough, my initial install of Hardy didn't have this ghostly beep...

any ideas as to what might cause this? It's not a big deal as everything seems to function properly.

TIA,
Rob

P.S. Apart from the initial install (where I had to add VGA=771 to the boot line), everything seems to work rather well with Intrepid on this laptop. I'm kinda chuffed with Intrepid...

---

### Post by sdennie on 2008-12-09
Does the beep sound like a click?  It could be caused by ACPI "errors".  The next time you hear the sound, look at the bottom of /var/log/acpid and /var/log/syslog to see if there is an event corresponding to the click.  If so, and the event is harmless but being caused by ACPI "errors", you can probably disable the sound by going to System->Preferences->Power Management->General and disable "Notify with sound on error" option.

---

### Post by robenroute on 2008-12-12
Vor, thanks for the tips. I've had a look at both files: /var/log/acpid doesn't exist and /var/log/syslog shows no entries at the time of the beeping sound.

I've got the idea it's all pretty harmless, but nonetheless, I wouldn't mind finding out what the sound causes...

---

