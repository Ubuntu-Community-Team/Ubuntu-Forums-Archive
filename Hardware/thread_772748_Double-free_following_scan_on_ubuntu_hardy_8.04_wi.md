---
title: "Double-free following scan on ubuntu hardy 8.04 with	epjitsu fi-60f"
date: 2008-04-28
forum: Hardware
---

### Post by jeffk on 2008-04-28
via gmane.comp.graphics.scanning.sane.devel Mon, 28 Apr 2008

My Fujitusu Fi-60f produces a color scan on Ubuntu Hardy 8.04 Desktop,
but emits a double-free error at the end.

My purpose of this post is to gather information for a proper bug report
to the attention of Ubuntu.

If anyone knows how to correct this directly (rebuild package, etc.), I'd
be very interested as well, as we're going to use this scanner immediately.

The error does not prevent me from using scanimage, but the more
user-friendly GUI scan tools, gscan2pdf in particular, encounter an
intolderable number of modal dialogs announcing the error.

Thanks,
Jeff

```

  $ cat /etc/sane.d/epjitsu.conf
  (...)
  # Fujitsu fi-60F
  firmware /usr/share/sane/epjitsu/60f_0A00.nal
  usb 0x04c5 0x10c7

  $ ls -al /usr/share/sane/epjitsu/60f_0A00.nal
  -rw-r--r-- 1 root root 65793 2008-04-28 13:09 /usr/share/sane/epjitsu/60f_0A00.nal

  $ scanimage -d epjitsu
  (massive ansi terminal spew)
  *** glibc detected *** scanimage: double free or corruption (!prev): 0x08053ca0 ***
  ======= Backtrace: =========
  /lib/tls/i686/cmov/libc.so.6[0xb7e7fa85]
  /lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7e834f0]
  /usr/lib/sane/libsane-epjitsu.so.1(sane_epjitsu_exit+0x3d)[0xb7e029dd]
  /usr/lib/libsane.so.1(sane_dll_exit+0x15d)[0xb7f69c8d]
  /usr/lib/libsane.so.1(sane_exit+0x17)[0xb7f6af97]
  scanimage[0x804b59d]
  /lib/tls/i686/cmov/libc.so.6(exit+0xd4)[0xb7e42084]
  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe8)[0xb7e2a458]
  scanimage[0x8049241]
  ======= Memory map: ========
  08048000-08051000 r-xp 00000000 08:05 6447711    /usr/bin/scanimage
  08051000-08052000 rw-p 00009000 08:05 6447711    /usr/bin/scanimage
  08052000-080c6000 rw-p 08052000 00:00 0          [heap]
  b7c00000-b7c21000 rw-p b7c00000 00:00 0 
  b7c21000-b7d00000 ---p b7c21000 00:00 0 
  b7de2000-b7dec000 r-xp 00000000 08:05 7716880    /lib/libgcc_s.so.1
  b7dec000-b7ded000 rw-p 0000a000 08:05 7716880    /lib/libgcc_s.so.1
  b7df8000-b7dfe000 r-xp 00000000 08:05 7717114    /lib/libusb-0.1.so.4.4.4
  b7dfe000-b7e00000 rw-p 00005000 08:05 7717114    /lib/libusb-0.1.so.4.4.4
  b7e00000-b7e0f000 r-xp 00000000 08:05 935162     /usr/lib/sane/libsane-epjitsu.so.1.0.19
  b7e0f000-b7e10000 rw-p 0000e000 08:05 935162     /usr/lib/sane/libsane-epjitsu.so.1.0.19
  b7e10000-b7e14000 rw-p b7e10000 00:00 0 
  b7e14000-b7f5d000 r-xp 00000000 08:05 7717018    /lib/tls/i686/cmov/libc-2.7.so
  b7f5d000-b7f5e000 r--p 00149000 08:05 7717018    /lib/tls/i686/cmov/libc-2.7.so
  b7f5e000-b7f60000 rw-p 0014a000 08:05 7717018    /lib/tls/i686/cmov/libc-2.7.so
  b7f60000-b7f64000 rw-p b7f60000 00:00 0 
  b7f64000-b7f66000 r-xp 00000000 08:05 7717021    /lib/tls/i686/cmov/libdl-2.7.so
  b7f66000-b7f68000 rw-p 00001000 08:05 7717021    /lib/tls/i686/cmov/libdl-2.7.so
  b7f68000-b7f6d000 r-xp 00000000 08:05 856953     /usr/lib/libsane.so.1.0.19
  b7f6d000-b7f6e000 rw-p 00004000 08:05 856953     /usr/lib/libsane.so.1.0.19
  b7f78000-b7f7b000 rw-p b7f78000 00:00 0 
  b7f7b000-b7f7c000 r-xp b7f7b000 00:00 0          [vdso]
  b7f7c000-b7f96000 r-xp 00000000 08:05 7716881    /lib/ld-2.7.so
  b7f96000-b7f98000 rw-p 00019000 08:05 7716881    /lib/ld-2.7.so
  bfed7000-bfeec000 rw-p bffeb000 00:00 0          [stack]
  Aborted
  
  ~$ scanimage -d epjitsu --format=tiff > foo.tiff
  *** glibc detected *** scanimage: double free or corruption (!prev): 0x08053ca0 ***
  ======= Backtrace: =========
  /lib/tls/i686/cmov/libc.so.6[0xb7ec9a85]
  /lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7ecd4f0]
  /usr/lib/sane/libsane-epjitsu.so.1(sane_epjitsu_exit+0x3d)[0xb7e4c9dd]
  /usr/lib/libsane.so.1(sane_dll_exit+0x15d)[0xb7fb3c8d]
  /usr/lib/libsane.so.1(sane_exit+0x17)[0xb7fb4f97]
  scanimage[0x804b59d]
  /lib/tls/i686/cmov/libc.so.6(exit+0xd4)[0xb7e8c084]
  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe8)[0xb7e74458]
  scanimage[0x8049241]
  ======= Memory map: ========
  08048000-08051000 r-xp 00000000 08:05 6447711    /usr/bin/scanimage
  08051000-08052000 rw-p 00009000 08:05 6447711    /usr/bin/scanimage
  08052000-080c6000 rw-p 08052000 00:00 0          [heap]
  b7d00000-b7d21000 rw-p b7d00000 00:00 0 
  b7d21000-b7e00000 ---p b7d21000 00:00 0 
  b7e2c000-b7e36000 r-xp 00000000 08:05 7716880    /lib/libgcc_s.so.1
  b7e36000-b7e37000 rw-p 0000a000 08:05 7716880    /lib/libgcc_s.so.1
  b7e42000-b7e48000 r-xp 00000000 08:05 7717114    /lib/libusb-0.1.so.4.4.4
  b7e48000-b7e4a000 rw-p 00005000 08:05 7717114    /lib/libusb-0.1.so.4.4.4
  b7e4a000-b7e59000 r-xp 00000000 08:05 935162     /usr/lib/sane/libsane-epjitsu.so.1.0.19
  b7e59000-b7e5a000 rw-p 0000e000 08:05 935162     /usr/lib/sane/libsane-epjitsu.so.1.0.19
  b7e5a000-b7e5e000 rw-p b7e5a000 00:00 0 
  b7e5e000-b7fa7000 r-xp 00000000 08:05 7717018    /lib/tls/i686/cmov/libc-2.7.so
  b7fa7000-b7fa8000 r--p 00149000 08:05 7717018    /lib/tls/i686/cmov/libc-2.7.so
  b7fa8000-b7faa000 rw-p 0014a000 08:05 7717018    /lib/tls/i686/cmov/libc-2.7.so
  b7faa000-b7fae000 rw-p b7faa000 00:00 0 
  b7fae000-b7fb0000 r-xp 00000000 08:05 7717021    /lib/tls/i686/cmov/libdl-2.7.so
  b7fb0000-b7fb2000 rw-p 00001000 08:05 7717021    /lib/tls/i686/cmov/libdl-2.7.so
  b7fb2000-b7fb7000 r-xp 00000000 08:05 856953     /usr/lib/libsane.so.1.0.19
  b7fb7000-b7fb8000 rw-p 00004000 08:05 856953     /usr/lib/libsane.so.1.0.19
  b7fc2000-b7fc5000 rw-p b7fc2000 00:00 0 
  b7fc5000-b7fc6000 r-xp b7fc5000 00:00 0          [vdso]
  b7fc6000-b7fe0000 r-xp 00000000 08:05 7716881    /lib/ld-2.7.so
  b7fe0000-b7fe2000 rw-p 00019000 08:05 7716881    /lib/ld-2.7.so
  bfaa3000-bfab8000 rw-p bffeb000 00:00 0          [stack]
  Aborted  
```

