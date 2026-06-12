---
title: "Mounting network drive through fstab as non-root user"
date: 2013-03-21
forum: Hardware
---

### Post by JOZeldenrust on 2013-03-21
Hey everyone,


I've run into a problem that I had before and that got solved, but now the same sollution doesn't seem to be working anymore. See [this thread]("http://ubuntuforums.org/showthread.php?t=1778060").

The relevant lines in /etc/fstab now read:

//192.168.1.102/OpenShare  /media/OpenShare  cifs  username=USER,password=PASS,  0  0
//192.168.1.102/MyShare  /media/MyShare  cifs  username=USER,password=PASS,  0  0

If I add the uid=1000 stuff, attempting to mount again yields a notification that those lines are bad.

Does anyone know how to get this running like it's supposed to again? Any help is greatly appreciated.

---

