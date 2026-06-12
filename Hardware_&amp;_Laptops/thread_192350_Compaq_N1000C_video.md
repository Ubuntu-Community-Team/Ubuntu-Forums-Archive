---
title: "Compaq N1000C video?"
date: 2006-06-08
forum: Hardware &amp; Laptops
---

### Post by viking325i on 2006-06-08
Hi,

I've just installed 6.06 on a Evo N1000c laptop which uses a ATI Mobility Radeon 7500, but the desktop isnt filling the display fully? Its leaving about an inch of blank space to the right side, and also not extending all the way to the bottom of the display?

Does anyone know what the fix for this is?

Thanks

---

### Post by Patsoe on 2006-06-08
Sounds like you need to set a higher resolution. From the top menu's, try System > Preferences > Screen Resolution. That should be the easiest way.

---

### Post by viking325i on 2006-06-13
Its not detecting the video correctly, only resolution option is 1280x1024 with a refresh rate of -19569hz.

---

### Post by Patsoe on 2006-06-13
You could try reconfiguring X, by running (from a terminal) "sudo dpkg-reconfigure xserver-xorg", which rewrites the xorg.conf file, asking you for settings while it does so.

You might want to check [https://wiki.ubuntu.com/LaptopTestingTeam/CompaqEvoN1000C](https://wiki.ubuntu.com/LaptopTestingTeam/CompaqEvoN1000C) too, maybe other owners can help...

---

### Post by viking325i on 2006-06-14
[QUOTE=Patsoe]You could try reconfiguring X, by running (from a terminal) "sudo dpkg-reconfigure xserver-xorg", which rewrites the xorg.conf file, asking you for settings while it does so.

You might want to check [https://wiki.ubuntu.com/LaptopTestingTeam/CompaqEvoN1000C](https://wiki.ubuntu.com/LaptopTestingTeam/CompaqEvoN1000C) too, maybe other owners can help...[/QUOTE]

That fixed it :) Thank you

---

