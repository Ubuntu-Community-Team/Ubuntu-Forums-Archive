---
title: "[SOLVED] first time compying problem"
date: 2008-08-04
forum: General Help
---

### Post by l0fls on 2008-08-04
i typed :jimmy@jimmy-laptop:/usr/local/src/airsnort-0.2.7e$ ./configure

terminal said
```
checking for gtk+-2.0 >= 2.0.0... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

```

where did i go wrong...

---

### Post by loboc on 2008-08-04
you need the gtk 2.0 developer library for the compilier to link to

```

sudo apt-get install libgtk2-dev

```

---

### Post by sisco311 on 2008-08-04
try to install the libgtk2.0-dev package:
```
sudo aptitude install libgtk2.0-dev
```

---

### Post by l0fls on 2008-08-04
thanks i got it

---

