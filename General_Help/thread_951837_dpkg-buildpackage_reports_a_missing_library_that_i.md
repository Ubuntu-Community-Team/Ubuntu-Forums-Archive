---
title: "dpkg-buildpackage reports a missing library that isn't"
date: 2008-10-18
forum: General Help
---

### Post by Perivane on 2008-10-18
Hi everyone,

I'm a seasoned unix admin who's fairly new to Ubuntu (so please be gentle with me!). I'm currently working on a project for a client that's looking to build a debian package and then create a repository for so other users can download and install it. 

The problem I'm having is with dpkg-buildpackage on 32-bit Hardy.. On it's own, the software builds just fine. When I build it with 'dpkg-buildpackage -rfakeroot', I get this error:

```
dh_fixperms
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: symbol ceilf used by debian/osi/bin/libopenjpeg-1.0.0.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol floorf used by debian/osi/bin/libopenjpeg-1.0.0.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol pow used by debian/osi/bin/libopenjpeg-1.0.0.so found in none of the libraries.
dpkg-shlibdeps: warning: debian/osi/bin/libopenjpeg-1.0.0.so shouldn't be linked with libstdc++.so.6 (it uses none of its symbols).
dpkg-shlibdeps: failure: couldn't find library libstdc++.so.6 needed by debian/osi/bin/libopenjpeg-dotnet-2.1.3.0-x86_64.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: command returned error code 512
make: *** [binary-arch] Error 1
```

It looks like it's trying to find libstdc++.so.6, but I already have that in /usr/lib:

```
lrwxrwxrwx 1 root root 18 2008-10-17 05:42 /usr/lib/libstdc++.so.6 -> libstdc++.so.6.0.9
```

I've tried setting LD_LIBRARY_PATH in the program's Makefile, in my shell environment and in the debian/rules file but every single time I get the same error and I'm just about out of ideas.

Does anyone have any suggestions on how I can fix this?

---

