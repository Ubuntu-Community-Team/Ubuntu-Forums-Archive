---
title: "CD ripping to iso fails"
date: 2008-08-06
forum: General Help
---

### Post by eapache on 2008-08-06
I have been ripping some of my game CDs to iso files as backups (perfectly legal according to fair use blah blah blah).

Most of them rip fine, but a few of them fail after the first MB or so. I assume it's copy protection of some sort. Since what I am doing is not illegal, is there a way to work around this DRM?

I was using brasero, but I ran the same copy with dd to see what it said:```
dd: reading `/dev/cdrom': Input/output error
3552+0 records in
3552+0 records out
1818624 bytes (1.8 MB) copied
```

Any help would be appreciated.

---

### Post by mb_webguy on 2008-08-06
Have you tried using K3B?  I'm not entirely sure it will work any better, but if dd didn't work, that's my best guess until I have a chanve to look into it a bit more...

Try using K3B, and try some combination of the "Clone Copy" copy mode and the "Ignore Read Errors" option in the Advanced tap of the CD Copying window.  I've read that some people have problems with K3B's Clone Copy mode, and also that some CDs use small corrupted areas on the disc to prevent programs from copying them, so you might want to try the "Ignore Read Errors" option first.

---

### Post by eapache on 2008-08-07
dd has an option to ignore read errors (conv=noerror) which doesn't work.

It just spits out the same error over and over until it is killed.

I'll try K3B, but I'm pretty sure it uses the same mechanism.

---

### Post by eapache on 2008-08-12
Anybody else know of a way to do this?

---

### Post by Sebastral on 2008-08-25
Not yet. hope to find a solution for this too..

---

