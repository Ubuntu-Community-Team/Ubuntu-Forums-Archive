---
title: "[SOLVED] Restoring /home partition after reinstall"
date: 2008-09-17
forum: General Help
---

### Post by Inane_Asylum on 2008-09-17
I reinstalled Kubuntu (Hardy), and am trying to get my /home partition recognized.  After installing, I changed /home on my OS partition to home_backup, then added /dev/sda1 /home ext3 nodev,nosuid 0 2 to my /etc/fstab.  After rebooting, it boots to the standard default KDM.  Trying to login gives me something like "could not start kstartupconfig. check your installation." Clicking okay takes me back to KDM.  Am I missing something?:confused:

---

### Post by Inane_Asylum on 2008-09-17
Nevermind...got it.

Forgot to mkdir home after mv home home_backup

All better now :D

---

