---
title: "Can't unmount my CD rom"
date: 2008-08-06
forum: General Help
---

### Post by IronLionZion87 on 2008-08-06
I'm using Wine to install World Of Warcraft.  The install was a success  and now I'm trying to install the expansion.  But when I try to take the disk out I get a msg saying

"You are not privileged to unmount volume 'WoW DVD'"
Details: Only root can unmount /dev/scd0 from /media/cdrom0

Looked around and played witha  few things...can't figure out how to unmount

---

### Post by MyR on 2008-08-06
greetings

have you used wine eject?
wine eject

if that doesn't work you can force an unmount with
umount -f /media/cdrom
or wherever your cd drive is located.

peace

---

