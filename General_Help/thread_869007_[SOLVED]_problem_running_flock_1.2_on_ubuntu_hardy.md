---
title: "[SOLVED] problem running flock 1.2 on ubuntu hardy :("
date: 2008-07-24
forum: General Help
---

### Post by harrybazeegar on 2008-07-24
Hi...

I am using ubuntu hardy, and I recently downloaded the flock tgz...

when I tried to run it (i gave the command from console) I got a message:

/opt/flock/flock-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

I checked my /usr/lib directory, and sure enough, there was no libstdc++.so.5

BUT, I had a libstdc++.so.6.0.9

so i made a soft link named libstdc++.so.5, pointing to libstdc++.so.6.0.9
and re-run flock, but I just got more errors...

```

/opt/flock/flock-bin: /usr/lib/libstdc++.so.5: version `GLIBCPP_3.2' not found (required by /opt/flock/flock-bin)
/opt/flock/flock-bin: /usr/lib/libstdc++.so.5: version `CXXABI_1.2' not found (required by /opt/flock/flock-bin)
/opt/flock/flock-bin: /usr/lib/libstdc++.so.5: version `GLIBCPP_3.2' not found (required by /opt/flock/libxpcom_core.so)
/opt/flock/flock-bin: /usr/lib/libstdc++.so.5: version `CXXABI_1.2' not found (required by /opt/flock/libxpcom_core.so)
/opt/flock/flock-bin: /usr/lib/libstdc++.so.5: version `GLIBCPP_3.2' not found (required by /opt/flock/libxpcom_compat.so)

```

is there any way I can make the current version of libc++ work?
if not, is there any way to simultaneously have libstdc++ version 6 as well as 5??

Cheers!

---

### Post by harrybazeegar on 2008-07-25
okay, found the solution myself:

```
sudo apt-get install libstdc++5 
```
this did the trick, and flock is now running just fine :)

cheers!

---

