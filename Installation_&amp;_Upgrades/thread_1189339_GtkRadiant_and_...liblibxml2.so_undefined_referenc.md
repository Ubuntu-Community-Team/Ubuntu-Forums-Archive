---
title: "GtkRadiant and .../lib/libxml2.so: undefined reference to `gzopen64'"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by Lean 946 on 2009-06-16
Hi, 
I'm here with a problem regarding compiling GtkRadiant from svn, along with some-other-project-yet-to-be-compiled by me, which have the same problem.
GtkRadiant uses Scons, which leads to a very simple command: scons SETUP=0
However:
```
lean@Ubuntu:/home/compiles/GtkRadiant$ scons SETUP=0
python: /usr/lib/libz.so.1: no version information available (required by python)
scons: Reading SConscript files ...
SCons.Script:4: DeprecationWarning: The popen2 module is deprecated.  Use the subprocess module.
SCons 1.2.0
OS="Linux"
Loading build configuration from site.conf
CC="gcc"
CXX="g++"
JOBS="1"
BUILD="debug"
version: 1.5.0
minor: 0 major: 5
about message is in /home/compiles/GtkRadiant/include/aboutmsg.default
about: Custom build based on trunk\ngcc version: 4.3.3

scons: warning: The env.Copy() method is deprecated; use the env.Clone() method instead.
File "/home/compiles/GtkRadiant/SConscript", line 19, in <module>
(some more random things with the SConscript file...)
File "/home/compiles/GtkRadiant/SConscript", line 290, in <module>
scons: done reading SConscript files.
scons: Building targets ...
scons: building associated VariantDir targets: build
g++ -o build/debug/h2data -fPIC -Wl,-fini,fini_stub -L. -static-libgcc `xml2-config --libs` -lpthread build/debug/tools/quake2/qdata_heretic2/common/bspfile.o build/debug/tools/quake2/qdata_heretic2/common/cmdlib.o build/debug/tools/quake2/qdata_heretic2/common/inout.o build/debug/tools/quake2/qdata_heretic2/common/l3dslib.o build/debug/tools/quake2/qdata_heretic2/common/lbmlib.o build/debug/tools/quake2/qdata_heretic2/common/mathlib.o build/debug/tools/quake2/qdata_heretic2/common/md4.o build/debug/tools/quake2/qdata_heretic2/common/path_init.o build/debug/tools/quake2/qdata_heretic2/common/qfiles.o build/debug/tools/quake2/qdata_heretic2/common/scriplib.o build/debug/tools/quake2/qdata_heretic2/common/threads.o build/debug/tools/quake2/qdata_heretic2/common/token.o build/debug/tools/quake2/qdata_heretic2/common/trilib.o build/debug/tools/quake2/qdata_heretic2/qcommon/reference.o build/debug/tools/quake2/qdata_heretic2/qcommon/resourcemanager.o build/debug/tools/quake2/qdata_heretic2/qcommon/skeletons.o build/debug/tools/quake2/qdata_heretic2/animcomp.o build/debug/tools/quake2/qdata_heretic2/book.o build/debug/tools/quake2/qdata_heretic2/fmodels.o build/debug/tools/quake2/qdata_heretic2/images.o build/debug/tools/quake2/qdata_heretic2/jointed.o build/debug/tools/quake2/qdata_heretic2/models.o build/debug/tools/quake2/qdata_heretic2/pics.o build/debug/tools/quake2/qdata_heretic2/qdata.o build/debug/tools/quake2/qdata_heretic2/qd_skeletons.o build/debug/tools/quake2/qdata_heretic2/sprites.o build/debug/tools/quake2/qdata_heretic2/svdcmp.o build/debug/tools/quake2/qdata_heretic2/tables.o build/debug/tools/quake2/qdata_heretic2/tmix.o build/debug/tools/quake2/qdata_heretic2/video.o -Lbuild/debug/libs -Llibs -ll_net
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/libxml2.so: undefined reference to `gzopen64'
collect2: ld returned error status 1
scons: *** [build/debug/h2data] Error 1
scons: building terminated because of errors.

```
A ls /usr/lib | grep libz returns:
```
libz.so.1.2.1
libzip.so.1
libzip.so.1.0.0
libzephyr.so.3
libzephyr.so.3.0.0
libz.so.1
libz.a
libz.so
libzzip-0.so.13
libzzip-0.so.13.0.49
libzzipfseeko-0.so.13
libzzipfseeko-0.so.13.0.49
libzzipmmapped-0.so.13
libzzipmmapped-0.so.13.0.49
libzzipwrap-0.so.13
libzzipwrap-0.so.13.0.49
libz.so.1.2.1
libzip.so.1
libzip.so.1.0.0
libzephyr.so.3
libzephyr.so.3.0.0
libz.so.1
libz.a
libz.so
libzzip-0.so.13
libzzip-0.so.13.0.49
libzzipfseeko-0.so.13
libzzipfseeko-0.so.13.0.49
libzzipmmapped-0.so.13
libzzipmmapped-0.so.13.0.49
libzzipwrap-0.so.13
libzzipwrap-0.so.13.0.49

```
I can post some more info if you need.
Thanks in advance.

---

