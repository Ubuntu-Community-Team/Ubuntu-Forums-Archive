---
title: "mplayer on moxilla firefox"
date: 2006-01-22
forum: Installation &amp; Upgrades
---

### Post by raul99 on 2006-01-22
I am new to Linux and have recently installed ubuntu 5.10. I have been trying to get internet movies to paly on firefox, no luck with Totem so I installed mplayer and installed the firefox plugin. Now when I click on a video I get error: Totem could not Play' fd://0" there was no decoder found to handle the stream. How do I make mpalyer the default video player in firefox?  Thanks

---

### Post by codejunkie on 2006-01-28
[QUOTE=raul99]I am new to Linux and have recently installed ubuntu 5.10. I have been trying to get internet movies to paly on firefox, no luck with Totem so I installed mplayer and installed the firefox plugin. Now when I click on a video I get error: Totem could not Play' fd://0" there was no decoder found to handle the stream. How do I make mpalyer the default video player in firefox?  Thanks[/QUOTE]
press alt+F2 and enter ```
gksudo nautilus
```when it asks for a password enter your password, then navigate to /usr/lib/mozilla-firefox/plugins directory and delete libtotem_mozilla.so, libtotem_mozilla.xpt, and any other file that might have totem in the name.

---

