---
title: "Restore Usplash after installing Splashy"
date: 2008-08-11
forum: General Help
---

### Post by seshomaru samma on 2008-08-11
I moved my swap partition to another place in the disc, this resulted in no usplash , i searched a bit and found the solution (changing the UUID in fstab) which got me the usplash back .sort of.
What happened is while looking for solutions i tried 'splashy' an alternative usplash manager. it didn't work and i spt-get remove purge it. After changing the UUID i get the splash screen on shutting down but when I boot the usplash start and then i get a console mode saying "reading files needed to boot "
and
"starting boot manager /etc/splashy/rc3....."
or something similar.
so even though i removed splashy it still looks for it. i wonder how to make it stop looking for splashy and look for usplash.

---

### Post by laloruelas on 2009-03-07
i have the same problem :(

---

