---
title: "Ibex loads to blank tan screen after login"
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by Jive Turkey on 2008-12-03
Hardy refused to boot after I added some RAM and a second HDD so I decided to install 8.10.  I installed '/' to a 10GB partition (formatted) and '/home' to my old partition without formatting.  I deleted most of the config files on ~/.* except for .mozilla .thunderbird and .gnome* and some others.  The GDM login screen appears normal but after logging in it shows the mouse pointer on the fleshy-tan colored background.

I tried ctrl+alt+f1 and ran update/upgrade and restarted, same problem still.  When apt-get was running I saw some lines fly by that said something like "unable to load gnome-theme-manager ????????????????????????????????-?????????????????????????????" including the question marks.  It was only visible for a second or two.

I suspect that my old theme stuff is interfering with gnome loading something that works but I'm not sure how best to clear the old junk and leave/rebuild the new.

Thanks in advance for any suggestions.

---

