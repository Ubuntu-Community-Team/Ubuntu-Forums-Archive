---
title: "Permission problems with separate internal hard drive"
date: 2010-08-02
forum: Hardware
---

### Post by kyleabaker on 2010-08-02
I'm trying to configure Firefly Media Server and have all of my media on a separate hard drive from the one that I installed Ubuntu on.

Firefly correctly finds music from my home Music folder:
/home/kyleabaker/Music

..but not from my separate internal hard drive (mounted at):
/media/kyDrive

I've currently configured fstab for this drive as follows:
UUID=35115dc0-34db-4a5d-9e28-1326d4c5a155 /media/kyDrive  ext4    defaults 0 0

Is it possible to make sure that this drive is available to all users? or at the very least, available to me and the user 'mt-daapd'?

I'd like it to work immediately after startup rather than manually configuring anything each time. Any ideas?

---

### Post by ahbart on 2010-08-02
Does firefly search for media files on /media/kyDrive ?
If not, you could try to make a symlink from /media/kyDrive to /home/kyleabaker/Music or to a directory/folder in this music folder.

Otherwise you could chmod/chown the folders on this: /media/kyDrive

---

### Post by kyleabaker on 2010-08-02
Thanks, chmod fixed it. Should have been working, but I guess my previous chmod wasn't properly applied.

---

