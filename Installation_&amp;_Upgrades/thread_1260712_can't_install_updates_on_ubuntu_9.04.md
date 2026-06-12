---
title: "can't install updates on ubuntu 9.04"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by haitham1 on 2009-09-07
[SIZE=5]hi

i am a new ubuntu user.  i like the os very much and would like to be able to use it more often.  i encountered a problem however.  i tried to install compiz effects so i went to 


applications-------->add/remove


in the search box in the add/remove window i typed "compiz" and the application "desktop effects, compiz setup" appeared.  i checked the box to it's left and clicked "apply changes".  a summery window then popped up and i had to confirm one more time that i want to "apply" the changes. finally a small window (the header said "downloading package") poped up.  after a while the download failed and i recived the following error message:



[/SIZE]> [I][COLOR=DarkRed]W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtcore4_4.5.0-0ubuntu4.1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtcore4_4.5.0-0ubuntu4.1_i386.deb)
  Could not connect to eg.archive.ubuntu.com:80 (91.189.88.45), connection timed out [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-xml_4.5.0-0ubuntu4.1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-xml_4.5.0-0ubuntu4.1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-dbus_4.5.0-0ubuntu4.1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-dbus_4.5.0-0ubuntu4.1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/n/nas/libaudio2_1.9.1-5_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/n/nas/libaudio2_1.9.1-5_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtgui4_4.5.0-0ubuntu4.1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtgui4_4.5.0-0ubuntu4.1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/p/phonon/libphonon4_4.3.1-0ubuntu3_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/p/phonon/libphonon4_4.3.1-0ubuntu3_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-script_4.5.0-0ubuntu4.1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-script_4.5.0-0ubuntu4.1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-designer_4.5.0-0ubuntu4.1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-designer_4.5.0-0ubuntu4.1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-network_4.5.0-0ubuntu4.1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-network_4.5.0-0ubuntu4.1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-sql_4.5.0-0ubuntu4.1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-sql_4.5.0-0ubuntu4.1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-qt3support_4.5.0-0ubuntu4.1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-qt3support_4.5.0-0ubuntu4.1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-svg_4.5.0-0ubuntu4.1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-svg_4.5.0-0ubuntu4.1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/c/clucene-core/libclucene0ldbl_0.9.20-3_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/c/clucene-core/libclucene0ldbl_0.9.20-3_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/r/raptor/libraptor1_1.4.18-2_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/r/raptor/libraptor1_1.4.18-2_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-common_5.1.30really5.0.75-0ubuntu10.2_all.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-common_5.1.30really5.0.75-0ubuntu10.2_all.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.1.30really5.0.75-0ubuntu10.2_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.1.30really5.0.75-0ubuntu10.2_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/p/postgresql-8.3/libpq5_8.3.7-1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/p/postgresql-8.3/libpq5_8.3.7-1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/r/rasqal/librasqal1_0.9.16-1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/r/rasqal/librasqal1_0.9.16-1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/r/redland/librdf0_1.0.8-1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/r/redland/librdf0_1.0.8-1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/s/soprano/soprano-daemon_2.2.2+dfsg.1-1ubuntu1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/s/soprano/soprano-daemon_2.2.2+dfsg.1-1ubuntu1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/s/soprano/libsoprano4_2.2.2+dfsg.1-1ubuntu1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/s/soprano/libsoprano4_2.2.2+dfsg.1-1ubuntu1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/e/exiv2/libexiv2-5_0.18-1ubuntu1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/e/exiv2/libexiv2-5_0.18-1ubuntu1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/s/strigi/libstreams0_0.6.4-0ubuntu2_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/s/strigi/libstreams0_0.6.4-0ubuntu2_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/s/strigi/libstreamanalyzer0_0.6.4-0ubuntu2_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/s/strigi/libstreamanalyzer0_0.6.4-0ubuntu2_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdelibs5-data_4.2.2-0ubuntu5.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdelibs5-data_4.2.2-0ubuntu5.1_all.deb)
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdelibs5_4.2.2-0ubuntu5.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdelibs5_4.2.2-0ubuntu5.1_i386.deb)
  Unable to connect to security.ubuntu.com http:


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdelibs-bin_4.2.2-0ubuntu5.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdelibs-bin_4.2.2-0ubuntu5.1_i386.deb)
  Unable to connect to security.ubuntu.com http:


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-opengl_4.5.0-0ubuntu4.1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-opengl_4.5.0-0ubuntu4.1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/p/phonon/phonon-backend-gstreamer_4.3.1-0ubuntu3_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/p/phonon/phonon-backend-gstreamer_4.3.1-0ubuntu3_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/p/phonon/phonon_4.3.1-0ubuntu3_all.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/p/phonon/phonon_4.3.1-0ubuntu3_all.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-webkit_4.5.0-0ubuntu4.1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-webkit_4.5.0-0ubuntu4.1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/k/kde4libs/libplasma3_4.2.2-0ubuntu5.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/k/kde4libs/libplasma3_4.2.2-0ubuntu5.1_i386.deb)
  Unable to connect to security.ubuntu.com http:


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-assistant_4.5.0-0ubuntu4.1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-assistant_4.5.0-0ubuntu4.1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-help_4.5.0-0ubuntu4.1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-help_4.5.0-0ubuntu4.1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-sql-mysql_4.5.0-0ubuntu4.1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-sql-mysql_4.5.0-0ubuntu4.1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-test_4.5.0-0ubuntu4.1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-test_4.5.0-0ubuntu4.1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-xmlpatterns_4.5.0-0ubuntu4.1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-xmlpatterns_4.5.0-0ubuntu4.1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/qt4-qtconfig_4.5.0-0ubuntu4.1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/qt4-qtconfig_4.5.0-0ubuntu4.1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/s/sip4-qt3/python-sip4_4.7.9-1ubuntu1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/s/sip4-qt3/python-sip4_4.7.9-1ubuntu1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/p/python-qt4/python-qt4-common_4.4.4-2ubuntu6_all.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/p/python-qt4/python-qt4-common_4.4.4-2ubuntu6_all.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/p/python-qt4/python-qt4_4.4.4-2ubuntu6_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/p/python-qt4/python-qt4_4.4.4-2ubuntu6_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libm/libmodplug/libmodplug0c2_0.8.4-3ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libm/libmodplug/libmodplug0c2_0.8.4-3ubuntu1.1_i386.deb)
  Unable to connect to security.ubuntu.com http:


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/libm/libmpcdec/libmpcdec3_1.2.2-1build1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/libm/libmpcdec/libmpcdec3_1.2.2-1build1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-bin_1.1.16.3-0ubuntu1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-bin_1.1.16.3-0ubuntu1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-misc-plugins_1.1.16.3-0ubuntu1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-misc-plugins_1.1.16.3-0ubuntu1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-shape0_1.1.93-0ubuntu3.1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-shape0_1.1.93-0ubuntu3.1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-shm0_1.1.93-0ubuntu3.1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-shm0_1.1.93-0ubuntu3.1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-xv0_1.1.93-0ubuntu3.1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-xv0_1.1.93-0ubuntu3.1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-x_1.1.16.3-0ubuntu1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-x_1.1.16.3-0ubuntu1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-console_1.1.16.3-0ubuntu1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-console_1.1.16.3-0ubuntu1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1_1.1.16.3-0ubuntu1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1_1.1.16.3-0ubuntu1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-runtime/kdebase-runtime-bin-kde4_4.2.2-0ubuntu1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-runtime/kdebase-runtime-bin-kde4_4.2.2-0ubuntu1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-runtime/kdebase-runtime-data-common_4.2.2-0ubuntu1_all.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-runtime/kdebase-runtime-data-common_4.2.2-0ubuntu1_all.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-runtime/kdebase-runtime-data_4.2.2-0ubuntu1_all.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-runtime/kdebase-runtime-data_4.2.2-0ubuntu1_all.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-runtime/kde-icons-oxygen_4.2.2-0ubuntu1_all.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-runtime/kde-icons-oxygen_4.2.2-0ubuntu1_all.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-runtime/kdebase-runtime_4.2.2-0ubuntu1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-runtime/kdebase-runtime_4.2.2-0ubuntu1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/k/kdesudo/kdesudo_3.4.1-0ubuntu1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/k/kdesudo/kdesudo_3.4.1-0ubuntu1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/b/boost1.35/libboost-program-options1.35.0_1.35.0-8ubuntu5_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/b/boost1.35/libboost-program-options1.35.0_1.35.0-8ubuntu5_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/a/akonadi/libakonadiprivate1_1.1.1-0ubuntu3_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/a/akonadi/libakonadiprivate1_1.1.1-0ubuntu3_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/k/kdepimlibs/kdepimlibs-data_4.2.2-0ubuntu1_all.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/k/kdepimlibs/kdepimlibs-data_4.2.2-0ubuntu1_all.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/k/kdepimlibs/kdepimlibs5_4.2.2-0ubuntu1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/k/kdepimlibs/kdepimlibs5_4.2.2-0ubuntu1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/k/kdebindings/python-kde4_4.2.2-0ubuntu2_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/k/kdebindings/python-kde4_4.2.2-0ubuntu2_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/g/gdebi/gdebi-kde_0.4.9_all.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/g/gdebi/gdebi-kde_0.4.9_all.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/i/install-package/install-package_0.3.1_all.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/i/install-package/install-package_0.3.1_all.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/d/desktop-effects-kde/desktop-effects-kde_0.4.4.1_all.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/d/desktop-effects-kde/desktop-effects-kde_0.4.4.1_all.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/e/exiv2/exiv2_0.18-1ubuntu1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/e/exiv2/exiv2_0.18-1ubuntu1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-runtime/khelpcenter4_4.2.2-0ubuntu1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-runtime/khelpcenter4_4.2.2-0ubuntu1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/r/raptor/raptor-utils_1.4.18-2_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/r/raptor/raptor-utils_1.4.18-2_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/r/redland/redland-utils_1.0.8-1_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/r/redland/redland-utils_1.0.8-1_i386.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/t/ttf-dejavu/ttf-dejavu-extra_2.28-1_all.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/t/ttf-dejavu/ttf-dejavu-extra_2.28-1_all.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]


