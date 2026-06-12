---
title: "Ubunutu 6.10 upgrade to 8.04 LTS, LIVING NIGHTMARE!!"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by Dark_Meow1 on 2009-02-25
So I've searched the interwebs far and wide, and I am not getting anywhere.

I'm trying to upgrade to 8.04 from 6.10, and my update manager only checks and finds 7.04 available.  I then try to download the packages and updates, and that fails.  Here is what I get.

> Authentication Failed

Then I try the updates

> W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/u/util-linux/bsdutils_2.12r-11ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/u/util-linux/bsdutils_2.12r-11ubuntu2.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.4-1ubuntu12.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.4-1ubuntu12.3_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.4-1ubuntu12.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.4-1ubuntu12.3_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.4-1ubuntu12.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.4-1ubuntu12.3_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-libc-dev_2.6.17.1-12.44_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-libc-dev_2.6.17.1-12.44_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/e2fslibs_1.39-1ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/e2fslibs_1.39-1ubuntu0.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/e2fsprogs_1.39-1ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/e2fsprogs_1.39-1ubuntu0.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/u/util-linux/mount_2.12r-11ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/u/util-linux/mount_2.12r-11ubuntu2.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl-modules_5.8.8-6ubuntu0.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl-modules_5.8.8-6ubuntu0.1_all.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl_5.8.8-6ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl_5.8.8-6ubuntu0.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/perl/libperl5.8_5.8.8-6ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/perl/libperl5.8_5.8.8-6ubuntu0.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl-base_5.8.8-6ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl-base_5.8.8-6ubuntu0.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/tar/tar_1.15.91-2ubuntu0.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tar/tar_1.15.91-2ubuntu0.4_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/u/util-linux/util-linux_2.12r-11ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/u/util-linux/util-linux_2.12r-11ubuntu2.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/upstart/upstart-logd_0.2.7-7.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/upstart/upstart-logd_0.2.7-7.2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/upstart/upstart-compat-sysv_0.2.7-7.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/upstart/upstart-compat-sysv_0.2.7-7.2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/upstart/upstart_0.2.7-7.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/upstart/upstart_0.2.7-7.2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg/x11-common_7.1.1ubuntu6.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg/x11-common_7.1.1ubuntu6.2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsys2_1.2.4-2ubuntu3.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsys2_1.2.4-2ubuntu3.3_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-0_1.2.8rel-5.1ubuntu0.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-0_1.2.8rel-5.1ubuntu0.3_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsimage2_1.2.4-2ubuntu3.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsimage2_1.2.4-2ubuntu3.3_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/d/dbus/libdbus-1-3_0.93-0ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/d/dbus/libdbus-1-3_0.93-0ubuntu3.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6_2.2.1-5ubuntu0.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6_2.2.1-5ubuntu0.2_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libx/libx11/libx11-data_1.0.3-0ubuntu4.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libx11/libx11-data_1.0.3-0ubuntu4.1_all.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libx/libx11/libx11-6_1.0.3-0ubuntu4.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libx11/libx11-6_1.0.3-0ubuntu4.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo2_1.2.4-1ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo2_1.2.4-1ubuntu2.2_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-common_2.10.6-0ubuntu3.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-common_2.10.6-0ubuntu3.1_all.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-bin_2.10.6-0ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-bin_2.10.6-0ubuntu3.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.10.6-0ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.10.6-0ubuntu3.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler1-glib_0.5.4-0ubuntu4.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler1-glib_0.5.4-0ubuntu4.4_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler1_0.5.4-0ubuntu4.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler1_0.5.4-0ubuntu4.4_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/poppler/poppler-utils_0.5.4-0ubuntu4.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/poppler/poppler-utils_0.5.4-0ubuntu4.4_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gs-esp/gs-esp_8.15.2.dfsg.0ubuntu1-0ubuntu4.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gs-esp/gs-esp_8.15.2.dfsg.0ubuntu1-0ubuntu4.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-common_1.2.4-2ubuntu3.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-common_1.2.4-2ubuntu3.3_all.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys_1.2.4-2ubuntu3.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys_1.2.4-2ubuntu3.3_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_1.6.9-0ubuntu2.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_1.6.9-0ubuntu2.1_all.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/net-snmp/libsnmp-base_5.2.2-5ubuntu1.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/n/net-snmp/libsnmp-base_5.2.2-5ubuntu1.1_all.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8b-2ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8b-2ubuntu2.2_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/net-snmp/libsnmp9_5.2.2-5ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/n/net-snmp/libsnmp9_5.2.2-5ubuntu1.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_1.6.9-0ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_1.6.9-0ubuntu2.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_6.10+20080227_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_6.10+20080227_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_6.10+20080227_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_6.10+20080227_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-style-industrial_2.0.4-0ubuntu7_all.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-style-industrial_2.0.4-0ubuntu7_all.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-style-default_2.0.4-0ubuntu7_all.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-style-default_2.0.4-0ubuntu7_all.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-calc_2.0.4-0ubuntu7_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-calc_2.0.4-0ubuntu7_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/i/icu/libicu34_3.4.1a-1ubuntu1.6.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/i/icu/libicu34_3.4.1a-1ubuntu1.6.10.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libw/libwpd/libwpd8c2a_0.8.6-1ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libw/libwpd/libwpd8c2a_0.8.6-1ubuntu0.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/python2.4/python2.4_2.4.4~c1-0ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/python2.4/python2.4_2.4.4~c1-0ubuntu1.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/python2.4/python2.4-minimal_2.4.4~c1-0ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/python2.4/python2.4-minimal_2.4.4~c1-0ubuntu1.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bzip2/bzip2_1.0.3-3ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bzip2/bzip2_1.0.3-3ubuntu0.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bzip2/libbz2-1.0_1.0.3-3ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bzip2/libbz2-1.0_1.0.3-3ubuntu0.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/python-uno_2.0.4-0ubuntu7_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/python-uno_2.0.4-0ubuntu7_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-writer_2.0.4-0ubuntu7_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-writer_2.0.4-0ubuntu7_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-impress_2.0.4-0ubuntu7_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-impress_2.0.4-0ubuntu7_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-draw_2.0.4-0ubuntu7_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-draw_2.0.4-0ubuntu7_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-java-common_2.0.4-0ubuntu7_all.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-java-common_2.0.4-0ubuntu7_all.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-base_2.0.4-0ubuntu7_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-base_2.0.4-0ubuntu7_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gtk_2.0.4-0ubuntu7_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gtk_2.0.4-0ubuntu7_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common-data_0.6.13-2ubuntu2.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common-data_0.6.13-2ubuntu2.4_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common3_0.6.13-2ubuntu2.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common3_0.6.13-2ubuntu2.4_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-client3_0.6.13-2ubuntu2.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-client3_0.6.13-2ubuntu2.4_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-glib1_0.6.13-2ubuntu2.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-glib1_0.6.13-2ubuntu2.4_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libcomerr2_1.39-1ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libcomerr2_1.39-1ubuntu0.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb53_1.4.3-9ubuntu1.6_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb53_1.4.3-9ubuntu1.6_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2_2.6.26.dfsg-2ubuntu4.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2_2.6.26.dfsg-2ubuntu4.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/d/dbus/dbus_0.93-0ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/d/dbus/dbus_0.93-0ubuntu3.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.22-1ubuntu4.5_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.22-1ubuntu4.5_i386.deb)
  404 Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-vfs2/libgnomevfs2-extra_2.16.1-0ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-vfs2/libgnomevfs2-extra_2.16.1-0ubuntu7_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-vfs2/libgnomevfs2-0_2.16.1-0ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-vfs2/libgnomevfs2-0_2.16.1-0ubuntu7_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-vfs2/libgnomevfs2-common_2.16.1-0ubuntu7_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-vfs2/libgnomevfs2-common_2.16.1-0ubuntu7_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gnome_2.0.4-0ubuntu7_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gnome_2.0.4-0ubuntu7_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-evolution_2.0.4-0ubuntu7_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-evolution_2.0.4-0ubuntu7_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-math_2.0.4-0ubuntu7_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-math_2.0.4-0ubuntu7_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org_2.0.4-0ubuntu7_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org_2.0.4-0ubuntu7_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/ttf-opensymbol_2.0.4-0ubuntu7_all.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/ttf-opensymbol_2.0.4-0ubuntu7_all.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/nas/libaudio2_1.8-2ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/n/nas/libaudio2_1.8-2ubuntu0.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/curl/libcurl3_7.15.4-1ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/curl/libcurl3_7.15.4-1ubuntu2.2_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/flac/libflac7_1.1.2-5ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/flac/libflac7_1.1.2-5ubuntu1.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libs/libsndfile/libsndfile1_1.0.16-1ubuntu0.6.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libs/libsndfile/libsndfile1_1.0.16-1ubuntu0.6.10.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_2.0.4-0ubuntu7_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_2.0.4-0ubuntu7_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-common_2.0.4-0ubuntu7_all.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-common_2.0.4-0ubuntu7_all.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/screen/screen_4.0.2-4.1ubuntu5.6.10_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/screen/screen_4.0.2-4.1ubuntu5.6.10_i386.deb)
  404 Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-video-all_7.1.1ubuntu6.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-video-all_7.1.1ubuntu6.2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-input-all_7.1.1ubuntu6.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-input-all_7.1.1ubuntu6.2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libx/libxfont/libxfont1_1.2.0-0ubuntu3.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxfont/libxfont1_1.2.0-0ubuntu3.2_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.1.1-0ubuntu12.5_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.1.1-0ubuntu12.5_i386.deb)
  404 Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xutils_7.1.1ubuntu6.2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xutils_7.1.1ubuntu6.2_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xbase-clients_7.1.1ubuntu6.2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xbase-clients_7.1.1ubuntu6.2_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg_7.1.1ubuntu6.2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg_7.1.1ubuntu6.2_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libblkid1_1.39-1ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libblkid1_1.39-1ubuntu0.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libss2_1.39-1ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libss2_1.39-1ubuntu0.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libuuid1_1.39-1ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libuuid1_1.39-1ubuntu0.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gnupg/gnupg_1.4.3-2ubuntu3.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gnupg/gnupg_1.4.3-2ubuntu3.3_i386.deb)
  404 Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/udev/libvolumeid0_093-0ubuntu18.0edgy2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/udev/libvolumeid0_093-0ubuntu18.0edgy2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/udev/udev_093-0ubuntu18.0edgy2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/udev/udev_093-0ubuntu18.0edgy2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/udev/volumeid_093-0ubuntu18.0edgy2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/udev/volumeid_093-0ubuntu18.0edgy2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/u/util-linux/util-linux-locales_2.12r-11ubuntu2.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/u/util-linux/util-linux-locales_2.12r-11ubuntu2.1_all.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/v/vim/vim-tiny_7.0-035+1ubuntu5.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/v/vim/vim-tiny_7.0-035+1ubuntu5.2_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/v/vim/vim-common_7.0-035+1ubuntu5.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/v/vim/vim-common_7.0-035+1ubuntu5.2_i386.deb)
  404 Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/upstart/startup-tasks_0.2.7-7.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/upstart/startup-tasks_0.2.7-7.2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/upstart/system-services_0.2.7-7.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/upstart/system-services_0.2.7-7.2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2008a-0ubuntu0.6.10_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2008a-0ubuntu0.6.10_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisc11_9.3.2-2ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisc11_9.3.2-2ubuntu3.3_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libdns21_9.3.2-2ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libdns21_9.3.2-2ubuntu3.3_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccc0_9.3.2-2ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccc0_9.3.2-2ubuntu3.3_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccfg1_9.3.2-2ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccfg1_9.3.2-2ubuntu3.3_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libbind9-0_9.3.2-2ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libbind9-0_9.3.2-2ubuntu3.3_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/liblwres9_9.3.2-2ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/liblwres9_9.3.2-2ubuntu3.3_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/bind9-host_9.3.2-2ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/bind9-host_9.3.2-2ubuntu3.3_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/dnsutils_9.3.2-2ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/dnsutils_9.3.2-2ubuntu3.3_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/file/file_4.17-2ubuntu1.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/file/file_4.17-2ubuntu1.2_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/file/libmagic1_4.17-2ubuntu1.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/file/libmagic1_4.17-2ubuntu1.2_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/info_4.8.dfsg.1-1ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/info_4.8.dfsg.1-1ubuntu0.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/i/iptables/iptables_1.3.5.0debian1-1ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/i/iptables/iptables_1.3.5.0debian1-1ubuntu2.1_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.3p2-5ubuntu1.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.3p2-5ubuntu1.2_i386.deb)
  404 Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/popularity-contest/popularity-contest_1.33ubuntu2.3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/popularity-contest/popularity-contest_1.33ubuntu2.3_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/r/rsync/rsync_2.6.8-2ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/r/rsync/rsync_2.6.8-2ubuntu3.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/tcpdump/tcpdump_3.9.4-4ubuntu0.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tcpdump/tcpdump_3.9.4-4ubuntu0.2_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/w/w3m/w3m_0.5.1-4ubuntu2.6.10_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/w/w3m/w3m_0.5.1-4ubuntu2.6.10_i386.deb)
  404 Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/app-install-data-commercial/app-install-data-commercial_6.3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/app-install-data-commercial/app-install-data-commercial_6.3_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libv/libvorbis/libvorbis0a_1.1.2-1ubuntu1.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libv/libvorbis/libvorbis0a_1.1.2-1ubuntu1.2_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libv/libvorbis/libvorbisenc2_1.1.2-1ubuntu1.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libv/libvorbis/libvorbisenc2_1.1.2-1ubuntu1.2_i386.deb)
  404 Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/a/audacity/audacity_1.2.4b-2.1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/a/audacity/audacity_1.2.4b-2.1ubuntu1_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-core4_0.6.13-2ubuntu2.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-core4_0.6.13-2ubuntu2.4_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-daemon_0.6.13-2ubuntu2.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-daemon_0.6.13-2ubuntu2.4_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserver1.2-7_1.8.1-0ubuntu5.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserver1.2-7_1.8.1-0ubuntu5.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/libnss3_1.firefox2.0.0.14+0nobinonly-0ubuntu0.6.10_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/libnss3_1.firefox2.0.0.14+0nobinonly-0ubuntu0.6.10_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libcamel1.2-8_1.8.1-0ubuntu5.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libcamel1.2-8_1.8.1-0ubuntu5.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/libnspr4_1.firefox2.0.0.14+0nobinonly-0ubuntu0.6.10_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/libnspr4_1.firefox2.0.0.14+0nobinonly-0ubuntu0.6.10_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libebook1.2-9_1.8.1-0ubuntu5.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libebook1.2-9_1.8.1-0ubuntu5.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/libnautilus-extension1_2.16.1-0ubuntu3.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/libnautilus-extension1_2.16.1-0ubuntu3.2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/control-center/gnome-control-center_2.16.1-0ubuntu4.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/control-center/gnome-control-center_2.16.1-0ubuntu4.2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/control-center/libgnome-window-settings1_2.16.1-0ubuntu4.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/control-center/libgnome-window-settings1_2.16.1-0ubuntu4.2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/control-center/capplets-data_2.16.1-0ubuntu4.2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/control-center/capplets-data_2.16.1-0ubuntu4.2_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-bsd_1.2.4-2ubuntu3.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-bsd_1.2.4-2ubuntu3.3_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-client_1.2.4-2ubuntu3.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-client_1.2.4-2ubuntu3.3_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/d/dbus/dbus-1-utils_0.93-0ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/d/dbus/dbus-1-utils_0.93-0ubuntu3.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pwlib/libpt-plugins-v4l2_1.10.2.dfsg-0ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pwlib/libpt-plugins-v4l2_1.10.2.dfsg-0ubuntu3.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pwlib/libpt-plugins-v4l_1.10.2.dfsg-0ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pwlib/libpt-plugins-v4l_1.10.2.dfsg-0ubuntu3.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pwlib/libpt-plugins-alsa_1.10.2.dfsg-0ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pwlib/libpt-plugins-alsa_1.10.2.dfsg-0ubuntu3.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pwlib/libpt-1.10.0_1.10.2.dfsg-0ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pwlib/libpt-1.10.0_1.10.2.dfsg-0ubuntu3.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/opal/libopal-2.2.0_2.2.3.dfsg-0ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/opal/libopal-2.2.0_2.2.3.dfsg-0ubuntu2.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libecal1.2-7_1.8.1-0ubuntu5.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libecal1.2-7_1.8.1-0ubuntu5.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-book1.2-2_1.8.1-0ubuntu5.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-book1.2-2_1.8.1-0ubuntu5.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-cal1.2-6_1.8.1-0ubuntu5.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-cal1.2-6_1.8.1-0ubuntu5.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libs/libsoup/libsoup2.2-8_2.2.96-0ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libs/libsoup/libsoup2.2-8_2.2.96-0ubuntu2.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libegroupwise1.2-12_1.8.1-0ubuntu5.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libegroupwise1.2-12_1.8.1-0ubuntu5.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server_1.8.1-0ubuntu5.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server_1.8.1-0ubuntu5.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server-common_1.8.1-0ubuntu5.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server-common_1.8.1-0ubuntu5.1_all.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/ekiga/ekiga_2.0.3-0ubuntu3.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/ekiga/ekiga_2.0.3-0ubuntu3.2_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/tetex-bin/libkpathsea4_3.0-17ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tetex-bin/libkpathsea4_3.0-17ubuntu2.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/evince/evince_0.6.1-0ubuntu1.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/evince/evince_0.6.1-0ubuntu1.2_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserverui1.2-8_1.8.1-0ubuntu5.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserverui1.2-8_1.8.1-0ubuntu5.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libexchange-storage1.2-2_1.8.1-0ubuntu5.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libexchange-storage1.2-2_1.8.1-0ubuntu5.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomeprintui/libgnomeprintui2.2-0_2.12.1-4ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomeprintui/libgnomeprintui2.2-0_2.12.1-4ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomeprintui/libgnomeprintui2.2-common_2.12.1-4ubuntu2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomeprintui/libgnomeprintui2.2-common_2.12.1-4ubuntu2_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/evolution/evolution_2.8.1-0ubuntu4.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/evolution/evolution_2.8.1-0ubuntu4.2_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-plugins_2.8.1-0ubuntu4.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-plugins_2.8.1-0ubuntu4.2_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_2.0.0.14+0nobinonly-0ubuntu0.6.10_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_2.0.0.14+0nobinonly-0ubuntu0.6.10_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_2.0.0.14+0nobinonly-0ubuntu0.6.10_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_2.0.0.14+0nobinonly-0ubuntu0.6.10_i386.deb)
  404 Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/foo2zjs/foo2zjs_20060625dfsg-2ubuntu0.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/foo2zjs/foo2zjs_20060625dfsg-2ubuntu0.1_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gdm/gdm_2.16.1-0ubuntu4.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gdm/gdm_2.16.1-0ubuntu4.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gimp/gimp_2.2.13-1ubuntu3.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gimp/gimp_2.2.13-1ubuntu3.3_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gimp/gimp-data_2.2.13-1ubuntu3.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gimp/gimp-data_2.2.13-1ubuntu3.3_all.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libe/libexif/libexif12_0.6.13-4ubuntu0.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libe/libexif/libexif12_0.6.13-4ubuntu0.2_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gimp/libgimp2.0_2.2.13-1ubuntu3.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gimp/libgimp2.0_2.2.13-1ubuntu3.3_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gimp/gimp-python_2.2.13-1ubuntu3.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gimp/gimp-python_2.2.13-1ubuntu3.3_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libg/libgtop2/libgtop2-common_2.14.4-0ubuntu1.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/libg/libgtop2/libgtop2-common_2.14.4-0ubuntu1.1_all.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libg/libgtop2/libgtop2-7_2.14.4-0ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libg/libgtop2/libgtop2-7_2.14.4-0ubuntu1.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/libpanel-applet2-0_2.16.1-0ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/libpanel-applet2-0_2.16.1-0ubuntu4_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-applets/gnome-applets_2.16.1-0ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-applets/gnome-applets_2.16.1-0ubuntu4_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-applets/gnome-applets-data_2.16.1-0ubuntu4_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-applets/gnome-applets-data_2.16.1-0ubuntu4_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/gnome-panel_2.16.1-0ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/gnome-panel_2.16.1-0ubuntu4_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/gnome-panel-data_2.16.1-0ubuntu4_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/gnome-panel-data_2.16.1-0ubuntu4_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games_2.16.1-0ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games_2.16.1-0ubuntu3_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games-data_2.16.1-0ubuntu3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games-data_2.16.1-0ubuntu3_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-netstatus/gnome-netstatus-applet_2.12.0-5ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-netstatus/gnome-netstatus-applet_2.12.0-5ubuntu7_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.6.9+1.6.9-0ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.6.9+1.6.9-0ubuntu2.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libc/libcdio/libcdio6_0.76-1ubuntu1.6.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libc/libcdio/libcdio6_0.76-1ubuntu1.6.10.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-vfs2/libgnomevfs2-bin_2.16.1-0ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-vfs2/libgnomevfs2-bin_2.16.1-0ubuntu7_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libg/libgsf/libgsf-1-common_1.14.1-2ubuntu1.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/libg/libgsf/libgsf-1-common_1.14.1-2ubuntu1.1_all.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libg/libgsf/libgsf-1-114_1.14.1-2ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libg/libgsf/libgsf-1-114_1.14.1-2ubuntu1.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/j/jasper/libjasper-1.701-1_1.701.0-2ubuntu0.6.10_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/j/jasper/libjasper-1.701-1_1.701.0-2ubuntu0.6.10_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagick9_6.2.4.5.dfsg1-0.10ubuntu0.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagick9_6.2.4.5.dfsg1-0.10ubuntu0.4_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/mono-runtime_1.1.17.1-1ubuntu7.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/mono-runtime_1.1.17.1-1ubuntu7.2_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/mono-gac_1.1.17.1-1ubuntu7.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/mono-gac_1.1.17.1-1ubuntu7.2_all.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/mono-jit_1.1.17.1-1ubuntu7.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/mono-jit_1.1.17.1-1ubuntu7.2_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/mono-common_1.1.17.1-1ubuntu7.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/mono-common_1.1.17.1-1ubuntu7.2_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono0_1.1.17.1-1ubuntu7.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono0_1.1.17.1-1ubuntu7.2_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-corlib1.0-cil_1.1.17.1-1ubuntu7.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-corlib1.0-cil_1.1.17.1-1ubuntu7.2_all.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-cairo1.0-cil_1.1.17.1-1ubuntu7.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-cairo1.0-cil_1.1.17.1-1ubuntu7.2_all.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-system1.0-cil_1.1.17.1-1ubuntu7.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-system1.0-cil_1.1.17.1-1ubuntu7.2_all.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-security1.0-cil_1.1.17.1-1ubuntu7.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-security1.0-cil_1.1.17.1-1ubuntu7.2_all.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-data-tds1.0-cil_1.1.17.1-1ubuntu7.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-data-tds1.0-cil_1.1.17.1-1ubuntu7.2_all.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-sharpzip0.84-cil_1.1.17.1-1ubuntu7.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-sharpzip0.84-cil_1.1.17.1-1ubuntu7.2_all.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-system-data1.0-cil_1.1.17.1-1ubuntu7.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-system-data1.0-cil_1.1.17.1-1ubuntu7.2_all.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-sqlite1.0-cil_1.1.17.1-1ubuntu7.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-sqlite1.0-cil_1.1.17.1-1ubuntu7.2_all.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-system-web1.0-cil_1.1.17.1-1ubuntu7.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-system-web1.0-cil_1.1.17.1-1ubuntu7.2_all.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono1.0-cil_1.1.17.1-1ubuntu7.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono1.0-cil_1.1.17.1-1ubuntu7.2_all.deb)
  404 Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/libtotem-plparser1_2.16.2-0ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/libtotem-plparser1_2.16.2-0ubuntu3_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-utils_2.6.26.dfsg-2ubuntu4.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-utils_2.6.26.dfsg-2ubuntu4.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-image-2.6.17-12-generic_2.6.17.1-12.44_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-image-2.6.17-12-generic_2.6.17.1-12.44_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.17.12.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.17.12.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.17/linux-restricted-modules-common_2.6.17.9-12.4_all.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.17/linux-restricted-modules-common_2.6.17.9-12.4_all.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.17/linux-restricted-modules-2.6.17-12-generic_2.6.17.9-12.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.17/linux-restricted-modules-2.6.17-12-generic_2.6.17.9-12.4_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-restricted-modules-generic_2.6.17.12.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-restricted-modules-generic_2.6.17.12.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-generic_2.6.17.12.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-generic_2.6.17.12.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-headers-2.6.17-10_2.6.17.1-10.34_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-headers-2.6.17-10_2.6.17.1-10.34_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-headers-2.6.17-10-generic_2.6.17.1-10.34_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-headers-2.6.17-10-generic_2.6.17.1-10.34_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-headers-2.6.17-12_2.6.17.1-12.44_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-headers-2.6.17-12_2.6.17.1-12.44_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-headers-2.6.17-12-generic_2.6.17.1-12.44_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-headers-2.6.17-12-generic_2.6.17.1-12.44_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.17.12.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.17.12.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-image-2.6.17-10-generic_2.6.17.1-10.34_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-image-2.6.17-10-generic_2.6.17.1-10.34_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.17/linux-restricted-modules-2.6.17-10-generic_2.6.17.7-10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.17/linux-restricted-modules-2.6.17-10-generic_2.6.17.7-10.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus_2.16.1-0ubuntu3.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus_2.16.1-0ubuntu3.2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus-data_2.16.1-0ubuntu3.2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus-data_2.16.1-0ubuntu3.2_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8b-2ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8b-2ubuntu2.2_i386.deb)
  404 Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-apt/python-apt_0.6.19ubuntu9.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-apt/python-apt_0.6.19ubuntu9.1_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/python-libxml2_2.6.26.dfsg-2ubuntu4.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/python-libxml2_2.6.26.dfsg-2ubuntu4.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/r/rdesktop/rdesktop_1.4.1-1.1ubuntu0.6.10_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/r/rdesktop/rdesktop_1.4.1-1.1ubuntu0.6.10_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.22-1ubuntu4.5_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.22-1ubuntu4.5_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.22-1ubuntu4.5_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.22-1ubuntu4.5_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.3p2-5ubuntu1.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.3p2-5ubuntu1.2_i386.deb)
  404 Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/synaptic/synaptic_0.57.11ubuntu12.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/synaptic/synaptic_0.57.11ubuntu12.1_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-system-tools/gnome-system-tools_2.15.5-0ubuntu6_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-system-tools/gnome-system-tools_2.15.5-0ubuntu6_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/system-tools-backends/system-tools-backends_1.9.7-0ubuntu5_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/system-tools-backends/system-tools-backends_1.9.7-0ubuntu5_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/tomboy/tomboy_0.4.1-0ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tomboy/tomboy_0.4.1-0ubuntu3.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-gstreamer_2.16.2-0ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-gstreamer_2.16.2-0ubuntu3_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem_2.16.2-0ubuntu3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem_2.16.2-0ubuntu3_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-mozilla_2.16.2-0ubuntu3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-mozilla_2.16.2-0ubuntu3_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-docs/ubuntu-docs_6.10.4.2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-docs/ubuntu-docs_6.10.4.2_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/u/unzip/unzip_5.52-8ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/u/unzip/unzip_5.52-8ubuntu1.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.45.2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.45.2_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-notifier/update-notifier_0.43.4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-notifier/update-notifier_0.43.4_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/v/vino/vino_2.16.0-0ubuntu2.4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/v/vino/vino_2.16.0-0ubuntu2.4_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xorg_7.1.1ubuntu6.2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xorg_7.1.1ubuntu6.2_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xscreensaver/xscreensaver-data_4.24-4ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xscreensaver/xscreensaver-data_4.24-4ubuntu2.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xscreensaver/xscreensaver-gl_4.24-4ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xscreensaver/xscreensaver-gl_4.24-4ubuntu2.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/slocate/slocate_3.1-1ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/slocate/slocate_3.1-1ubuntu0.1_i386.deb)
  404 Not Found




