---
title: "I want 'mv' to update timestamp"
date: 2008-09-26
forum: General Help
---

### Post by sparky-steve on 2008-09-26
Hi....

Pretty much what it says on the tin; For several scripts that I'm running I want the mv command to update the timestamp to the time of the move.

Is this as simple as it should be?

Thanks
SS

---

### Post by kpatz on 2008-09-26
The ctime (inode change time) does get updated on a move.  So if you're running a find or whatever based on the timestamps, just use ctime instead of mtime.

If you want mtime (file modification time) to get updated, do a 'touch' on the file, either before or after moving it.

---

### Post by sparky-steve on 2008-09-26
Ah superb stuff; I looked at manpages for mv, I should have looked at find, as that's one of the commands I'm using.

Will try it now.

Thanks
SS

---

### Post by DrMega on 2008-09-26
I'm not a bash script expert so this is just an idea. Shoot it down at leisure.

What if instead of using mv to move the file, you copy it first (with cp) then delete the original with rm?

---

### Post by ilrudie on 2008-09-26
Just touch the file after moving it.

---

