---
title: "Wine + DVD Shrink"
date: 2005-12-04
forum: General Help
---

### Post by Drunken Pirate on 2005-12-04
I am trying to make a backup of my DVD. I apt-get install wine and then installed DVD Shrink. It runs fine, but when I first started it, there were no DVD drives listed. I figured wine didnt install them for me, so I went to ~/.wine/dosdevices/ and did a "ln -s /media/cdrom f:" which is linked to the DVD drive that contains the audio and video _ts files. I restarted DVD Shrink, and it detected my DVD and the title of the DVD that was in there. When I press "Open Disk" then choose the correct drive, and press OK, I get this error: "Failed to initialize ASPI device."

What should I do?

Solved. I ran winecfg, auto detected my drives, and made sure that DVD Shrink.exe ran under "Windows XP"

---

### Post by installer on 2005-12-04
Somewhere in  winecfg you have to tell Wine which drive/s are dvd roms (Auto detect doesn't get it right) Can't remember where though.

---

### Post by teaker1s on 2005-12-04
plus run nt4.0 compatability

---

