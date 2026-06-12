---
title: "[SOLVED] I think my compiz settings are corrupt."
date: 2008-08-24
forum: General Help
---

### Post by JillSwift on 2008-08-24
Window open and close animations (plugin "animations") stopped working on me. I ran compiz from the CLI and I see these messages at window open and close events:
```
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Close event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Open event.
```My filter for general windows in both looks like so:
```
((type=Normal | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver)
```I added " & !(class=Kicker) & !(class=Cairo-dock)" to the end of "Open"'s filters to speed up launching KDE a little.

A second very strange symptom that leads me to think the config files are shot is, new changes don't "stick". In fact, I can change or add a filter, and sometimes get to watch them disappear right from CCSM.

I'm at a loss for where to go from here. Any suggestions?

Pentium D 2.8Ghz
GeForce 7600 GS 256M
Kubuntu 8.04

edit: By the way, the other events for "animations" work: focus, minimize and shade.

---

### Post by JillSwift on 2008-08-25
Never mind. I hit me to save a copy of my compiz profile, de-install (purge) compiz, then re-install it and import the profile.

All's well in compiz-ville.

---