---

### Post by jeffk on 2008-05-06
Could I get some debian-packagers assistance on applying this upstream patch to rebuild sane-backends?

The backend author made the following commits to CVS in response to the report:
[URL="https://alioth.debian.org/plugins/scmcvs/cvsweb.php/sane-backends/backend/epjitsu.c.diff?cvsroot=sane&r2=1.6&r1=1.5&f=u"]
epjitsu.c.diff[/URL]
[URL="https://alioth.debian.org/plugins/scmcvs/cvsweb.php/sane-backends/backend/epjitsu.h.diff?cvsroot=sane&r2=1.3&r1=1.2&f=u"]
epjitsu.h.diff[/URL]

I'd like to test and if successful (and appropriate) file the bug for Ubuntu to incorporate this fix into a maintenance release.

I was given some instruction on how to patch and rebuild the source package:
[http://article.gmane.org/gmane.comp.graphics.scanning.sane.devel/13110]("http://article.gmane.org/gmane.comp.graphics.scanning.sane.devel/13110")

But I'm not quite following some of the debian-specific terminology, such as the dsc file, and what development packages will be needed to rebuild.

The machine which has the scanner in question is an ordinary 8.04 workstation, and I'd rather not install a full suite of development packages on that machine if possible.

Thanks for any step-by-step help suggestions,
Jeff

---

### Post by jeffk on 2008-05-06
I have made some progress on building from .dsc with dpkg-source, but am stuck on the proper way to append the two patch diffs to sane-backends_1.0.19-1ubuntu3.diff:

I simply concatenated the two epjitsu diffs, and followed the steps to rebuild the package, but the patch is failing. My format must not be correct for sane-backends_1.0.19-1ubuntu3.diff.

Any suggestions? Thanks.

---

