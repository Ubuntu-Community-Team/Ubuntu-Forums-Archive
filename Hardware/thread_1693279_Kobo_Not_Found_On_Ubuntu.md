---
title: "Kobo Not Found On Ubuntu"
date: 2011-02-22
forum: Hardware
---

### Post by embryonichappyperson on 2011-02-22
Hi,

I have installed Adobe Digital Editions through wine with no issues but I have another problem. Ubuntu won't recognise my Kobo. It say's connected on the Kobo screen and it shows as being connected on the computer but it's not showing up in Adobe Digital Editions or Calibre!

---

### Post by embryonichappyperson on 2011-02-22
Bump

---

### Post by Levitation on 2011-11-05
Bump

I too am seeking a solution to this issue.

---

### Post by Kantis on 2011-11-27
As I just explained in another thread, I found an answer that works for me. At  [http://appdb.winehq.org/objectManager.php?sClass=version&iId=15545](http://appdb.winehq.org/objectManager.php?sClass=version&iId=15545) the user David Egts writes the following:

"What I do is plug in my nook so Linux mounts it as /media/nook. Then I run winecfg and go to the Devices tab. I'll see drive E: mapped to /media/nook. Then I'll select E: and then Show Advanced and set the Type to Floppy disk and hit Apply and *not* OK. If you do OK, the winecfg window will be dismissed and the settings presumably lost and not written to disk. Hitting Apply will keep the winecfg window in place and the settings presumably in memory. With the winecfg window up with the right setting for E: as a Floppy disk, I then run ADE and the nook will show up every time."

I hope it works for you too! :smile:

---

