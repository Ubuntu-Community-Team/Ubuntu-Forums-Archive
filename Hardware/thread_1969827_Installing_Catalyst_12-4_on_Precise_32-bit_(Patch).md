---
title: "Installing Catalyst 12-4 on Precise 32-bit (Patch)"
date: 2012-04-30
forum: Hardware
---

### Post by Yellow Pasque on 2012-04-30
NOTE: Most people should use the fglrx package included in Precise, since it is very similar to Catalyst 12-4 and is already patched to fix this error: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/947871](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/947871)

On Ubuntu 12.04 32-bit, attempting to manually install the fglrx/Catalyst 12-4 driver from AMD's site results in a failed build and this error in the log:
```
fglrx kernel module failed to build [KCL_fpu_begin: Error: 'TS_USEDFPU' undeclared (first use in this function)]
```
The error occurs because Catalyst has not been updated to work with recent 3.2 kernels. The following procedure works around the build error. I assume you are using this guide for manual Catalyst installation: [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

```
sudo apt-get install build-essential cdbs dh-make dkms execstack dh-modaliases fakeroot
cd ~/; mkdir catalyst12.4; cd catalyst12.4/
wget http://www2.ati.com/drivers/linux/amd-driver-installer-12-4-x86.x86_64.run
chmod +x amd-driver-installer-12-4-x86.x86_64.run
./amd-driver-installer-12-4-x86.x86_64.run --extract driver
cd driver/common/lib/modules/fglrx/build_mod/
wget -O fglrx.patch http://ubuntuone.com/5gNgEmVfzs3ytD5QZ2YGCi
patch -p1 < fglrx.patch
cd ~/catalyst12.4/driver/
./ati-installer.sh 8.961 --buildpkg Ubuntu/precise
cd ../
```

Now, you should have .deb's ready to install and you can continue following the wiki guide.

Thanks to 'Gennar1' at Phoronix for the patch: [http://phoronix.com/forums/showthread.php?68922-Patch-to-compile-fgrlx-module-on-Linux-3-3-rc4-with-x86-32-bit-arch](http://phoronix.com/forums/showthread.php?68922-Patch-to-compile-fgrlx-module-on-Linux-3-3-rc4-with-x86-32-bit-arch)

---

### Post by RepWolf on 2012-05-01
I had the error reported above and finally switched to the Ubuntu 64bit version which fixed the problem and I was able to install Catalyst 12.4 with a Radeon HD 4200 integrated graphics card. 

However, despite manually installing the Catalyst driver: under "Additional Hardware" in "Settings", Ubuntu reports that "No proprietary drivers are in use on this system" and it suggests that I install "ATI/AMD proprietary FGLRX graphics driver" and one with "post-release updates)

How do I confirm that my drivers are installed properly and register them with the system so they are activated?

---

### Post by Yellow Pasque on 2012-05-01
> **RepWolf said:**
> How do I confirm that my drivers are installed properly and register them with the system so they are activated?

"Additional Drivers" (aka jockey) only checks to see if the fglrx packages from the Ubuntu repo are installed. If you manually install fglrx/Catalyst, then jockey will give you that message. It's nothing to worry about. The important commands to check are:
```
fglrxinfo
fgl_glxgears
```

---

### Post by RepWolf on 2012-05-01
Thank you for replying so quickly!

I will check those commands tomorrow - but I should have mentioned that I did some reviews about jockey and did not quite get it.

I'll check back.

---

### Post by Outeger on 2012-05-02
Hi Temüjin,

I got following error while building package(s):

```

make[1]: Entering directory `/tmp/fglrx.vaMmLu'
dh_shlibdeps -l/tmp/fglrx.vaMmLu/debian/fglrx/usr/lib/fglrx
dpkg-shlibdeps: warning: symbol dlsym used by debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextCreateExtension used by debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XInitExtension used by debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XRead used by debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol sem_close used by debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XCloseDisplay used by debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XOpenDisplay used by debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XDisplayString used by debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XQueryExtension used by debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XReply used by debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: 12 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/bin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin.
dpkg-shlibdeps: warning: symbol XOpenDisplay used by debian/fglrx/usr/lib/fglrx/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XReadPad used by debian/fglrx/usr/lib/fglrx/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XFree used by debian/fglrx/usr/lib/fglrx/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XGetErrorDatabaseText used by debian/fglrx/usr/lib/fglrx/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XMaxRequestSize used by debian/fglrx/usr/lib/fglrx/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XCreateGC used by debian/fglrx/usr/lib/fglrx/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XFreeFontInfo used by debian/fglrx/usr/lib/fglrx/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XEHeadOfExtensionList used by debian/fglrx/usr/lib/fglrx/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XSend used by debian/fglrx/usr/lib/fglrx/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XQueryExtension used by debian/fglrx/usr/lib/fglrx/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: 19 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: error: no dependency information found for /usr/share/ati/lib/libQtGui.so.4 (used by debian/fglrx/usr/lib/fglrx/bin/amdnotifyui).
dh_shlibdeps: dpkg-shlibdeps -Tdebian/fglrx.substvars debian/fglrx/usr/lib/fglrx/libaticalrt.so debian/fglrx/usr/lib/fglrx/libOpenCL.so.1 debian/fglrx/usr/lib/fglrx/libaticaldd.so debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so debian/fglrx/usr/lib/fglrx/libSlotMaximizerBe.so debian/fglrx/usr/lib/fglrx/bin/aticonfig debian/fglrx/usr/lib/fglrx/bin/atiodcli debian/fglrx/usr/lib/fglrx/bin/fgl_glxgears debian/fglrx/usr/lib/fglrx/bin/amdnotifyui debian/fglrx/usr/lib/fglrx/bin/atieventsd debian/fglrx/usr/lib/fglrx/bin/atiode debian/fglrx/usr/lib/fglrx/bin/fglrxinfo debian/fglrx/usr/lib/fglrx/xorg/modules/glesx.so debian/fglrx/usr/lib/fglrx/xorg/modules/extensions/libglx.so debian/fglrx/usr/lib/fglrx/xorg/modules/amdxmm.so debian/fglrx/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so debian/fglrx/usr/lib/fglrx/xorg/modules/linux/libfglrxdrm.so debian/fglrx/usr/lib/fglrx/libfglrx_dm.so.1.0 debian/fglrx/usr/lib/fglrx/libXvBAW.so.1.0 debian/fglrx/usr/lib/fglrx/libatiadlxx.so debian/fglrx/usr/lib/fglrx/libaticalcl.so debian/fglrx/usr/lib/fglrx/libGL.so.1.2 debian/fglrx/usr/lib/fglrx/libatiuki.so.1.0 debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 debian/fglrx/usr/lib/fglrx/libamdocl32.so debian/fglrx/usr/lib/fglrx/libSlotMaximizerAg.so returned exit code 2
make[1]: *** [override_dh_shlibdeps] Error 2
make[1]: Leaving directory `/tmp/fglrx.vaMmLu'
make: *** [binary-arch] Error 2
dpkg-buildpackage: error: fakeroot debian/rules binary gave error exit status 2

```

Any idea?

Thanks

---

### Post by Yellow Pasque on 2012-05-03
^I don't have time to research at the moment, but is there a reason you're not just using fglrx package from repo?

---

### Post by Outeger on 2012-05-04
Sure i have a reason, regular fglrx package doesn't work either :) Nevermind, i solve it somehow... I don't know whats happened but it is now working after an upgrade of xorg.

---

### Post by huangtinge258 on 2012-05-08
Hi Temüjin and Outeger
I got the same error with you Outeger,but I'm new in ubuntu,I don't know how to solve it.
Can you show me something[I]specific or some codes
Thank you so much~!!!!!!~~~~~
[/I]

---

### Post by MarioMey on 2012-11-11
Hey, I'm trying to install Catalyst 12.4 drivers manually in Ubuntu 12.10. I need this version because newers don't support ATI 4250. I have this error, trying to install debs:

Error! Bad return status for module build on kernel: 3.5.0-18-generic (x86_64)

I have **Ubuntu 64bits**. Is it the same problem as this thread? Is it the same procedure to fix it?

---

### Post by Yellow Pasque on 2012-11-12
@MarioMey: no, that's a different problem. [https://bugs.launchpad.net/bugs/1058040](https://bugs.launchpad.net/bugs/1058040)

---

### Post by MarioMey on 2012-11-14
Thanks, Temüjin.

---

### Post by maxehhh2 on 2013-08-01
I get the following error trying to patch fglrx

> patching file firegl_public.cHunk #1 FAILED at 5807.
1 out of 1 hunk FAILED -- saving rejects to file firegl_public.c.rej




---

### Post by QIII on 2013-08-01
This is an old thread and has been marked solved.  You will be more likely to get help if you start a new thread.

Closed.

---

