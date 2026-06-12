---
title: "Firefox (2.0.0.1) crashes, Java App"
date: 2007-02-03
forum: Hardware &amp; Laptops
---

### Post by HilliBilly on 2007-02-03
hi,

need your help. the firefox (2.0.0.1) on my edgy (gnome) laptop crashes when i try to open a website which uses a java app with a public/private key set. to get the website loading the applet i installed a mozilla add-on (user agent) where i have to switch to internet explorer.

java ( sun 1.5.0_08 ) and its firefox plugin itself are working perfect. tested it with [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

any ideas what i could do/try?


**vi /var/crash/_usr_lib_firefox_firefox-bin.1000.crash**

ProblemType: Crash
CrashCounter: 1
Date: Sat Feb  3 13:52:50 2007
ExecutablePath: /usr/lib/firefox/firefox-bin
ProcCmdline: /usr/lib/firefox/firefox-bin
ProcCwd: /home/xyz
ProcEnviron:
 SHELL=/bin/bash
 PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
 LANG=en_AU.UTF-8
 LANGUAGE=en_AU:en
ProcMaps:
 08048000-0805a000 r-xp 00000000 03:02 831824     /usr/lib/firefox/firefox-bin
 0805a000-0805c000 rw-p 00011000 03:02 831824     /usr/lib/firefox/firefox-bin
 0805c000-08bbd000 rw-p 0805c000 00:00 0          [heap]
 ace00000-ace95000 rw-p ace00000 00:00 0 
 ace95000-acf00000 ---p ace95000 00:00 0 
 acfdd000-acff9000 r-xp 00000000 03:02 862160     /usr/lib/X11/locale/common/ximcp.so.2.0.0
 acff9000-acffb000 rw-p 0001b000 03:02 862160     /usr/lib/X11/locale/common/ximcp.so.2.0.0
 acffb000-acffc000 ---p acffb000 00:00 0 
 acffc000-ad7fc000 rwxp acffc000 00:00 0 
 ad7fc000-ad8ac000 r-xp 00000000 03:02 813233     /usr/lib/libstdc++.so.5.0.7
 ad8ac000-ad8b1000 rw-p 000af000 03:02 813233     /usr/lib/libstdc++.so.5.0.7
 ad8b1000-ad8b6000 rw-p ad8b1000 00:00 0 
 ad8b6000-ada5c000 r-xp 00000000 03:02 1139612    /usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so
 ada5c000-ada7c000 rw-p 001a6000 03:02 1139612    /usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so
 ada7c000-adbe2000 rw-p ada7c000 00:00 0 
 adbe2000-aea82000 ---p adbe2000 00:00 0 
 aea82000-af0ed000 r-xp 00000000 03:02 845362     /usr/lib/firefox/plugins/libflashplayer.so
 af0ed000-af136000 rw-p 0066b000 03:02 845362     /usr/lib/firefox/plugins/libflashplayer.so
 af136000-af2f5000 rw-p af136000 00:00 0 
 af2f5000-af300000 ---p af2f5000 00:00 0 
 af311000-af31a000 r-xp 00000000 03:02 862165     /usr/lib/X11/locale/common/xomGeneric.so.2.0.0
 af31a000-af31b000 rw-p 00008000 03:02 862165     /usr/lib/X11/locale/common/xomGeneric.so.2.0.0
 af31b000-af348000 r-xp 00000000 03:02 930057     /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libjavaplugin_nscp.so
 af348000-af34e000 rw-p 0002d000 03:02 930057     /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libjavaplugin_nscp.so
 af34e000-af364000 r-xp 00000000 03:02 975911     /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/plugin/i386/ns7/libjavaplugin_oji.so
 af364000-af368000 rw-p 00015000 03:02 975911     /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/plugin/i386/ns7/libjavaplugin_oji.so
 af368000-af371000 r-xp 00000000 03:02 1139968    /home/xyz/Desktop/RealPlayer/mozilla/nphelix.so
 af371000-af372000 rw-p 00008000 03:02 1139968    /home/xyz/Desktop/RealPlayer/mozilla/nphelix.so
 af372000-af379000 r-xp 00000000 03:02 832879     /usr/lib/totem/libtotem-narrowspace-plugin.so
 af379000-af37a000 rw-p 00006000 03:02 832879     /usr/lib/totem/libtotem-narrowspace-plugin.so
 af37a000-af381000 r-xp 00000000 03:02 832878     /usr/lib/totem/libtotem-mully-plugin.so
 af381000-af382000 rw-p 00006000 03:02 832878     /usr/lib/totem/libtotem-mully-plugin.so
 af382000-af389000 r-xp 00000000 03:02 832877     /usr/lib/totem/libtotem-gmp-plugin.so
 af389000-af38a000 rw-p 00006000 03:02 832877     /usr/lib/totem/libtotem-gmp-plugin.so
 af38a000-af3b3000 r-xp 00000000 03:02 845554     /usr/lib/firefox/components/libgkplugin.so
 af3b3000-af3b5000 rw-p 00028000 03:02 845554     /usr/lib/firefox/components/libgkplugin.so
 af3b5000-af3b6000 ---p af3b5000 00:00 0 
 af3b6000-afbb6000 rwxp af3b6000 00:00 0 
 afbb6000-afbed000 r-xp 00000000 03:02 585230     /usr/lib/firefox/libnssckbi.so
 afbed000-afbf6000 rw-p 00037000 03:02 585230     /usr/lib/firefox/libnssckbi.so
 afbf6000-afc35000 r-xp 00000000 03:02 815044     /usr/lib/libfreebl3.so
 afc35000-afc36000 rw-p 0003f000 03:02 815044     /usr/lib/libfreebl3.so
 afc36000-afc37000 ---p afc36000 00:00 0 
 afc37000-b0437000 rwxp afc37000 00:00 0 
 b0437000-b0482000 r-xp 00000000 03:02 815042     /usr/lib/libsoftokn3.so
 b0482000-b0486000 rw-p 0004b000 03:02 815042     /usr/lib/libsoftokn3.so
 b0486000-b04f2000 r-xp 00000000 03:02 813048     /usr/lib/libnss3.so
 b04f2000-b04f7000 rw-p 0006c000 03:02 813048     /usr/lib/libnss3.so
 b04f7000-b051f000 r-xp 00000000 03:02 815043     /usr/lib/libssl3.so
 b051f000-b0521000 rw-p 00027000 03:02 815043     /usr/lib/libssl3.so
 b0521000-b0542000 r-xp 00000000 03:02 813050     /usr/lib/libsmime3.so
 b0542000-b0544000 rw-p 00021000 03:02 813050     /usr/lib/libsmime3.so
 b0547000-b054e000 r-xp 00000000 03:02 832875     /usr/lib/totem/libtotem-basic-plugin.so
 b054e000-b054f000 rw-p 00006000 03:02 832875     /usr/lib/totem/libtotem-basic-plugin.so
 b054f000-b05aa000 r-xp 00000000 03:02 845694     /usr/lib/firefox/components/libpipnss.so
 b05aa000-b05ae000 rw-p 0005a000 03:02 845694     /usr/lib/firefox/components/libpipnss.so
 b05ae000-b05cf000 rw-p b05ae000 00:00 0 
 b05cf000-b0602000 r-xp 00000000 03:02 845501     /usr/lib/firefox/components/libmork.so
 b0602000-b0605000 rw-p 00032000 03:02 845501     /usr/lib/firefox/components/libmork.so
 b0605000-b0606000 ---p b0605000 00:00 0 
 b0606000-b0e06000 rwxp b0606000 00:00 0 
 b0e06000-b0e07000 ---p b0e06000 00:00 0 
 b0e07000-b1607000 rwxp b0e07000 00:00 0 
 b1607000-b1608000 ---p b1607000 00:00 0 
 b1608000-b1e08000 rwxp b1608000 00:00 0 
 b1e08000-b1e5f000 r-xp 00000000 03:02 845503     /usr/lib/firefox/components/libstoragecomps.so
 b1e5f000-b1e61000 rw-p 00056000 03:02 845503     /usr/lib/firefox/components/libstoragecomps.so
 b1e61000-b1efb000 r-xp 00000000 03:02 845633     /usr/lib/firefox/components/libeditor.so
 b1efb000-b1eff000 rw-p 0009a000 03:02 845633     /usr/lib/firefox/components/libeditor.so
 b1eff000-b2000000 rw-p b1eff000 00:00 0 
 b2007000-b200b000 r-xp 00000000 03:02 601499     /lib/tls/i686/cmov/libnss_dns-2.4.so
 b200b000-b200d000 rw-p 00003000 03:02 601499     /lib/tls/i686/cmov/libnss_dns-2.4.so
 b2010000-b2012000 r-xp 00000000 03:02 81281      /usr/lib/firefox/plugins/libunixprintplugin.so
 b2012000-b2013000 rw-p 00001000 03:02 81281      /usr/lib/firefox/plugins/libunixprintplugin.so
 b2013000-b2017000 r-xp 00000000 03:02 845367     /usr/lib/firefox/components/libmozgnome.so
 b2017000-b2018000 rw-p 00003000 03:02 845367     /usr/lib/firefox/components/libmozgnome.so
 b2018000-b2022000 r-xp 00000000 03:02 845522     /usr/lib/firefox/components/libnecko2.so
 b2022000-b2023000 rw-p 0000a000 03:02 845522     /usr/lib/firefox/components/libnecko2.so
 b2023000-b2036000 r-xp 00000000 03:02 845637     /usr/lib/firefox/components/libcomposer.so
 b2036000-b2038000 rw-p 00012000 03:02 845637     /usr/lib/firefox/components/libcomposer.so
 b2038000-b2048000 r-xp 00000000 03:02 845715     /usr/lib/firefox/components/libspellchecker.so
 b2048000-b2049000 rw-p 0000f000 03:02 845715     /usr/lib/firefox/components/libspellchecker.so
 b2049000-b204e000 r-xp 00000000 03:02 845634     /usr/lib/firefox/components/libtxmgr.so
 b204e000-b204f000 rw-p 00004000 03:02 845634     /usr/lib/firefox/components/libtxmgr.so
 b204f000-b2052000 r-xp 00000000 03:02 845659     /usr/lib/firefox/components/libremoteservice.so
 b2052000-b2053000 rw-p 00002000 03:02 845659     /usr/lib/firefox/components/libremoteservice.so
 b2053000-b2083000 rw-s 00000000 00:07 1376269    /SYSV00000000 (deleted)
 b2083000-b20b6000 r--p 00000000 03:02 992558     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSerif.ttf
 b20b6000-b20b7000 ---p b20b6000 00:00 0 
 b20b7000-b28b7000 rwxp b20b7000 00:00 0 
 b28b7000-b28b8000 ---p b28b7000 00:00 0 
 b28b8000-b30b8000 rwxp b28b8000 00:00 0 
 b30b8000-b30b9000 ---p b30b8000 00:00 0 
 b30b9000-b38b9000 rwxp b30b9000 00:00 0 
 b38b9000-b38bd000 r-xp 00000000 03:02 861659     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
 b38bd000-b38be000 rw-p 00003000 03:02 861659     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
 b38bf000-b3d95000 r--p 00000000 03:02 1056902    /usr/share/icons/hicolor/icon-theme.cache
 b3d95000-b43f1000 r--p 00000000 03:02 1058463    /usr/share/icons/gnome/icon-theme.cache
 b43f1000-b4649000 r--p 00000000 03:02 1058464    /usr/share/icons/Tango/icon-theme.cache
 b4649000-b469a000 r--p 00000000 03:02 1056897    /usr/share/icons/Tangerine/icon-theme.cache
 b469a000-b470b000 r--p 00000000 03:02 992541     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
 b470b000-b4777000 r--p 00000000 03:02 991620     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
 b4777000-b4782000 r-xp 00000000 03:02 814060     /usr/lib/libgnome-keyring.so.0.0.1
 b4782000-b4783000 rw-p 0000a000 03:02 814060     /usr/lib/libgnome-keyring.so.0.0.1
 b4783000-b4797000 r-xp 00000000 03:02 814101     /usr/lib/libart_lgpl_2.so.2.3.17
 b4797000-b4798000 rw-p 00013000 03:02 814101     /usr/lib/libart_lgpl_2.so.2.3.17
 b4798000-b47c0000 r-xp 00000000 03:02 814324     /usr/lib/libgnomecanvas-2.so.0.1400.0
 b47c0000-b47c1000 rw-p 00027000 03:02 814324     /usr/lib/libgnomecanvas-2.so.0.1400.0
 b47c1000-b481b000 r-xp 00000000 03:02 814141     /usr/lib/libbonoboui-2.so.0.0.0
 b481b000-b481e000 rw-p 0005a000 03:02 814141     /usr/lib/libbonoboui-2.so.0.0.0
 b481e000-b48a3000 r-xp 00000000 03:02 814502     /usr/lib/libgnomeui-2.so.0.1600.1
 b48a3000-b48a7000 rw-p 00084000 03:02 814502     /usr/lib/libgnomeui-2.so.0.1600.1
 b48a7000-b48ae000 r--p 00000000 03:02 1040921    /usr/share/icons/Human/icon-theme.cache
 b48ae000-b48b2000 r--p 00000000 03:02 1106938    /usr/share/locale-langpack/en_AU/LC_MESSAGES/glib20.mo
 b48b2000-b48b9000 r-xp 00000000 03:02 845473     /usr/lib/firefox/components/libimgicon.so
 b48b9000-b48ba000 rw-p 00007000 03:02 845473     /usr/lib/firefox/components/libimgicon.so
 b48ba000-b4913000 r-xp 00000000 03:02 845536     /usr/lib/firefox/components/libhtmlpars.so
 b4913000-b491b000 rw-p 00059000 03:02 845536     /usr/lib/firefox/components/libhtmlpars.so
 b491b000-b49d9000 r-xp 00000000 03:02 845494     /usr/lib/firefox/components/libuconv.so
 b49d9000-b49df000 rw-p 000bd000 03:02 845494     /usr/lib/firefox/components/libuconv.so
 b49df000-b49ea000 rw-p b49df000 00:00 0 
 b49ea000-b4a00000 r-xp 00000000 03:02 831818     /usr/lib/firefox/libjsj.so
 b4a00000-b4a01000 rw-p 00016000 03:02 831818     /usr/lib/firefox/libjsj.so
 b4a01000-b4a15000 r-xp 00000000 03:02 845641     /usr/lib/firefox/components/liboji.so
 b4a15000-b4a16000 rw-p 00014000 03:02 845641     /usr/lib/firefox/components/liboji.so
 b4a16000-b4a1d000 r-xp 00000000 03:02 845693     /usr/lib/firefox/components/libpipboot.so
 b4a1d000-b4a1e000 rw-p 00006000 03:02 845693     /usr/lib/firefox/components/libpipboot.so
 b4a1e000-b4a1f000 ---p b4a1e000 00:00 0 
 b4a1f000-b521f000 rwxp b4a1f000 00:00 0 
 b521f000-b5227000 r-xp 00000000 03:02 845698     /usr/lib/firefox/components/libcookie.so
 b5227000-b5228000 rw-p 00008000 03:02 845698     /usr/lib/firefox/components/libcookie.so
 b5228000-b523a000 r-xp 00000000 03:02 845630     /usr/lib/firefox/components/libwebbrwsr.so
 b523a000-b523c000 rw-p 00011000 03:02 845630     /usr/lib/firefox/components/libwebbrwsr.so
 b523c000-b526e000 r-xp 00000000 03:02 569010     /lib/libsepol.so.1
 b526e000-b526f000 rw-p 00031000 03:02 569010     /lib/libsepol.so.1
 b526f000-b5279000 rw-p b526f000 00:00 0 
 b5279000-b527c000 r-xp 00000000 03:02 668473     /usr/lib/libgpg-error.so.0.2.0
 b527c000-b527d000 rw-p 00002000 03:02 668473     /usr/lib/libgpg-error.so.0.2.0
 b527d000-b52c9000 r-xp 00000000 03:02 668540     /usr/lib/libgcrypt.so.11.2.1
 b52c9000-b52cb000 rw-p 0004b000 03:02 668540     /usr/lib/libgcrypt.so.11.2.1
 b52cb000-b52dd000 r-xp 00000000 03:02 669441     /usr/lib/libtasn1.so.3.0.5
 b52dd000-b52de000 rw-p 00011000 03:02 669441     /usr/lib/libtasn1.so.3.0.5
 b52de000-b5391000 r-xp 00000000 03:02 813151     /usr/lib/libasound.so.2.0.0
 b5391000-b5396000 rw-p 000b2000 03:02 813151     /usr/lib/libasound.so.2.0.0
 b5396000-b53a8000 r-xp 00000000 03:02 569387     /lib/libselinux.so.1
 b53a8000-b53aa000 rw-p 00011000 03:02 569387     /lib/libselinux.so.1
 b53aa000-b53b9000 r-xp 00000000 03:02 601506     /lib/tls/i686/cmov/libresolv-2.4.so
 b53b9000-b53bb000 rw-p 0000f000 03:02 601506     /lib/tls/i686/cmov/libresolv-2.4.so
 b53bb000-b53bd000 rw-p b53bb000 00:00 0 
 b53bd000-b53cb000 r-xp 00000000 03:02 668241     /usr/lib/libavahi-client.so.3.2.0
 b53cb000-b53cc000 rw-p 0000e000 03:02 668241     /usr/lib/libavahi-client.so.3.2.0
 b53cc000-b53d6000 r-xp 00000000 03:02 668044     /usr/lib/libavahi-common.so.3.4.2
 b53d6000-b53d7000 rw-p 00009000 03:02 668044     /usr/lib/libavahi-common.so.3.4.2
 b53d7000-b5440000 r-xp 00000000 03:02 669466     /usr/lib/libgnutls.so.13.0.5
 b5440000-b5446000 rw-p 00068000 03:02 669466     /usr/lib/libgnutls.so.13.0.5
 b5446000-b5475000 r-xp 00000000 03:02 813169     /usr/lib/libdbus-1.so.3.0.0
 b5475000-b5476000 rw-p 0002f000 03:02 813169     /usr/lib/libdbus-1.so.3.0.0
 b5476000-b5490000 r-xp 00000000 03:02 814428     /usr/lib/libdbus-glib-1.so.2.0.0
 b5490000-b5491000 rw-p 00019000 03:02 814428     /usr/lib/libdbus-glib-1.so.2.0.0
 b5491000-b55a4000 r-xp 00000000 03:02 812829     /usr/lib/libxml2.so.2.6.26
 b55a4000-b55a9000 rw-p 00113000 03:02 812829     /usr/lib/libxml2.so.2.6.26
 b55a9000-b55aa000 rw-p b55a9000 00:00 0 
 b55aa000-b55b0000 r-xp 00000000 03:02 569078     /lib/libpopt.so.0.0.0
 b55b0000-b55b1000 rw-p 00006000 03:02 569078     /lib/libpopt.so.0.0.0
 b55b1000-b55cf000 r-xp 00000000 03:02 814118     /usr/lib/libaudiofile.so.0.0.2
 b55cf000-b55d1000 rw-p 0001e000 03:02 814118     /usr/lib/libaudiofile.so.0.0.2
 b55d1000-b55da000 r-xp 00000000 03:02 814211     /usr/lib/libesd.so.0.2.36
 b55da000-b55db000 rw-p 00008000 03:02 814211     /usr/lib/libesd.so.0.2.36
 b55db000-b55ed000 r-xp 00000000 03:02 814025     /usr/lib/libbonobo-activation.so.4.0.0
 b55ed000-b55ef000 rw-p 00012000 03:02 814025     /usr/lib/libbonobo-activation.so.4.0.0
 b55ef000-b563f000 r-xp 00000000 03:02 814024     /usr/lib/libbonobo-2.so.0.0.0
 b563f000-b5649000 rw-p 0004f000 03:02 814024     /usr/lib/libbonobo-2.so.0.0.0
 b5649000-b569e000 r-xp 00000000 03:02 814613     /usr/lib/libgnomevfs-2.so.0.1600.1
 b569e000-b56a1000 rw-p 00054000 03:02 814613     /usr/lib/libgnomevfs-2.so.0.1600.1
 b56a1000-b56b5000 r-xp 00000000 03:02 814842     /usr/lib/libgnome-2.so.0.1600.0
 b56b5000-b56b6000 rw-p 00013000 03:02 814842     /usr/lib/libgnome-2.so.0.1600.0
 b56b7000-b56ba000 r-xp 00000000 03:02 845714     /usr/lib/firefox/components/libpermissions.so
 b56ba000-b56bb000 rw-p 00002000 03:02 845714     /usr/lib/firefox/components/libpermissions.so
 b56bb000-b56c1000 r--p 00000000 03:02 1106939    /usr/share/locale-langpack/en_AU/LC_MESSAGES/libgnome-2.0.mo
 b56c1000-b5721000 rw-s 00000000 00:07 1343500    /SYSV00000000 (deleted)
 b5721000-b5732000 r-xp 00000000 03:02 812986     /usr/lib/libXft.so.2.1.2
 b5732000-b5733000 rw-p 00010000 03:02 812986     /usr/lib/libXft.so.2.1.2
 b5733000-b5739000 r-xp 00000000 03:02 814798     /usr/lib/libpangoxft-1.0.so.0.1400.5
 b5739000-b573a000 rw-p 00005000 03:02 814798     /usr/lib/libpangoxft-1.0.so.0.1400.5
 b573a000-b573d000 r-xp 00000000 03:02 814950     /usr/lib/libORBitCosNaming-2.so.0.1.0
 b573d000-b573e000 rw-p 00003000 03:02 814950     /usr/lib/libORBitCosNaming-2.so.0.1.0
 b573e000-b5744000 r-xp 00000000 03:02 861665     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
 b5744000-b5745000 rw-p 00005000 03:02 861665     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
 b5745000-b577e000 r-xp 00000000 03:02 845550     /usr/lib/firefox/components/libgfx_gtk.so
 b577e000-b5781000 rw-p 00038000 03:02 845550     /usr/lib/firefox/components/libgfx_gtk.so
 b5781000-b579f000 r-xp 00000000 03:02 814845     /usr/lib/libjpeg.so.62.0.0
 b579f000-b57a0000 rw-p 0001d000 03:02 814845     /usr/lib/libjpeg.so.62.0.0
 b57a0000-b57b8000 r-xp 00000000 03:02 845552     /usr/lib/firefox/components/libimglib2.so
 b57b8000-b57ba000 rw-p 00017000 03:02 845552     /usr/lib/firefox/components/libimglib2.so
 b57ba000-b5cf8000 r-xp 00000000 03:02 845614     /usr/lib/firefox/components/libgklayout.so
 b5cf8000-b5d58000 rw-p 0053e000 03:02 845614     /usr/lib/firefox/components/libgklayout.so
 b5d58000-b5d5f000 rw-p b5d58000 00:00 0 
 b5d5f000-b5da6000 r-xp 00000000 03:02 814015     /usr/lib/libORBit-2.so.0.1.0
 b5da6000-b5db0000 rw-p 00046000 03:02 814015     /usr/lib/libORBit-2.so.0.1.0
 b5db0000-b5dde000 r-xp 00000000 03:02 813385     /usr/lib/libgconf-2.so.4.1.0
 b5dde000-b5de1000 rw-p 0002e000 03:02 813385     /usr/lib/libgconf-2.so.4.1.0
 b5de2000-b5de3000 rw-p b5de2000 00:00 0 
 b5de3000-b5de5000 r-xp 00000000 03:02 601510     /lib/tls/i686/cmov/libutil-2.4.so
 b5de5000-b5de7000 rw-p 00001000 03:02 601510     /lib/tls/i686/cmov/libutil-2.4.so
 b5de7000-b5deb000 r-xp 00000000 03:02 845678     /usr/lib/firefox/components/libcommandlines.so
 b5deb000-b5dec000 rw-p 00003000 03:02 845678     /usr/lib/firefox/components/libcommandlines.so
 b5dec000-b5e02000 r-xp 00000000 03:02 845639     /usr/lib/firefox/components/libnsappshell.so
 b5e02000-b5e04000 rw-p 00015000 03:02 845639     /usr/lib/firefox/components/libnsappshell.so
 b5e04000-b5e18000 r-xp 00000000 03:02 845655     /usr/lib/firefox/components/libappcomps.so
 b5e18000-b5e19000 rw-p 00014000 03:02 845655     /usr/lib/firefox/components/libappcomps.so
 b5e19000-b5e66000 r-xp 00000000 03:02 845617     /usr/lib/firefox/components/libdocshell.so
 b5e66000-b5e6a000 rw-p 0004d000 03:02 845617     /usr/lib/firefox/components/libdocshell.so
 b5e6a000-b5e91000 r-xp 00000000 03:02 845533     /usr/lib/firefox/components/librdf.so
 b5e91000-b5e93000 rw-p 00027000 03:02 845533     /usr/lib/firefox/components/librdf.so
 b5e93000-b5e94000 ---p b5e93000 00:00 0 
 b5e94000-b6694000 rwxp b5e94000 00:00 0 
 b6694000-b66a7000 r-xp 00000000 03:02 845531     /usr/lib/firefox/components/libcaps.so
 b66a7000-b66a8000 rw-p 00013000 03:02 845531     /usr/lib/firefox/components/libcaps.so
 b66a8000-b66d3000 r-xp 00000000 03:02 845628     /usr/lib/firefox/components/libembedcomponents.so
 b66d3000-b66d5000 rw-p 0002b000 03:02 845628     /usr/lib/firefox/components/libembedcomponents.so
 b66d5000-b671a000 r-xp 00000000 03:02 845681     /usr/lib/firefox/components/libtoolkitcomps.so
 b671a000-b671d000 rw-p 00045000 03:02 845681     /usr/lib/firefox/components/libtoolkitcomps.so
 b671d000-b672e000 r-xp 00000000 03:02 864839     /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
 b672e000-b672f000 rw-p 00011000 03:02 864839     /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
 b672f000-b6744000 r-xp 00000000 03:02 813396     /usr/lib/libICE.so.6.3.0
 b6744000-b6745000 rw-p 00014000 03:02 813396     /usr/lib/libICE.so.6.3.0
 b6745000-b6747000 rw-p b6745000 00:00 0 
 b6747000-b674f000 r-xp 00000000 03:02 813436     /usr/lib/libSM.so.6.0.0
 b674f000-b6750000 rw-p 00007000 03:02 813436     /usr/lib/libSM.so.6.0.0
 b6750000-b679a000 r-xp 00000000 03:02 812818     /usr/lib/libXt.so.6.0.0
 b679a000-b679e000 rw-p 00049000 03:02 812818     /usr/lib/libXt.so.6.0.0
 b679e000-b67a2000 r-xp 00000000 03:02 814238     /usr/lib/libgthread-2.0.so.0.1200.4
 b67a2000-b67a3000 rw-p 00003000 03:02 814238     /usr/lib/libgthread-2.0.so.0.1200.4
 b67a3000-b67a8000 r-xp 00000000 03:02 845706     /usr/lib/firefox/components/libsystem-pref.so
 b67a8000-b67a9000 rw-p 00004000 03:02 845706     /usr/lib/firefox/components/libsystem-pref.so
 b67a9000-b67ac000 r-xp 00000000 03:02 831817     /usr/lib/firefox/libgtkxtbin.so
 b67ac000-b67ad000 rw-p 00003000 03:02 831817     /usr/lib/firefox/libgtkxtbin.so
 b67ad000-b67d9000 r-xp 00000000 03:02 845599     /usr/lib/firefox/components/libwidget_gtk2.so
 b67d9000-b67dd000 rw-p 0002b000 03:02 845599     /usr/lib/firefox/components/libwidget_gtk2.so
 b67dd000-b67ee000 r-xp 00000000 03:02 845523     /usr/lib/firefox/components/libjar50.so
 b67ee000-b67f0000 rw-p 00010000 03:02 845523     /usr/lib/firefox/components/libjar50.so
 b67f0000-b683c000 r-xp 00000000 03:02 845491     /usr/lib/firefox/components/libxpconnect.so
 b683c000-b6840000 rw-p 0004c000 03:02 845491     /usr/lib/firefox/components/libxpconnect.so
 b6840000-b6841000 ---p b6840000 00:00 0 
 b6841000-b7041000 rwxp b6841000 00:00 0 
 b7041000-b7059000 r-xp 00000000 03:02 831821     /usr/lib/firefox/libxpcom_compat.so
 b7059000-b705b000 rw-p 00017000 03:02 831821     /usr/lib/firefox/libxpcom_compat.so
 b705b000-b7078000 r-xp 00000000 03:02 830782     /usr/lib/firefox/libgkgfx.so
 b7078000-b707a000 rw-p 0001c000 03:02 830782     /usr/lib/firefox/libgkgfx.so
 b707a000-b70b4000 r-xp 00000000 03:02 48783      /usr/lib/firefox/components/libbrowsercomps.so
 b70b4000-b70b7000 rw-p 00039000 03:02 48783      /usr/lib/firefox/components/libbrowsercomps.so
 b70b7000-b70ee000 r-xp 00000000 03:02 845500     /usr/lib/firefox/components/libi18n.so
 b70ee000-b70f1000 rw-p 00036000 03:02 845500     /usr/lib/firefox/components/libi18n.so
 b70f1000-b71b3000 r-xp 00000000 03:02 845521     /usr/lib/firefox/components/libnecko.so
 b71b3000-b71bb000 rw-p 000c2000 03:02 845521     /usr/lib/firefox/components/libnecko.so
 b71bb000-b71ca000 r-xp 00000000 03:02 845529     /usr/lib/firefox/components/libpref.so
 b71ca000-b71cb000 rw-p 0000f000 03:02 845529     /usr/lib/firefox/components/libpref.so
 b71cb000-b71db000 r-xp 00000000 03:02 845646     /usr/lib/firefox/components/libchrome.so
 b71db000-b71dc000 rw-p 0000f000 03:02 845646     /usr/lib/firefox/components/libchrome.so
 b71dc000-b71e7000 r-xp 00000000 03:02 813866     /usr/lib/libmyspell.so.3.1
 b71e7000-b71eb000 rw-p 0000a000 03:02 813866     /usr/lib/libmyspell.so.3.1
 b71eb000-b71ed000 r-xp 00000000 03:02 668494     /usr/lib/libavahi-glib.so.1.0.1
 b71ed000-b71ee000 rw-p 00002000 03:02 668494     /usr/lib/libavahi-glib.so.1.0.1
 b71ee000-b71f5000 r-xp 00000000 03:02 845705     /usr/lib/firefox/components/libautoconfig.so
 b71f5000-b71f6000 rw-p 00006000 03:02 845705     /usr/lib/firefox/components/libautoconfig.so
 b71f6000-b71fb000 r-xp 00000000 03:02 845717     /usr/lib/firefox/components/libmyspell.so
 b71fb000-b71fc000 rw-p 00004000 03:02 845717     /usr/lib/firefox/components/libmyspell.so
 b71fc000-b71ff000 r-xp 00000000 03:02 845720     /usr/lib/firefox/components/libbrowserdirprovider.so
 b71ff000-b7200000 rw-p 00002000 03:02 845720     /usr/lib/firefox/components/libbrowserdirprovider.so
 b7200000-b7202000 r-xp 00000000 03:02 832112     /usr/lib/gconv/UTF-16.so
 b7202000-b7204000 rw-p 00001000 03:02 832112     /usr/lib/gconv/UTF-16.so
 b7204000-b720d000 r-xp 00000000 03:02 601500     /lib/tls/i686/cmov/libnss_files-2.4.so
 b720d000-b720f000 rw-p 00008000 03:02 601500     /lib/tls/i686/cmov/libnss_files-2.4.so
 b720f000-b7217000 r-xp 00000000 03:02 601502     /lib/tls/i686/cmov/libnss_nis-2.4.so
 b7217000-b7219000 rw-p 00007000 03:02 601502     /lib/tls/i686/cmov/libnss_nis-2.4.so
 b7219000-b722b000 r-xp 00000000 03:02 601497     /lib/tls/i686/cmov/libnsl-2.4.so
 b722b000-b722d000 rw-p 00011000 03:02 601497     /lib/tls/i686/cmov/libnsl-2.4.so
 b722d000-b722f000 rw-p b722d000 00:00 0 
 b722f000-b7236000 r-xp 00000000 03:02 601498     /lib/tls/i686/cmov/libnss_compat-2.4.so
 b7236000-b7238000 rw-p 00006000 03:02 601498     /lib/tls/i686/cmov/libnss_compat-2.4.so
 b7238000-b723a000 r-xp 00000000 03:02 829990     /usr/lib/firefox/libgfxpsshar.so
 b723a000-b723b000 rw-p 00001000 03:02 829990     /usr/lib/firefox/libgfxpsshar.so
 b723b000-b723c000 r-xp 00000000 03:02 832059     /usr/lib/gconv/ISO8859-1.so
 b723c000-b723e000 rw-p 00001000 03:02 832059     /usr/lib/gconv/ISO8859-1.so
 b723e000-b7243000 r--p 00000000 03:02 1106900    /usr/share/locale-langpack/en_AU/LC_MESSAGES/gtk20-properties.mo
 b7243000-b7252000 r--p 00000000 03:02 1106899    /usr/share/locale-langpack/en_AU/LC_MESSAGES/gtk20.mo
 b7252000-b7253000 r-xp 00000000 03:02 862162     /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
 b7253000-b7254000 rw-p 00000000 03:02 862162     /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
 b7254000-b7287000 r--p 00000000 03:02 928673     /usr/lib/locale/en_AU.utf8/LC_CTYPE
 b7287000-b7288000 r--p 00000000 03:02 928674     /usr/lib/locale/en_AU.utf8/LC_NUMERIC
 b7288000-b7289000 r--p 00000000 03:02 928675     /usr/lib/locale/en_AU.utf8/LC_TIME
 b7289000-b7360000 r--p 00000000 03:02 928676     /usr/lib/locale/en_AU.utf8/LC_COLLATE
 b7360000-b7361000 r--p 00000000 03:02 928677     /usr/lib/locale/en_AU.utf8/LC_MONETARY
 b7361000-b7362000 r--p 00000000 03:02 928679     /usr/lib/locale/en_AU.utf8/LC_MESSAGES/SYS_LC_MESSAGES
 b7362000-b7363000 r--p 00000000 03:02 928680     /usr/lib/locale/en_AU.utf8/LC_PAPER
 b7363000-b7364000 r--p 00000000 03:02 928681     /usr/lib/locale/en_AU.utf8/LC_NAME
 b7364000-b7367000 rw-p b7364000 00:00 0 
 b7367000-b7383000 r-xp 00000000 03:02 812827     /usr/lib/libexpat.so.1.0.0
 b7383000-b7385000 rw-p 0001c000 03:02 812827     /usr/lib/libexpat.so.1.0.0
 b7385000-b73a8000 r-xp 00000000 03:02 813867     /usr/lib/libpng12.so.0.1.2.8
 b73a8000-b73a9000 rw-p 00023000 03:02 813867     /usr/lib/libpng12.so.0.1.2.8
 b73a9000-b73b0000 r-xp 00000000 03:02 601507     /lib/tls/i686/cmov/librt-2.4.so
 b73b0000-b73b2000 rw-p 00006000 03:02 601507     /lib/tls/i686/cmov/librt-2.4.so
 b73b2000-b73c5000 r-xp 00000000 03:02 813752     /usr/lib/libz.so.1.2.3
 b73c5000-b73c6000 rw-p 00012000 03:02 813752     /usr/lib/libz.so.1.2.3
 b73c6000-b742d000 r-xp 00000000 03:02 814048     /usr/lib/libfreetype.so.6.3.10
 b742d000-b7430000 rw-p 00067000 03:02 814048     /usr/lib/libfreetype.so.6.3.10
 b7430000-b7431000 rw-p b7430000 00:00 0 
 b7431000-b745b000 r-xp 00000000 03:02 814795     /usr/lib/libpangoft2-1.0.so.0.1400.5
 b745b000-b745c000 rw-p 00029000 03:02 814795     /usr/lib/libpangoft2-1.0.so.0.1400.5
 b745c000-b7460000 r-xp 00000000 03:02 814234     /usr/lib/libXdmcp.so.6.0.0
 b7460000-b7461000 rw-p 00003000 03:02 814234     /usr/lib/libXdmcp.so.6.0.0
 b7461000-b7463000 r-xp 00000000 03:02 814176     /usr/lib/libXau.so.6.0.0
 b7463000-b7464000 rw-p 00001000 03:02 814176     /usr/lib/libXau.so.6.0.0
 b7464000-b7468000 r-xp 00000000 03:02 813842     /usr/lib/libXfixes.so.3.1.0
 b7468000-b7469000 rw-p 00003000 03:02 813842     /usr/lib/libXfixes.so.3.1.0
 b7469000-b7471000 r-xp 00000000 03:02 814043     /usr/lib/libXcursor.so.1.0.2
 b7471000-b7472000 rw-p 00007000 03:02 814043     /usr/lib/libXcursor.so.1.0.2
 b7472000-b7473000 rw-p b7472000 00:00 0 
 b7473000-b7475000 r-xp 00000000 03:02 813891     /usr/lib/libXrandr.so.2.0.0
 b7475000-b7476000 rw-p 00002000 03:02 813891     /usr/lib/libXrandr.so.2.0.0
 b7476000-b747d000 r-xp 00000000 03:02 814050     /usr/lib/libXi.so.6.0.0
 b747d000-b747e000 rw-p 00006000 03:02 814050     /usr/lib/libXi.so.6.0.0
 b747e000-b7480000 r-xp 00000000 03:02 814609     /usr/lib/libXinerama.so.1.0.0
 b7480000-b7481000 rw-p 00001000 03:02 814609     /usr/lib/libXinerama.so.1.0.0
 b7481000-b7488000 r-xp 00000000 03:02 813731     /usr/lib/libXrender.so.1.3.0
 b7488000-b7489000 rw-p 00006000 03:02 813731     /usr/lib/libXrender.so.1.3.0
 b7489000-b7495000 r-xp 00000000 03:02 814039     /usr/lib/libXext.so.6.4.0
 b7495000-b7496000 rw-p 0000c000 03:02 814039     /usr/lib/libXext.so.6.4.0
 b7496000-b74bf000 r-xp 00000000 03:02 813060     /usr/lib/libfontconfig.so.1.0.4
 b74bf000-b74c4000 rw-p 00028000 03:02 813060     /usr/lib/libfontconfig.so.1.0.4
 b74c4000-b74c6000 rw-p b74c4000 00:00 0 
 b74c6000-b7526000 r-xp 00000000 03:02 813062     /usr/lib/libcairo.so.2.9.2
 b7526000-b7528000 rw-p 0005f000 03:02 813062     /usr/lib/libcairo.so.2.9.2
 b7528000-b75b9000 r-xp 00000000 03:02 813624     /usr/lib/libglib-2.0.so.0.1200.4
 b75b9000-b75ba000 rw-p 00091000 03:02 813624     /usr/lib/libglib-2.0.so.0.1200.4
 b75ba000-b75bd000 r-xp 00000000 03:02 813995     /usr/lib/libgmodule-2.0.so.0.1200.4
 b75bd000-b75be000 rw-p 00002000 03:02 813995     /usr/lib/libgmodule-2.0.so.0.1200.4
 b75be000-b75f7000 r-xp 00000000 03:02 813690     /usr/lib/libgobject-2.0.so.0.1200.4
 b75f7000-b75f8000 rw-p 00038000 03:02 813690     /usr/lib/libgobject-2.0.so.0.1200.4
 b75f8000-b7610000 r-xp 00000000 03:02 814761     /usr/lib/libatk-1.0.so.0.1213.0
 b7610000-b7612000 rw-p 00017000 03:02 814761     /usr/lib/libatk-1.0.so.0.1213.0
 b7612000-b764a000 r-xp 00000000 03:02 813526     /usr/lib/libpango-1.0.so.0.1400.5
 b764a000-b764c000 rw-p 00037000 03:02 813526     /usr/lib/libpango-1.0.so.0.1400.5
 b764c000-b764d000 rw-p b764c000 00:00 0 
 b764d000-b7654000 r-xp 00000000 03:02 814799     /usr/lib/libpangocairo-1.0.so.0.1400.5
 b7654000-b7655000 rw-p 00006000 03:02 814799     /usr/lib/libpangocairo-1.0.so.0.1400.5
 b7655000-b766a000 r-xp 00000000 03:02 814882     /usr/lib/libgdk_pixbuf-2.0.so.0.1000.6
 b766a000-b766b000 rw-p 00015000 03:02 814882     /usr/lib/libgdk_pixbuf-2.0.so.0.1000.6
 b766b000-b7675000 r-xp 00000000 03:02 569089     /lib/libgcc_s.so.1
 b7675000-b7676000 rw-p 00009000 03:02 569089     /lib/libgcc_s.so.1
 b7676000-b7678000 r-xp 00000000 03:02 601494     /lib/tls/i686/cmov/libdl-2.4.so
 b7678000-b767a000 rw-p 00001000 03:02 601494     /lib/tls/i686/cmov/libdl-2.4.so
 b767a000-b767c000 r-xp 00000000 03:02 814198     /usr/lib/libplds4.so
 b767c000-b767d000 rw-p 00001000 03:02 814198     /usr/lib/libplds4.so
 b767d000-b767e000 rw-p b767d000 00:00 0 
 b767e000-b76a2000 r-xp 00000000 03:02 601495     /lib/tls/i686/cmov/libm-2.4.so
 b76a2000-b76a4000 rw-p 00023000 03:02 601495     /lib/tls/i686/cmov/libm-2.4.so
 b76a4000-b77d1000 r-xp 00000000 03:02 601491     /lib/tls/i686/cmov/libc-2.4.so
 b77d1000-b77d3000 r--p 0012c000 03:02 601491     /lib/tls/i686/cmov/libc-2.4.so
 b77d3000-b77d5000 rw-p 0012e000 03:02 601491     /lib/tls/i686/cmov/libc-2.4.so
 b77d5000-b77d8000 rw-p b77d5000 00:00 0 
 b77d8000-b78ac000 r-xp 00000000 03:02 814000     /usr/lib/libstdc++.so.6.0.8
 b78ac000-b78af000 r--p 000d4000 03:02 814000     /usr/lib/libstdc++.so.6.0.8
 b78af000-b78b1000 rw-p 000d7000 03:02 814000     /usr/lib/libstdc++.so.6.0.8
 b78b1000-b78b7000 rw-p b78b1000 00:00 0 
 b78b7000-b797d000 r-xp 00000000 03:02 812941     /usr/lib/libX11.so.6.2.0
 b797d000-b7980000 rw-p 000c5000 03:02 812941     /usr/lib/libX11.so.6.2.0
 b7980000-b7a01000 r-xp 00000000 03:02 814890     /usr/lib/libgdk-x11-2.0.so.0.1000.6
 b7a01000-b7a04000 rw-p 00081000 03:02 814890     /usr/lib/libgdk-x11-2.0.so.0.1000.6
 b7a04000-b7d4d000 r-xp 00000000 03:02 814891     /usr/lib/libgtk-x11-2.0.so.0.1000.6
 b7d4d000-b7d53000 rw-p 00349000 03:02 814891     /usr/lib/libgtk-x11-2.0.so.0.1000.6
 b7d53000-b7d55000 rw-p b7d53000 00:00 0 
 b7d55000-b7d64000 r-xp 00000000 03:02 601505     /lib/tls/i686/cmov/libpthread-2.4.so
 b7d64000-b7d66000 rw-p 0000f000 03:02 601505     /lib/tls/i686/cmov/libpthread-2.4.so
 b7d66000-b7d68000 rw-p b7d66000 00:00 0 
 b7d68000-b7d97000 r-xp 00000000 03:02 813211     /usr/lib/libnspr4.so
 b7d97000-b7d99000 rw-p 0002e000 03:02 813211     /usr/lib/libnspr4.so
 b7d99000-b7d9a000 rw-p b7d99000 00:00 0 
 b7d9a000-b7d9e000 r-xp 00000000 03:02 813231     /usr/lib/libplc4.so
 b7d9e000-b7d9f000 rw-p 00003000 03:02 813231     /usr/lib/libplc4.so
 b7d9f000-b7da0000 r--p 00000000 03:02 928682     /usr/lib/locale/en_AU.utf8/LC_ADDRESS
 b7da0000-b7da1000 r--p 00000000 03:02 928683     /usr/lib/locale/en_AU.utf8/LC_TELEPHONE
 b7da1000-b7da2000 r--p 00000000 03:02 928684     /usr/lib/locale/en_AU.utf8/LC_MEASUREMENT
 b7da2000-b7da9000 r--s 00000000 03:02 830199     /usr/lib/gconv/gconv-modules.cache
 b7da9000-b7daa000 r--p 00000000 03:02 928685     /usr/lib/locale/en_AU.utf8/LC_IDENTIFICATION
 b7daa000-b7e4b000 r-xp 00000000 03:02 831822     /usr/lib/firefox/libxpcom_core.so
 b7e4b000-b7e53000 rw-p 000a0000 03:02 831822     /usr/lib/firefox/libxpcom_core.so
 b7e53000-b7e55000 r-xp 00000000 03:02 831820     /usr/lib/firefox/libxpcom.so
 b7e55000-b7e56000 rw-p 00002000 03:02 831820     /usr/lib/firefox/libxpcom.so
 b7e56000-b7efd000 r-xp 00000000 03:02 831819     /usr/lib/firefox/libmozjs.so
 b7efd000-b7f02000 rw-p 000a6000 03:02 831819     /usr/lib/firefox/libmozjs.so
 b7f02000-b7f04000 rw-p b7f02000 00:00 0 
 b7f04000-b7f1d000 r-xp 00000000 03:02 568982     /lib/ld-2.4.so
 b7f1d000-b7f1f000 rw-p 00018000 03:02 568982     /lib/ld-2.4.so
 bfd41000-bfd55000 rwxp bfd41000 00:00 0          [stack]
 bfd55000-bfd57000 rw-p bfd55000 00:00 0 
 ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]
ProcStatus:
 Name:	firefox-bin
 State:	D (disk sleep)
 SleepAVG:	84%
 Tgid:	5367
 Pid:	5367
 PPid:	1
 TracerPid:	0
 Uid:	1000	1000	1000	1000
 Gid:	1000	1000	1000	1000
 FDSize:	256
 Groups:	4 20 24 25 29 30 44 46 106 110 112 1000 
 VmPeak:	  193220 kB
 VmSize:	  192176 kB
 VmLck:	       0 kB
 VmHWM:	   93800 kB
 VmRSS:	   93800 kB
 VmData:	  130692 kB
 VmStk:	      88 kB
 VmExe:	      72 kB
 VmLib:	   42024 kB
 VmPTE:	     136 kB
 Threads:	12
 SigQ:	1/4294967295
 SigPnd:	0000000000000000
 ShdPnd:	0000000000000000
 SigBlk:	fffffffe7ffbfaff
 SigIgn:	0000000020001000
 SigCgt:	000000018000402f
 CapInh:	0000000000000000
 CapPrm:	0000000000000000
 CapEff:	0000000000000000
Signal: 11
CoreDump: base64

---

