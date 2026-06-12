---
title: "Permissions Problems?"
date: 2008-08-23
forum: General Help
---

### Post by Xpyd3r on 2008-08-23
Okay, so first, could anyone answer me if there is a way to give permission to certain users that they can add and create files, but cannot change or delete current ones?  I figured if I had one folder which gave permission to create, and then have another one with permission to only read, then that would work just as well too, only problem is though, that even using root, trying to change the properties, it wont let me apply anything besides access files, for anyone besides root.  It is a mounted drive if that has anything to do with it.  and it automatically gets mounted through the fstab file.  Anyone have any ideas or help?  Please and Thank you So much!

---

### Post by braddcadd on 2008-08-24
1) Are all the users on the same machine?  If not, are they acessing the folders over a network?

2) Have you tried:
```

sudo chown [uname]
sudo chmod [desirable access code] [files]

```

3) Is the drive external?

4) Are you running from a live CD version of linux?

---

