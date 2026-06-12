---
title: "No Firefox Icon - Kubuntu Jaunty"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by samjh on 2009-05-01
I've just made a switch from ubuntu-desktop to kubuntu-desktop.  The steps I performed are basically:
1. sudo aptitude install kubuntu-desktop
2. sudo apt-get purge (list of ubuntu-desktop packages)
3. sudo aptitude install kubuntu-desktop (to reinstall any Kubuntu stuff that step 2 removed).

That is the correct switch-over method as far as I'm aware.  Never had a problem with it.

But in Kubuntu, I cannot get Firefox's icon to show up.  I've installed Firefox after doing the switch-over by sudo aptitude firefox, which installs firefox-3.0 and firefox-3.0-branding packages.  The menu item exists in Kickoff, but no icon.

Strangely, if I edit the menu, the icon is there.  It's just not showing in Kickoff.  To make matters even more puzzling, I cannot find any Firefox icons in /usr/share directories at all (Firefox is supposed to have an icon in /usr/share/firefox subdirectory, but there is no such subdirectory, and no Firefox icon exists in /usr/share/pixmaps or /usr/share/icons).

Is there a problem with the Firefox package?

---

### Post by aysiu on 2009-05-01
It shows up just fine for me (see attached screenshot). All I did was ```
sudo apt-get update && sudo apt-get install firefox firefox-3.0-branding
``` If you want to try to add the icon in manually, look for it in /usr/lib/firefox-3.0.10/icons/mozicon128.png

If it's not refreshing for you, try pasting these commands in the terminal: ```
killall plasma
plasma &
```

---

