---
title: "Auto mount network shares"
date: 2008-07-30
forum: General Help
---

### Post by orangey on 2008-07-30
Hi there, 
I'm wondering if there's an easier way to auto mount network shares where the share server isn't always on all the time.

So I know I can add an entry to the fstab to mount on boot.  Or I can do a quick script to "mount -t cifs abc xyz".  But often times the server the shares is on can shutdown in the middle of the day or won't be available when I boot up my machine.

Is there a way to automatically check and mount the share if its there, and umount when its gone?  Or should I just come up with a fancy shell script with pings and mounts that sorta reinvents the wheel?

Ty,
-Dan

---

