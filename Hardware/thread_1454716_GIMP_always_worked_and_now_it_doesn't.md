---
title: "GIMP always worked and now it doesn't"
date: 2010-04-15
forum: Hardware
---

### Post by pritcharded on 2010-04-15
I use 9.10 and GIMP has always worked flawlessly. Now for some reason GIMP starts to load and then aborts. Synaptic Package Mngr says no packages are broken. I've tried removing and reinstalling all the packages that Synaptic Package Manager identifies as necessary for GIMP but it hasn't solved the problem.

Help required please.

Ted

---

### Post by Yellow Pasque on 2010-04-15
Start GIMP from terminal. Post output..:
```
gimp
```

---

### Post by pritcharded on 2010-04-15
> **Temüjin said:**
> Start GIMP from terminal. Post output..:
```
gimp
```

This is what I get:

ted@ted-desktop:/$ cd /
ted@ted-desktop:/$ usr/bin/gimp-2.6
usr/bin/gimp-2.6: symbol lookup error: usr/bin/gimp-2.6: undefined symbol: gimp_micro_version
ted@ted-desktop:/$ usr/bin/gimp
usr/bin/gimp: symbol lookup error: usr/bin/gimp: undefined symbol: gimp_micro_version
ted@ted-desktop:/$ 

Other applications in the same directory work fine.

Ted

---

### Post by Yellow Pasque on 2010-04-15
The symbol is in the libgimpbase library:
```
$ strings libgimpbase-2.0.so.0 | grep minor
gimp_minor_version
```

Make sure you reinstall libgimp2.0 and have the following (output from lucid, karmic may be slightly different):
```
$ ls -la /usr/lib | grep gimpbase
lrwxrwxrwx   1 root root       26 2010-04-15 18:18 libgimpbase-2.0.so.0 -> libgimpbase-2.0.so.0.600.8
-rw-r--r--   1 root root    97336 2010-02-26 14:15 libgimpbase-2.0.so.0.600.8

```

Also, you may need to run ldconfig after reinstalling the libgimp package:
```
sudo ldconfig
```

If that doesn't work, make sure gimp is linking properly:
```
ldd /usr/bin/gimp-2.6 | grep gimpbase
	libgimpbase-2.0.so.0 => /usr/lib/libgimpbase-2.0.so.0
```

---

### Post by pritcharded on 2010-04-17
Temüjin

Thanks very much. Your solution fixed the problem.

Ted

---

### Post by HunterAtUbuntu on 2010-06-21
I have the same problem but when I check gimp's linking with that command it says /usr/local/lib

If I start gimp with
```
LD_LIBRARY_PATH=/usr/lib  /usr/bin/gimp

```
It starts fine.

How can I permanently change it's library path?

edit:
I just copied all of the libgimp files from /usr/lib to /usr/local/lib and gimp starts now. Is this the right way to fix this or is it going to break on the next upgrade?

---

