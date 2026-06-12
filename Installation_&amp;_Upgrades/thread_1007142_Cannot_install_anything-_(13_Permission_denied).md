---
title: "Cannot install anything- (13 Permission denied)"
date: 2008-12-10
forum: Installation &amp; Upgrades
---

### Post by sirdouglas on 2008-12-10
I have been spending the past hours trying to sort through this problem and just cannot find a solution.

My current version of Ubuntu is 8.10 and I just finished installing it (dual-boot XP).  The update manager worked fine getting all the latest updates, but any command in the terminal for me to install something brings an error, for example:

sirdouglas@sirdouglas-laptop:~$ apt-get install vlc
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

... and it's always the same error!  I tried searched the net and tried so many different things that are supposed to fix this.  Shouldn't it be a simple solution?  Instead of wasting more hours getting nowhere, I thought I'd see if the good ol' community has any ideas for me.  So, what can I do?

Thanks!

Doug

---

### Post by lisati on 2008-12-10
Have you closed the update manager?

---

### Post by taurus on 2008-12-10
And don't forget to include the sudo.

```
sudo apt-get update
sudo apt-get install vlc
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by sirdouglas on 2008-12-10
Thank you so much, that was so simple!

Doug

---

### Post by sirdouglas on 2008-12-10
I still get the same error when I don't type "sudo" in front of it, but I can live with that right?

Thanks again,

Doug

---

### Post by dragos_iliescu_2005 on 2008-12-10
There two options:
use of sudo each time you need or
configure you as root privileges - not recommanded -

---

### Post by oldos2er on 2008-12-10
> **sirdouglas said:**
> I still get the same error when I don't type "sudo" in front of it, but I can live with that right?

 That's working as designed.

---

