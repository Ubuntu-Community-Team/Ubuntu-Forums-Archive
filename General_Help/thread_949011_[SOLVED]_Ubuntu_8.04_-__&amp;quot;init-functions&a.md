---
title: "[SOLVED] Ubuntu 8.04 -  &amp;quot;init-functions&amp;quot; Problem"
date: 2008-10-15
forum: General Help
---

### Post by johncp1962 on 2008-10-15
I made a copy of my 'init-functions' configuration file before editing it and now I can't boot. I have the option to drop to a root shell, but the system won't let me remove 'init-functions' because it's a system file (I was going to delete it, then rename the saved one). I did not create a bootable floppy either. I know; I'm a bad boy.

Help appreciated.

John

---

### Post by forger on 2008-10-15
Boot from live cd, mount your root partition and do your changes in the mounted partition :)

---

### Post by johncp1962 on 2008-10-15
Thanks forger, I d/l'd the live cd, but found that i could mount from the shell:

root:# mount -o remount,rw /


got my system back up and running...

John

---

