---
title: "&quot;gnome-power-cmd.sh suspend&quot; as non-root user"
date: 2008-04-28
forum: Hardware
---

### Post by argoo on 2008-04-28
Prior to installing hardy, I would suspend to ram from fluxbox by using the gnome-power-cmd.sh script.  Since installing hardy, I receive a message that the dbus security rules will no longer allow the message to be sent for the org.freedesktop.PowerManagement destination.  If I run the script through sudo/gksu, it works fine.  How do you change the dbus security rules to allow a user to suspend?  

I do not use any display managers like gdm, so X starts under my user account (i.e. non-root).  If I use gdm and X starts as root, I don't have the issue.

I used the policykit editor to grant suspend privs to my account through hal->power-management, but that had no effect.

I was thinking of adding a policy section for my account to /etc/dbus-1/session-local.conf for org.freedesktop.PowerManagement, but I'm not sure if that would be correct route.

Thanks,

---

### Post by argoo on 2008-04-28
Am I supposed to be using the pm-utils scripts instead?!?  I will have to give that a try.

---

### Post by Endolith on 2009-01-07
Did you figure something out?

---

