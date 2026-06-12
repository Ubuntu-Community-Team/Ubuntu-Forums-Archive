---
title: "[SOLVED] CCSM error"
date: 2008-08-07
forum: General Help
---

### Post by SteveNorman on 2008-08-07
I had compiz running fine, then I tried to run a script to get the cube into a cylinder. Now my compiz is hosed. I tried removing , purging, all sorts of stuff but I cant get my ccsm to work, and I cant get the advanced desktop effects menu option back. Here is the output of "ccsm"
```
desktop:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 38, in <module>
    import compizconfig
ImportError: libcompizconfig.so.0: cannot open shared object file: No such file or directory

```

---

### Post by tuxxy on 2008-08-07
[This]("http://forum.compiz-fusion.org/showthread.php?t=5828") post maybe useful

---

### Post by SteveNorman on 2008-08-07
```
Add /usr/local/lib to /etc/ld.so.conf 
```

not sure how i would do that,,,,
```
-desktop:/usr/local/lib$ sudo cp libcompizconfig* /usr/lib/
[sudo] password for steve: 
cp: cannot stat `libcompizconfig*': No such file or directory

```

is the result of my attempt to copy the next post there.

I am sure I am missing something obvious here,,

---

### Post by sayakb on 2008-08-07
Install Compiz 0.7.6: [http://ubuntuforums.org/showpost.php?p=5335372&postcount=24](http://ubuntuforums.org/showpost.php?p=5335372&postcount=24)
This version includes cube deformation (cylinder and sphere) by default.

---

### Post by SteveNorman on 2008-08-09
I have tried uninstalling and reinstalling, something related to ccsm is stopping me from successfully doing any desktop effects.

---

### Post by SteveNorman on 2008-08-28
after an extensive search and destroy mission for every file related even remotely to compiz I finaly was able to reload and run it. the icons in ccsm are greyed out, but the cube spins,,,happy happy!

---

