---
title: "Evolution: missing icons from toolbar"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by terryscott on 2009-11-08
Hi,

Installed kubuntu 09.10 onto a new partition, leaving my old 09.04 intact.
Used the same /tmp, /home and swap. Needed two attempts before I was able to logon properly. Added evolution from synaptic but missing the icons associated with moving on to next item, send, delete, folders, etc. Added ubuntu-desktop to see if that cured the problem. All ok when using gnome, except i've still got "trash" instead of "deleted items".

---

### Post by gunksta on 2009-11-08
When you are in Kubuntu, I suspect you are using the Oxygen Icon theme. The icons for Evolution may not exist in the theme and the Oxygen icon-set probably doesn't have fall-back icons for these.

Try using the Human theme or another Gnome icon theme in KDE and restarting Evolution. I bet you will find that you have the icons.

As for a more permanent solution, you can try using a Gnome theme, but it may look a little weird in KDE. You could try to figure out what the name of the icons are in Evolution and symlink to them in the Oxygen theme set.

---

### Post by terryscott on 2009-11-10
Hi gunksta,

Thanks for your response. I checked system settings, appearance, icons, the setting was Crystal SVG.
Had a play. Oxygen gave me all except the send/recieve. All showed under the other supplied themes.

---

