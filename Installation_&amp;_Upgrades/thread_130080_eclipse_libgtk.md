---
title: "eclipse libgtk"
date: 2006-02-15
forum: Installation &amp; Upgrades
---

### Post by songo on 2006-02-15
hi there..
i've installed eclipse and when i:
```

root@kapverd:~# /opt/eclipse/eclipse
/opt/eclipse/eclipse: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

```

there's no such lib in /usr/lib.

i've tried also:
```

root@kapverd:~# apt-get install libgtk2.0-0
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libgtk2.0-0

```

what should i do? where or how i get this missing package? i need eclipse for yesterday!

---

### Post by songo on 2006-02-16
done
i didn't had the apt setuped.

---

