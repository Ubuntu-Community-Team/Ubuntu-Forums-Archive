---
title: "How can I uninstall a program I installed using a .deb package?"
date: 2008-10-25
forum: General Help
---

### Post by Moonfrost on 2008-10-25
I installed Wah!Cade, a frontend for the MAME arcade emulator...it turns out it's useless since it doesn't let me setup any video, audio options etc etc...

The thing is I want to know how can I remove it? as I said, I didn't install it through Adept/Sypnaptic, I used a .deb package I downloaded. Is there a way to do this at all? I've been using Linux for a year and half and I stopped installing from .deb or compiling for this same reason, there doesn't seem to be anyway to uninstall programs and I can't believe it hasn't been implemented in Linux yet or at least Ubuntu/Kubuntu alone.

---

### Post by Beth1957 on 2008-10-25
> **Moonfrost said:**
> I installed Wah!Cade, a frontend for the MAME arcade emulator...it turns out it's useless since it doesn't let me setup any video, audio options etc etc...

The thing is I want to know how can I remove it? as I said, I didn't install it through Adept/Sypnaptic, I used a .deb package I downloaded. Is there a way to do this at all? I've been using Linux for a year and half and I stopped installing from .deb or compiling for this same reason, there doesn't seem to be anyway to uninstall programs and I can't believe it hasn't been implemented in Linux yet or at least Ubuntu/Kubuntu alone.

[SIZE="4"][COLOR="DarkSlateBlue"]Does ```
apt-get purge *{name of package}*
``` do anything? I've not tried it on .deb files...[/COLOR][/SIZE]

---

### Post by ciscosurfer on 2008-10-25
```
sudo dpkg -r wahcade
```

---

### Post by berriop on 2008-10-25
try
```
sudo dpkg -r packagename
```
from
[http://ubuntuforums.org/showthread.php?t=269296](http://ubuntuforums.org/showthread.php?t=269296)

or google it, search: ubuntu unistall deb package

---

### Post by geirha on 2008-10-25
You uninstall it the same way you uninstall packages installed from the repositories. Synaptic, apt-get, dpkg ... whichever you prefer.

---

### Post by Moonfrost on 2008-10-25
Okay, I fee embarrassed by not trying sudo apt-get remove before...I have tried it before on other Ubuntu versions and it NEVER worked, and somebody I think it was in this same forum told me that apt-get could only remove packages that were installed using either apt-get, adept or synaptic.

EDIT: I forgot to say that that worked and thanks!

---

