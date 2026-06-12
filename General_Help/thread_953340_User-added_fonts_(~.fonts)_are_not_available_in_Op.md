---
title: "User-added fonts (~/.fonts) are not available in OpenOffice and some other apps"
date: 2008-10-20
forum: General Help
---

### Post by MikeTheC on 2008-10-20
Hey Folks!

Having exhausted what resources there are, both here on UbuntuForums as well as other tech articles and Linux-related sites, I've decided to throw my hands in the air and ask for help.

**Problem:**

I have a number of self-installed fonts which some applications (such as Scribus, Gimp, Inkscape, Firefox, etc.) *do* see, and which others (OpenOffice, AbiWord, etc.) *do not* see. These fonts are all OpenType fonts, and are exclusively located in [font="Courier New"]~/.fonts[/font]. Now, it's worth noting that I *do have* the MS TT Core Fonts package installed via "[font="Courier New"]Add/Remove...[/font]" and *every* capable-of-using-fonts program has no problems recognizing *them*.


**My Configuration:**

[list][*] Ubuntu 8.04 for i386, all system and software up-to-date;
[*] OpenOffice 2.4.1 and AbiWord 2.4.6
[*] Everything else on the system seems to be behaving normally[/list]


**What I've *Already* Tried:**

[list=1][*] Refreshing font cache via [font="Courier New"]sudo fc-cache -f -v[/font] (completes successfully, no errors)
[*] Editing [font="Courier New"]local.conf[/font] (cannot do this because: 1. No such file exists anywhere on my system, and 2. No documented procedure *anywhere*, no matter how religiously followed, ultimately generates this file)
[*] Installing the [font="Courier New"]gsfonts-x11[/font] package (completes successfully, no errors)
[*] Redoing the fontconfig configuration via [font="Courier New"]sudo dpkg-reconfigure fontconfig-config[/font] (completes successfully, no errors)[/list]


I really have no clear idea what a "next step" would be or entail, and so I'm hoping one of you kind folks can help me to unravel the mystery.

Thanks in advance!


Mike

---

### Post by tonybaqain on 2008-10-20
try adding them into ** /usr/share/fonts/ **.

have fun :)

---

### Post by PsychedelicReaction on 2008-10-20
i think i also have the same problem with OO. And it doesn't happen with all the fonts in .fonts directory, but just with a bunch of them. I tried Abiword too and i can confirm they also don't work. I tried moving the fonts to /usr/share/fonts but nothing has changed.

---

### Post by hugmenot on 2008-10-20
Surprise, OpenOffice does not support OpenType fonts.

---

### Post by aspora.isernia on 2009-01-21
> **hugmenot said:**
> Surprise, OpenOffice does not support OpenType fonts.
So, there is a limit to the "openness" of OpenOffice? :D

---

