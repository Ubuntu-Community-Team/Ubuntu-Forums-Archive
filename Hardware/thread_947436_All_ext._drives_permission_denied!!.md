---
title: "All ext. drives permission denied!!"
date: 2008-10-14
forum: Hardware
---

### Post by hananias on 2008-10-14
I don't know what happened, but all of the sudden all the external usb drives I plug into my macbook, I can't copy files...no permission error.  They work fine in OSX partition.  So in OS X I try to change the permission to create and delete, and read/write for user and everyone...but when I boot Ubuntu, I loose all permissions!  I have no idea what's happening.

The craziest thing is...I can upload or copy files/folders from ubuntu into the external drive inside windows via vmware player in LINUX!! but I can't do it in the main System...what in the world???:confused:
Isn't that crazy?  
So as you can see, I need some help

---

### Post by hananias on 2008-10-14
Anybody???

---

### Post by dionp2 on 2009-01-17
Same here,,,,

Help

---

### Post by blackened on 2009-01-17
Have you tried to chown the mountpoint prior to mounting the external drive? That or use a mountpoint in your home folder.

Windows doesn't honor filesystem permissions (a fault, not a feature) the same way Linux and OSX do, so no wonder it works there.

---

### Post by corysarzotti on 2009-01-24
I'm having that problem with my documents folder I copied onto an external drive.  I can't even get into it.  Worse, I need my resume files out of there.  I tried Sudo CD Documents.

---

