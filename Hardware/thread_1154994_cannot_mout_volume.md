---
title: "cannot mout volume"
date: 2009-05-10
forum: Hardware
---

### Post by oof on 2009-05-10
Hi,

Ubuntu 8.04 I cannot read an external hard disk (western digital 'My Book' drive), as I get "cannot mount volume" message. A screen-shot with the error message is attached. Mybe you can help

Help is appreciated
Oof

---

### Post by drs305 on 2009-05-10
oof,

Welcome to the ubuntu forums.

Did you try what it said - going back to windows and unmounting it properly?

The force mount option is also available but not preferable.

The third option is to install ntfsprogs:
```

sudo apt-get ntfsprogs

```

Then:
```

sudo ntfsfix /dev/sdXX

```
With XX beging the drive designation  (sdb1, sde2, etc).

---

### Post by oof on 2009-05-11
Thank you drs, I use ubuntu for 2 weeks only, and there are some problems, although ubuntu works very good in general

I unmounted again in windows, and now ubuntu successfully connects to the drive (though trying to unmount it after successful connection makes ubuntu complaining "unable to unmount..").

Addtional problem that I encounter is that hybernation and suspension do not work properly (after recovery from suspension there is an error message, and I can't hybernate at all). This is another story

---

