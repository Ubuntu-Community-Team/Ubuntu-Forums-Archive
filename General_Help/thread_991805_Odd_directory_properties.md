---
title: "Odd directory properties"
date: 2008-11-24
forum: General Help
---

### Post by eludlow on 2008-11-24
I have a directory that I mount a remote file system into, using SSHFS.  I have a script which creates and then removes a directory in the mounted folder every minute so as to hopefully keep the SSH connection alive.

However, randomly the connection still drops out - sometimes it's happened within minutes of the connection being established, other times it can happily stay connected for a few days.

The big problem when this happens is that the directory to which I mount then becomes totally unusable unless I reboot the server.  By unusable, I mean it can't be accessed, changed, removed or anything.

An ls -alh shows the following:

```
d????????? ? ?    ?       ?                ? mount

```

Once I reboot it's fine and ownership is back with me.  Have obviously tried editing / removing it as root, but still no luck.

Any idea what is wrong?

Thanks,
Ed Ludlow

---

### Post by eludlow on 2008-11-24
*Shameless bump* :oops:

---

