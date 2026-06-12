---
title: "Can't Access home directory"
date: 2008-11-17
forum: General Help
---

### Post by jadymitchell on 2008-11-17
When I try to access my home directory, Ubuntu just hangs and nothing happens.  This is true whether I try to access it from Nautilus, any program, of even from the terminal.

I'm running Hardy with two users.  I notice that the other user has no trouble getting to her home directory.  Any suggestions?

---

### Post by RuleMaker on 2008-11-17
If you are the administrator try this (ar ask administrator):
```
sudo chown <your_username> ~
```

Edit:
or this
```
sudo chown -R <your_username> ~
```

---

### Post by jadymitchell on 2008-11-17
Thanks, but it didn't work.  Just hangs.  

I have noticed that after about 10 minutes it will finally display the contents of the folder.  I don't know what would cause this; the computer is very fast and my home directory is not that large....

---

### Post by cariboo on 2008-11-17
During boot up, does Linux ask you to run fsck on the drive where your home directory is located?

Jim

---

### Post by jadymitchell on 2008-11-17
No, did a reboot and checked the logs and there was no mention of fsck.

---

