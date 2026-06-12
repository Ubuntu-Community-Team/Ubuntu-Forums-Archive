---
title: "Database of installed packages?"
date: 2005-01-20
forum: Installation &amp; Upgrades
---

### Post by TravisNewman on 2005-01-20
So, I may have to reinstall Ubuntu since my latest trouble with kernel panic, and I was wondering if apt keeps a database of installed packages like gentoo's "world file" that can be backed up and restored so there's no need to search for packages for hours. For those not familiar with emerge, basically if you back up  your world file, wipe and reinstall gentoo, and restore the world file, then "emerge world" it reinstalls everything that you had before.

---

### Post by mpie on 2005-01-20
[QUOTE=panickedthumb]So, I may have to reinstall Ubuntu since my latest trouble with kernel panic, and I was wondering if apt keeps a database of installed packages like gentoo's "world file" that can be backed up and restored so there's no need to search for packages for hours. For those not familiar with emerge, basically if you back up  your world file, wipe and reinstall gentoo, and restore the world file, then "emerge world" it reinstalls everything that you had before.[/QUOTE]
 dpkg--set-selections    ....... see the man for exact details, at work the mo not sure of exact usage, believe you can store on a floppy or sepaerate partition and then restore from there.

with dpkg --get-selections      8)

---

