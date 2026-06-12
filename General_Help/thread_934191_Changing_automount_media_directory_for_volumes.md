---
title: "Changing automount /media directory for volumes"
date: 2008-09-30
forum: General Help
---

### Post by scarpasciolta on 2008-09-30
Hi Everybody!
I don't know if this is the right section to ask, if it is not, please address me to the right place.
The question is: 

How can I change the default directory in which every external device such as USB drives and Hard Disks will be mounted?
Now it is "/media" but I need to change it, for instance, to "/Volumes".
I mean WITHOUT symlinks. I'd like to know where this setting is set.

Thanks very much in advance.
Ciao

---

### Post by porchrat on 2008-09-30
looks like this is handled by the udev daemon.  It is governed by a set of rules located here:

/etc/udev/rules.d

I suppose you could create a new rule, but it would be no simple task.

However I don't think you can change the "/media" mount point...only the label of the volume within /media.

---

