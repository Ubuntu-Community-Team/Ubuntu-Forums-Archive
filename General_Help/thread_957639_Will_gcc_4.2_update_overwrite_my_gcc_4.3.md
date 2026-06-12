---
title: "Will gcc 4.2 update overwrite my gcc 4.3 ?"
date: 2008-10-24
forum: General Help
---

### Post by mistermads on 2008-10-24
I am using gcc 4.3 as my default compiler. I compiled/installed it myself without using synaptic. Now, the Update Manager recommends update of gcc 4.2 (a version lower)...  Will those updates overwrite my gcc and take me back to 4.2 ?

---

### Post by geirha on 2008-10-24
It depends on where you installed it. If you installed gcc-4.3 under /usr/local you should be fine. /usr/local/bin is before /usr/bin in $PATH.

This command will show you which binary you'll use when you run gcc
```
which gcc
```

And this will show all binaries named gcc in path
```
type -a gcc
```

---

### Post by Yellow Pasque on 2008-10-24
Do you use the lower version for anything? If not, remove the gcc-4.2 packages.
If you want to keep both, you can control which one is used by changing the /usr/bin/gcc symbolic link. To see what it currently points to:
```
ls -la /usr/bin/gcc
```
If you wanted to change to 4.2:
```
sudo ln -sf /usr/bin/gcc-4.2 /usr/bin/gcc
```

---

