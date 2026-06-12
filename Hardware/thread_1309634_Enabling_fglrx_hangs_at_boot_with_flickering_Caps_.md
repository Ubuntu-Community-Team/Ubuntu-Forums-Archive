---
title: "Enabling fglrx hangs at boot with flickering Caps Lock"
date: 2009-11-01
forum: Hardware
---

### Post by Lendro_Furioso on 2009-11-01
Ok, finally had time to sit down, do some much-needed file backups, and do a clean install of Karmic. Everything went well (I had a minor hiccup resizing an ntfs partition to give karmic some much-deserved space, but got it done) and in a couple of hours I have everything up and running pretty much...

Then I decided to try the restricted ati drivers. I went the simple way, System>Hardware Drivers and enabled them, then rebooted. All I get when booting is the white ubuntu symbol, then the system becomes completely unresponsive, with Caps Lock flickering on and off.
I booted into safe mode, modified my xorg.conf to load the "radeon" driver, and here I am. Still, it's pretty much a disappointment, and I'm interested enough to try and fix this. Is anyone else having the same problem? Should I be looking at log files to see what went wrong, or maybe try a different xorg.conf file? (mine's very bare). Any help would be greatly appreciated.

---

### Post by Lendro_Furioso on 2009-11-01
No clues? This isn't happening to anyone else? Come on, guys, I'm really just looking for some pointers, a direction to start looking at answers here...

---

