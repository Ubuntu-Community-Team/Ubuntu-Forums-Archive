---
title: "Cannot build fglrx package"
date: 2013-02-15
forum: Hardware
---

### Post by rudeboyskunk on 2013-02-15
I have been following the instructions [here]("http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29") religiously for installing the latest AMD legacy driver.

Yes, I have all of the dependencies installed.  Yes, I commented out "blacklist fglrx."

I am using Ubuntu 12.04 64-bit.  I have an ATI Mobility Radeon 4200.

Everything goes fine, it seems, in the building of the package, until the end, when I start to get these errors:

```
objdump: debian/fglrx/usr/lib/pxpress/ld.so.conf: File format not recognized
objdump: debian/fglrx/usr/lib/pxpress/alt_ld.so.conf: File truncated
objdump: debian/fglrx/usr/lib/fglrx/ld.so.conf: File format not recognized
objdump: debian/fglrx/usr/lib/fglrx/alt_ld.so.conf: File truncated
   debian/rules override_dh_shlibdeps
make[1]: Entering directory `/tmp/fglrx.crygJL'
dh_shlibdeps -l/tmp/fglrx.crygJL/debian/fglrx/usr/lib/fglrx:/tmp/fglrx.crygJL/debian/fglrx/usr/lib32/fglrx -Xlib32
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 contains an unresolvable reference to symbol dlsym: it's probably a plugin.
dpkg-shlibdeps: warning: 21 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/bin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin.
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libGL.so.1.2 contains an unresolvable reference to symbol XOpenDisplay: it's probably a plugin.
dpkg-shlibdeps: warning: 31 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: error: no dependency information found for /usr/lib/libQtGui.so.4 (used by debian/fglrx/usr/lib/fglrx/bin/amdnotifyui).
dh_shlibdeps: dpkg-shlibdeps -Tdebian/fglrx.substvars debian/fglrx/usr/lib/fglrx/libGL.so.1.2 debian/fglrx/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so debian/fglrx/usr/lib/fglrx/xorg/modules/extensions/libglx.so debian/fglrx/usr/lib/fglrx/xorg/modules/linux/libfglrxdrm.so debian/fglrx/usr/lib/fglrx/xorg/modules/amdxmm.so debian/fglrx/usr/lib/fglrx/xorg/modules/glesx.so debian/fglrx/usr/lib/fglrx/bin/atieventsd debian/fglrx/usr/lib/fglrx/bin/fglrxinfo debian/fglrx/usr/lib/fglrx/bin/atiode debian/fglrx/usr/lib/fglrx/bin/fgl_glxgears debian/fglrx/usr/lib/fglrx/bin/atiodcli debian/fglrx/usr/lib/fglrx/bin/aticonfig debian/fglrx/usr/lib/fglrx/bin/amdnotifyui debian/fglrx/usr/lib/fglrx/libaticalrt.so debian/fglrx/usr/lib/fglrx/libatiadlxx.so debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so debian/fglrx/usr/lib/fglrx/libaticaldd.so debian/fglrx/usr/lib/fglrx/libSlotMaximizerAg.so debian/fglrx/usr/lib/fglrx/libatiuki.so.1.0 debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 debian/fglrx/usr/lib/fglrx/libXvBAW.so.1.0 debian/fglrx/usr/lib/fglrx/libamdocl64.so debian/fglrx/usr/lib/fglrx/libaticalcl.so debian/fglrx/usr/lib/fglrx/libSlotMaximizerBe.so debian/fglrx/usr/lib/fglrx/libOpenCL.so.1 debian/fglrx/usr/lib/fglrx/libfglrx_dm.so.1.0 returned exit code 2
make[1]: *** [override_dh_shlibdeps] Error 2
make[1]: Leaving directory `/tmp/fglrx.crygJL'
make: *** [binary-arch] Error 2
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.SiOvaI

```

Googling shows me that a lot of people have this problem, and not a single post had a solution (except to delete /usr/share/ati/lib64 or something like that, but anyway it doesn't even exist on my computer).

The first part of the errors (objdump: debian/fglrx/usr/lib/pxpress/ld.so.conf: File format not recognized) seems pretty strange.  Isn't .conf a pretty normal extension?  ld.so.conf is a pretty vital file if I remember right, so how can its format not be recognized?

Any ideas?????

---

### Post by rudeboyskunk on 2013-02-16
*bump* Really?  No ideas whatsoever?

---

