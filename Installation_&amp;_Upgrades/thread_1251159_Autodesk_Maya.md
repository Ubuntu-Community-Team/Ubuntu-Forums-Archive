---
title: "Autodesk Maya"
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by elmnas on 2009-08-27
Hi guys when Im trying to install Autodesk maya its of course rpm files but when Im trying to convert a from rpm to deb I get error  just read in the end please help me out-->

   1.
      root@Dapeamel:~/Linux-64# alien -cv AWCommon-11.5-19.i686.rpm
   2.
              LANG=C rpm -qp --queryformat %{NAME} AWCommon-11.5-19.i686.rpm
   3.
              LANG=C rpm -qp --queryformat %{VERSION} AWCommon-11.5-19.i686.rpm
   4.
              LANG=C rpm -qp --queryformat %{RELEASE} AWCommon-11.5-19.i686.rpm
   5.
              LANG=C rpm -qp --queryformat %{ARCH} AWCommon-11.5-19.i686.rpm
   6.
              LANG=C rpm -qp --queryformat %{CHANGELOGTEXT} AWCommon-11.5-19.i686.rpm
   7.
              LANG=C rpm -qp --queryformat %{SUMMARY} AWCommon-11.5-19.i686.rpm
   8.
              LANG=C rpm -qp --queryformat %{DESCRIPTION} AWCommon-11.5-19.i686.rpm
   9.
              LANG=C rpm -qp --queryformat %{COPYRIGHT} AWCommon-11.5-19.i686.rpm
  10.
              LANG=C rpm -qp --queryformat %{PREFIXES} AWCommon-11.5-19.i686.rpm
  11.
              LANG=C rpm -qp --queryformat %{POSTIN} AWCommon-11.5-19.i686.rpm
  12.
              LANG=C rpm -qp --queryformat %{POSTUN} AWCommon-11.5-19.i686.rpm
  13.
              LANG=C rpm -qp --queryformat %{PREUN} AWCommon-11.5-19.i686.rpm
  14.
              LANG=C rpm -qp --queryformat %{PREIN} AWCommon-11.5-19.i686.rpm
  15.
              LANG=C rpm -qcp AWCommon-11.5-19.i686.rpm
  16.
              rpm -qpi AWCommon-11.5-19.i686.rpm
  17.
              LANG=C rpm -qpl AWCommon-11.5-19.i686.rpm
  18.
              mkdir AWCommon-11.5
  19.
              chmod 755 AWCommon-11.5
  20.
              rpm2cpio AWCommon-11.5-19.i686.rpm | (cd AWCommon-11.5; cpio --extract --make-directories --no-absolute-filenames --preserve-modification-time) 2>&1
  21.
              chmod 755 AWCommon-11.5/./
  22.
              chmod 755 AWCommon-11.5/./usr
  23.
              chmod 755 AWCommon-11.5/./usr/aw
  24.
              chmod 755 AWCommon-11.5/./usr/aw/COM
  25.
              chown 0:0 AWCommon-11.5//usr/aw/COM/bin
  26.
              chmod 777 AWCommon-11.5//usr/aw/COM/bin
  27.
              chown 0:0 AWCommon-11.5//usr/aw/COM/bin/awinfo
  28.
              chmod 755 AWCommon-11.5//usr/aw/COM/bin/awinfo
  29.
              chown 0:0 AWCommon-11.5//usr/aw/COM/bin/getid
  30.
              chmod 755 AWCommon-11.5//usr/aw/COM/bin/getid
  31.
              chown 0:0 AWCommon-11.5//usr/aw/COM/bin/installKey
  32.
              chmod 755 AWCommon-11.5//usr/aw/COM/bin/installKey
  33.
              chown 0:0 AWCommon-11.5//usr/aw/COM/bin/lmutil
  34.
              chmod 755 AWCommon-11.5//usr/aw/COM/bin/lmutil
  35.
              chown 0:0 AWCommon-11.5//usr/aw/COM/lib
  36.
              chmod 777 AWCommon-11.5//usr/aw/COM/lib
  37.
              chown 0:0 AWCommon-11.5//usr/aw/COM/lib/libXm.so.2.1
  38.
              chmod 755 AWCommon-11.5//usr/aw/COM/lib/libXm.so.2.1
  39.
              mkdir AWCommon-11.5/debian
  40.
              hostname -f
  41.
              date -R
  42.
              hostname -f
  43.
              date -R
  44.
              chmod 755 AWCommon-11.5/debian/rules
  45.
              debian/rules binary 2>&1
  46.
      Package build failed. Here's the log:
  47.
      dh_testdir
  48.
      dh_testdir
  49.
      dh_testroot
  50.
      dh_clean -k -d
  51.
      dh_installdirs
  52.
      dh_installdocs
  53.
      dh_installchangelogs
  54.
      find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
  55.
                      xargs -0 -r -i cp -a {} debian/awcommon
  56.
      dh_compress
  57.
      dh_makeshlibs
  58.
      dh_installdeb
  59.
      dh_shlibdeps
  60.
      dpkg-shlibdeps: failure: couldn't find library libXm.so.2 needed by debian/awcommon/usr/aw/COM/bin/installKey (its RPATH is '').
  61.
      Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
  62.
      To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
  63.
      dh_shlibdeps: command returned error code 512
  64.
      make: [binary-arch] Error 1 (ignored)
  65.
      dh_gencontrol
  66.
      dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
  67.
      dh_gencontrol: command returned error code 65280
  68.
      make: *** [binary-arch] Error 1
  69.
              find AWCommon-11.5 -type d -exec chmod 755 {} ;
  70.
      find: `AWCommon-11.5': No such file or directory
  71.
              rm -rf AWCommon-11.5:guitar::guitar:

---

