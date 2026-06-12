---
title: "fsck on next boot"
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by waltervalderrama on 2008-12-29
How can I make fsck scan my drive on next boot. Is there any way to cron it?

---

### Post by prshah on 2008-12-29
> **waltervalderrama said:**
> How can I make fsck scan my drive on next boot. Is there any way to cron it?

You can give this command from the terminal (Applications-Accessories-Terminal)```
sudo touch /forcefsck
``` That will create a "forcefsck" file in your "/" (root); on the next boot, the presence of this file will trigger an fsck.

You can also put that command into a text file, make it executable, and then add the filename as a command in cron; or you can use the tune2fs command to change the interval between forced fscks (usually every 30 mounts)

---

### Post by fie on 2012-08-26
> **prshah said:**
> You can give this command from the terminal (Applications-Accessories-Terminal)```
sudo touch /forcefsck
``` That will create a "forcefsck" file in your "/" (root); on the next boot, the presence of this file will trigger an fsck.

You can also put that command into a text file, make it executable, and then add the filename as a command in cron; or you can use the tune2fs command to change the interval between forced fscks (usually every 30 mounts)

Woah that's wild. Awesome protip, thanks.

---

