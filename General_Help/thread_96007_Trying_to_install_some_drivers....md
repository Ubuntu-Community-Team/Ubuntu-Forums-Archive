---
title: "Trying to install some drivers..."
date: 2005-11-27
forum: General Help
---

### Post by schizoid_embolism on 2005-11-27
Hi all,

I'm trying to install these drivers: [http://www.tanzband-scream.at/line6/binaries.html](http://www.tanzband-scream.at/line6/binaries.html)

When I use alien to convert the .rpm to a .deb, I get this error message:

> Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
        xargs -0 -r -i cp -a {} debian/podxtpro
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dh_gencontrol
dpkg-gencontrol: error: current build architecture i386 does not appear in package's list (amd64)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: podxtpro-0.5.2: No such file or directory


I have an AMD64 processor and I'm using the x86 version of Ubuntu.

Any suggestions?

Jeremy

---

### Post by az on 2005-11-27
[http://www.tanzband-scream.at/line6/download/podxtpro-0.5.2.tar.bz2](http://www.tanzband-scream.at/line6/download/podxtpro-0.5.2.tar.bz2)

Use the source package and not the rpm.  Install linux-headers-386 (or 686 or k7 or whatever your kernel is) and build-essential and gcc-3.4

---

### Post by schizoid_embolism on 2005-11-28
Thank you for your help.

Jeremy

---