Then I found somewhere that said I needed to update the manager itself, and I ran the synoptic and found what I needed, and got this error:


> W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.45.2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.45.2_all.deb)
  404 Not Found [IP: 91.189.88.45 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-manager-core/update-manager-core_0.56~edgy5_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-manager-core/update-manager-core_0.56~edgy5_all.deb)
  404 Not Found [IP: 91.189.88.45 80]

WTF?!?!?!  I have been searching, and can't find any answers.  I have no idea what to do, so if you guys could help, that'd be sweet.

---

### Post by avtolle on 2009-02-25
You are aware that 7.04 has reached its EOL, and that the repositories have moved to the  ubuntu old releases site, correct? My advice is to download and install 8.04 as a clean install without the sequential upgrade process that you will likely not be able to complete.

---

### Post by Dark_Meow1 on 2009-02-25
> **avtolle said:**
> You are aware that 7.04 has reached its EOL, and that the repositories have moved to the  ubuntu old releases site, correct? My advice is to download and install 8.04 as a clean install without the sequential upgrade process that you will likely not be able to complete.

Okay, I didn't realize that.  I knew it was dead, but I didn't know you couldn't download the old updates and such.  Thank you ^.^

---

### Post by memilanuk on 2009-02-25
Is there the same sort of issue going from one LTS release (6.06?) to the next (8.04) to the next(10.0x)?  Are users expected to completely rebuild working servers in order to upgrade?

TIA,

Monte

---

### Post by avtolle on 2009-02-25
> **memilanuk said:**
> Is there the same sort of issue going from one LTS release (6.06?) to the next (8.04) to the next(10.0x)?  Are users expected to completely rebuild working servers in order to upgrade?

TIA,

Monte
No; as I understand it, there is an upgrade path from 6.06 LTS to 8.04 LTS and likely, in the future, from 8.04 LTS to 10.X LTS. See the Upgrade Notes at [www.ubuntu.com](www.ubuntu.com) for information on a "network upgrade" from 6.06 to 8.04 if you are interested.

---

