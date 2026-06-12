---
title: "[SOLVED] dpkg-rebuildpackage?"
date: 2008-08-14
forum: General Help
---

### Post by moore.bryan on 2008-08-14
i'm following [this]("https://bugs.launchpad.net/ubuntu/+source/haxe/+bug/160417") launchpad post to try and get haxe working correctly, but ```
dpkg-rebuildpackage -rfakeroot
``` returns the error "command not found." any ideas?

---

### Post by loell on 2008-08-14
that because there's only

```
dpkg-buildpackage -rfakeroot
```

note, no **re** in buildpackage :)

---

### Post by moore.bryan on 2008-08-14
even though the directions given in the launchpad bug clearly state ```
$ dpkg-rebuildpackage -rfakeroot
```?

---

### Post by loell on 2008-08-14
hmm, i see

could it be a typo?

though its highly unlikely :-k

---

### Post by moore.bryan on 2008-08-14
it must have been because running ```
sudo dpkg-build
``` worked.

thanks!

---

