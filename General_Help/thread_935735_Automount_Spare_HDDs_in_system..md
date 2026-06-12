---
title: "Automount Spare HDDs in system."
date: 2008-10-02
forum: General Help
---

### Post by Roasted on 2008-10-02
I have 4 drives in my computer. 1 is used as a local backup, 2 are used as network backups (for other users in the house who back their stuff up to this computer)... and 1 of course I run off of.

How can I set it up so those other 3 HDDs auto-mount when the system boots?

Note - I have a script. But if this can be done automatically, I'd be game.

---

### Post by drs305 on 2008-10-02
The entries would go in fstab to mount all of them on boot. If you don't know how to do this, post the results of these commands:
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
```

Also please indicate the current or desired mountpoints for each drive if you know them.

---

