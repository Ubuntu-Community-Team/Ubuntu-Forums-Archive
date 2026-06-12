---
title: "apt question"
date: 2006-02-04
forum: Installation &amp; Upgrades
---

### Post by asv on 2006-02-04
I'm trying to do an apt-get build-dep for a particular package. But I keep get an error about a lib that is now missing, but it was really just renamed. 

```
asv@probe:/usr/lib/f-spot$ sudo apt-get build-dep f-spot
Reading package lists... Done
Building dependency tree... Done
Package libdbus-cil is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libdbus-1-cil
The following NEW packages will be installed
  cdbs cli-common libart-2.0-dev libatk1.0-dev libaudiofile-dev
  libavahi-client-dev libavahi-common-dev libavahi-glib-dev libbonobo2-dev
  libbonoboui2-dev libcairo2-dev libdbus-1-dev libesd0-dev libexif-dev
  libexpat1-dev libfontconfig1-dev libfreetype6-dev libgconf2-dev
  libgcrypt11-dev libglade2-dev libgnome-keyring-dev libgnome2-dev
  libgnomecanvas2-dev libgnomeui-dev libgnomevfs2-dev libgnutls11-dev
  libgpg-error-dev libgphoto2-2-dev libgtk2.0-dev libidl-dev liblcms1-dev
  libmono-dev libopencdk8-dev liborbit2-dev libpango1.0-dev libpng12-dev
  libsqlite0-dev libtasn1-2-dev libxcursor-dev libxfixes-dev libxft-dev
  libxinerama-dev libxrandr-dev libxrender-dev mono-mcs mono-utils x-dev
  x11proto-fixes-dev x11proto-randr-dev x11proto-render-dev
  x11proto-xinerama-dev
0 upgraded, 51 newly installed, 0 to remove and 0 not upgraded.
E: Package libdbus-cil has no installation candidate
E: Failed to process build dependencies
```

Is there any option for apt-get that will get this to do a build-dep regardless of the missing dependency?

---

### Post by joft on 2006-02-04
Hi,

did you try to install libdbus-1-cil manually (apt-get install ...) instead?

And then, maybe it wouldn't be a bad idea to download the sources of f-spot manually, unpacking it (dpkg-source -x ....), changing the "Build-Depends:" line of debian/control to point to libdbus-1-cil instead of libdbus-cil. Afterwards you do the usual "dpkg-buildpackage -rfakeroot" for example.

That's the way I would do it.

---

