---
title: "&quot;Read-only file system&quot; on sd card?"
date: 2008-08-18
forum: General Help
---

### Post by Toadinator on 2008-08-18
I backed up my SD card to my hard drive a while back just in case I needed it for anything, but I don't, so I decided now to copy all of it's old files back, but it's telling me it's "read-only". I tried flipping the switch on the side of it a few times but nothing works... Should I format it or something, and if so, how? Or do I have to mount it with a special command? Thanks in advance!

---

### Post by Toadinator on 2008-08-18
> **Toadinator said:**
> I backed up my SD card to my hard drive a while back just in case I needed it for anything, but I don't, so I decided now to copy all of it's old files back, but it's telling me it's "read-only". I tried flipping the switch on the side of it a few times but nothing works... Should I format it or something, and if so, how? Or do I have to mount it with a special command? Thanks in advance!

bump

---

### Post by dustman on 2008-08-18
well...a format would be nice. Or you could try :
```
chmod 755 /path_to_mount_point
chmod 755 /path_to_mount_point/*
```

About the mounting command, if the card was automatically detected by the system, i think it is mounted with read-write permissions. You could google for "mounting device ubuntu" and it should find you plenty of solutions about how to mount your device with write permissions.

P.S. I'm not sure this will work, but it won't break anything either (you just change the permissions for that folder and all the files in it).

---