W: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/t/ttf-dejavu/ttf-dejavu_2.28-1_all.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/t/ttf-dejavu/ttf-dejavu_2.28-1_all.deb)
  Unable to connect to eg.archive.ubuntu.com http: [IP: 91.189.88.45 80]
[/COLOR][/I]                                                                                                                                             
[SIZE=5] 




this took place several times.  i also noticed that i can not download and install the updates that i get from the update manager.  i suppose both events take place for the same reason.  i am not sure though.  

my ubuntu is 9.04

thanx in advance for your time and hope it all works out.  


[/SIZE]

---

### Post by haitham1 on 2009-09-07
[SIZE=5]It seems like i can not install plug ins also.  [/SIZE]

---

### Post by privatejarhead on 2009-09-08
first off, please use a normal font...like 12 perhaps....

as for the updating, i don't understand why ubuntu couldn't find the packages. have you checked your internet connection to see if it's running properly?

---

### Post by ymazlumyan on 2009-09-08
I agree to privatejarhead. The only reason why it couldn't find could be your internet connection. Check and see if you have one and if it's configured correctly. And try using Synaptic. It's better than just Add/Remove.

---

### Post by haitham1 on 2009-09-08
[SIZE=3]Oh i am really sorry about the font.  

my internet is working just fine.  i am using it right now to write this.  i opened the synaptic package manager from:

system------>administration------>synaptic

but i don't know how to use it.  

please bare with me since i am new to all this.

thank you [/SIZE]

---

### Post by haitham1 on 2009-09-08
[SIZE=4]i also am not able to install the extra effects manager.[/SIZE]

---

### Post by haitham1 on 2009-09-08
[SIZE=3]Ok guys.  First of I would like to thank both of you for your efforts to help out with my case.  

I not an expert but i felt this was not a problem with the operating system, but then what do i know.  i tried everything possible for two days and finally i got it to work.  it was simple actually. 

system>administration>synaptic package manager

in the "*synaptic package manager*" window choose "settings" from the options at the top of the window and then pick "*repositories*" from the drop down menu. A "*software sources*" window will appear.  In that window and from the "*Ubuntu software*" tab change the download option to "*main server*".


This actually did the trick for me.  


Cheers again   [/SIZE]

---

