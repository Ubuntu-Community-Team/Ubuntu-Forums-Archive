---
title: "SOLVED: Samsung SCX-4200 scanner driver crashes"
date: 2007-09-25
forum: Hardware &amp; Laptops
---

### Post by julian.coccia on 2007-09-25
Hi there,

I can't contact Samsung (their web form doesn't work :|), but I thought I'd drop a line here in case someone else runs into the same problem.

I was unable to scan using my SCX-4200 mutifunction printer under Ubuntu 7.04. Printer works fine using the latest drivers provided by Samsung. However, when clicking on the scanner icon, in the "Samsung unified driver", the program silently crashes.

When starting the application from the console, I realized right before the crash it says: "glibc detected". Therefore, I uninstalled it by issuing:

sudo dpkg --purge libstdc++2.10-glibc2.2

Right after that, the scanner works like a charm (using their provided software, of course. xsane never detects it)

Cheers,
Julian Coccia

Here is the error dump:

```
$ /opt/Samsung/mfp/bin/Configurator
*** glibc detected *** /opt/Samsung/mfp/bin/Configurator: double free or corruption (!prev): 0x08225448 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb744a7cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb744de30]
/usr/lib/libstdc++-libc6.2-2.so.3(__builtin_vec_delete+0x24)[0xb6841464]
/usr/lib/sane/libsane-samsung_scx4200.so.1(init_mfp_port_control__4port+0x7f)[0xb687938b]
/usr/lib/sane/libsane-samsung_scx4200.so.1(init_mfp_port_control__6device+0x16)[0xb6879e6a]
/usr/lib/sane/libsane-samsung_scx4200.so.1(init_mfp_port_control__6driver+0x16)[0xb6880a76]
/usr/lib/sane/libsane-samsung_scx4200.so.1(init__C7backendPiPFPCcPcPc_v+0x23)[0xb688212f]
/usr/lib/sane/libsane-samsung_scx4200.so.1(sane_samsung_scx4200_init+0x31)[0xb6882965]
/usr/lib/libsane.so.1[0xb6b3816d]
/usr/lib/libsane.so.1(sane_dll_get_devices+0x87)[0xb6b38487]
/usr/lib/libsane.so.1(sane_get_devices+0x24)[0xb6b389e4]
/opt/Samsung/mfp/lib/libScannerPlugin.so(_ZN7backend7refreshEv+0x153)[0xb6b4e1a3]
/opt/Samsung/mfp/lib/libScannerPlugin.so(_ZN13ScannerPlugin19RefreshScannersListEv+0x125)[0xb6b4d235]
/opt/Samsung/mfp/lib/libScannerPlugin.so(_ZN13ScannerPlugin10OnActivateEv+0x22)[0xb6b4d0c2]
/opt/Samsung/mfp/bin/Configurator[0x804ed2d]
/opt/Samsung/mfp/bin/Configurator[0x804e96e]
/opt/Samsung/mfp/bin/Configurator[0x8051bbd]
/usr/lib/libqt-mt.so.3(_ZN7QObject15activate_signalEP15QConnectionListP8QUObject+0x25c)[0xb7a5d9b8]
/usr/lib/libqt-mt.so.3(_ZN7QObject15activate_signalEii+0x1b0)[0xb7a5e1a2]
/usr/lib/libqt-mt.so.3(_ZN12QButtonGroup7clickedEi+0x38)[0xb7df1af0]
/usr/lib/libqt-mt.so.3(_ZN12QButtonGroup13buttonClickedEv+0xbc)[0xb7af99d0]
/usr/lib/libqt-mt.so.3(_ZN12QButtonGroup9qt_invokeEiP8QUObject+0x72)[0xb7df1a56]
/usr/lib/libqt-mt.so.3(_ZN7QObject15activate_signalEP15QConnectionListP8QUObject+0x12f)[0xb7a5d88b]
/usr/lib/libqt-mt.so.3(_ZN7QObject15activate_signalEi+0x162)[0xb7a5e330]
/usr/lib/libqt-mt.so.3(_ZN7QButton7clickedEv+0x31)[0xb7df27c7]
/usr/lib/libqt-mt.so.3(_ZN7QButton17mouseReleaseEventEP11QMouseEvent+0x14a)[0xb7afbf30]
/usr/lib/libqt-mt.so.3(_ZN7QWidget5eventEP6QEvent+0xf3)[0xb7a9465d]
/usr/lib/libqt-mt.so.3(_ZN12QApplication14internalNotifyEP7QObjectP6QEvent+0x274)[0xb79f4a60]
/usr/lib/libqt-mt.so.3(_ZN12QApplication6notifyEP7QObjectP6QEvent+0x578)[0xb79f6c1e]
/usr/lib/libqt-mt.so.3(_ZN12QApplication20sendSpontaneousEventEP7QObjectP6QEvent+0x5b)[0xb798725d]
/usr/lib/libqt-mt.so.3(_ZN9QETWidget19translateMouseEventEPK7_XEvent+0x121e)[0xb7985ec2]
/usr/lib/libqt-mt.so.3(_ZN12QApplication15x11ProcessEventEP7_XEvent+0xbfc)[0xb7983fac]
/usr/lib/libqt-mt.so.3(_ZN10QEventLoop13processEventsEj+0x108)[0xb799b180]
/usr/lib/libqt-mt.so.3(_ZN10QEventLoop9enterLoopEv+0x70)[0xb7a0f136]
/usr/lib/libqt-mt.so.3(_ZN10QEventLoop4execEv+0x32)[0xb7a0ef46]
/usr/lib/libqt-mt.so.3(_ZN12QApplication4execEv+0x25)[0xb79f6609]
/opt/Samsung/mfp/bin/Configurator[0x804f683]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb73f8ebc]
/opt/Samsung/mfp/bin/Configurator(_ZN7QWidget22windowActivationChangeEb+0x3d)[0x804d481]
======= Memory map: ========
08048000-08072000 r-xp 00000000 03:02 6734086    /opt/Samsung/mfp/bin/Configurator
08072000-08074000 rw-p 00029000 03:02 6734086    /opt/Samsung/mfp/bin/Configurator
08074000-08247000 rw-p 08074000 00:00 0          [heap]
b6700000-b6721000 rw-p b6700000 00:00 0 
b6721000-b6800000 ---p b6721000 00:00 0 
b680b000-b6844000 r-xp 00000000 03:02 10801355   /usr/lib/libstdc++-3-libc6.2-2-2.10.0.so
b6844000-b6851000 rw-p 00038000 03:02 10801355   /usr/lib/libstdc++-3-libc6.2-2-2.10.0.so
b6851000-b6853000 rw-p b6851000 00:00 0 
b686d000-b6886000 r-xp 00000000 03:02 10816402   /usr/lib/sane/libsane-samsung_scx4200.so.1.0.1
b6886000-b688a000 rw-p 00018000 03:02 10816402   /usr/lib/sane/libsane-samsung_scx4200.so.1.0.1
b688a000-b69a1000 r-xp 00000000 03:02 10797475   /usr/lib/libxml2.so.2.6.27
b69a1000-b69a7000 rw-p 00116000 03:02 10797475   /usr/lib/libxml2.so.2.6.27
b69a7000-b69cd000 r-xp 00000000 03:02 4538858    /usr/lib/sane/libsane-smfp.so.1.0.1
b69cd000-b69cf000 rw-p 00026000 03:02 4538858    /usr/lib/sane/libsane-smfp.so.1.0.1
b69cf000-b6a45000 r--p 00000000 03:02 3801256    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b6a45000-b6a48000 rw-p b6a45000 00:00 0 
b6a48000-b6a8c000 r--p 00000000 03:02 11813156   /usr/share/fonts/truetype/msttcorefonts/Arial.ttf
b6a8c000-b6a99000 r-xp 00000000 03:02 9864213    /usr/lib/libmfp.so.1.0.1
b6a99000-b6a9a000 rw-p 0000c000 03:02 9864213    /usr/lib/libmfp.so.1.0.1
b6a9a000-b6ac3000 r-xp 00000000 03:02 6750309    /opt/Samsung/mfp/lib/libMFPPortPlugin.so
b6ac3000-b6ac6000 rw-p 00028000 03:02 6750309    /opt/Samsung/mfp/lib/libMFPPortPlugin.so
b6ac6000-b6ad1000 rw-p b6ac6000 00:00 0 
b6ad1000-b6ada000 r-xp 00000000 03:02 10802202   /usr/lib/libieee1284.so.3.2.2
b6ada000-b6adb000 rw-p 00008000 03:02 10802202   /usr/lib/libieee1284.so.3.2.2
b6adb000-b6b2b000 r-xp 00000000 03:02 9863625    /usr/lib/libtiff.so.4.2.1
b6b2b000-b6b2d000 rw-p 00050000 03:02 9863625    /usr/lib/libtiff.so.4.2.1
b6b2d000-b6b33000 r-xp 00000000 03:02 9257085    /lib/libusb-0.1.so.4.4.4
b6b33000-b6b35000 rw-p 00005000 03:02 9257085    /lib/libusb-0.1.so.4.4.4
b6b35000-b6b3a000 r-xp 00000000 03:02 9863571    /usr/lib/libsane.so.1.0.18
b6b3a000-b6b3b000 rw-p 00005000 03:02 9863571    /usr/lib/libsane.so.1.0.18
b6b3b000-b6b6d000 r-xp 00000000 03:02 6750313    /opt/Samsung/mfp/lib/libScannerPlugin.so
b6b6d000-b6b70000 rw-p 00032000 03:02 6750313    /opt/Samsung/mfp/lib/libScannerPlugin.so
b6b70000-b6b7b000 rw-p b6b70000 00:00 0 
b6b7b000-b6b84000 r-xp 00000000 03:02 6946877    /lib/tls/i686/cmov/libnss_files-2.5.so
b6b84000-b6b86000 rw-p 00008000 03:02 6946877    /lib/tls/i686/cmov/libnss_files-2.5.so
b6b86000-b6b8e000 r-xp 00000000 03:02 6946881    /lib/tls/i686/cmov/libnss_nis-2.5.so
b6b8e000-b6b90000 rw-p 00007000 03:02 6946881    /lib/tls/i686/cmov/libnss_nis-2.5.so
b6b90000-b6b97000 r-xp 00000000 03:02 6946873    /lib/tls/i686/cmov/libnss_compat-2.5.so
b6b97000-b6b99000 rw-p 00006000 03:02 6946873    /lib/tls/i686/cmov/libnss_compat-2.5.so
b6b99000-b6bac000 r-xp 00000000 03:02 6946871    /lib/tls/i686/cmov/libnsl-2.5.so
b6bac000-b6bae000 rw-p 00012000 03:02 6946871    /lib/tls/i686/cmov/libnsl-2.5.so
b6bae000-b6bb0000 rw-p b6bae000 00:00 0 
b6bb0000-b6bb3000 r-xp 00000000 03:02 9863847    /usr/lib/libgpg-error.so.0.3.0
b6bb3000-b6bb4000 rw-p 00002000 03:02 9863847    /usr/lib/libgpg-error.so.0.3.0
b6bb4000-b6c03000 r-xp 00000000 03:02 9863287    /usr/lib/libgcrypt.so.11.2.2
b6c03000-b6c05000 rw-p 0004e000 03:02 9863287    /usr/lib/libgcrypt.so.11.2.2
b6c05000-b6c19000 r-xp 00000000 03:02 10797771   /usr/lib/libtasn1.so.3.0.6
b6c19000-b6c1a000 rw-p 00013000 03:02 10797771   /usr/lib/libtasn1.so.3.0.6
b6c1a000-b6c1f000 r-xp 00000000 03:02 6946863    /lib/tls/i686/cmov/libcrypt-2.5.so
b6c1f000-b6c21000 rw-p 00004000 03:02 6946863    /lib/tls/i686/cmov/libcrypt-2.5.so
b6c21000-b6c48000 rw-p b6c21000 00:00 0 
b6c48000-b6cb2000 r-xp 00000000 03:02 10798030   /usr/lib/libgnutls.so.13.0.9
b6cb2000-b6cb8000 rw-p 0006a000 03:02 10798030   /usr/lib/libgnutls.so.13.0.9
b6cb8000-b6ce7000 r-xp 00000000 03:02 10798372   /usr/lib/libcups.so.2
b6ce7000-b6ce9000 rw-p 0002e000 03:02 10798372   /usr/lib/libcups.so.2
b6ce9000-b6dad000 r-xp 00000000 03:02 6750311    /opt/Samsung/mfp/lib/libPrinterPlugin.so
b6dad000-b6db5000 rw-p 000c3000 03:02 6750311    /opt/Samsung/mfp/lib/libPrinterPlugin.so
b6db5000-b6dc0000 rw-p b6db5000 00:00 0 
b6dc0000-b6dea000 r-xp 00000000 03:02 9863425    /usr/lib/liblcms.so.1.0.15
b6dea000-b6deb000 rw-p 00029000 03:02 9863425    /usr/lib/liblcms.so.1.0.15
b6deb000-b6dee000 rw-p b6deb000 00:00 0 
b6dee000-b6e59000 r-xp 00000000 03:02 9863456    /usr/lib/libmng.so.1.1.0.9
b6e59000-b6e5c000 rw-p 0006a000 03:02 9863456    /usr/lib/libmng.so.1.1.0.9
b6e5c000-b6ed9000 r--p 00000000 03:02 3801260    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b6ed9000-b6f03000 r-xp 00000000 03:02 10800767   /usr/lib/libkdefx.so.4.2.0
b6f03000-b6f04000 rw-p 0002a000 03:02 10800767   /usr/lib/libkdefx.so.4.2.0
b6f15000-b6f16000 rw-s 00000000 00:08 35946534   /SYSVeca8642b (deleted)
b6f16000-b6f17000 rw-s 00000000 00:08 35913765   /SYSVeca8642a (deleted)
b6f17000-b6f18000 rw-s 00000000 00:08 35880996   /SYSVeca86429 (deleted)
b6f18000-b6f19000 rw-s 00000000 00:08 35848227   /SYSVeca86428 (deleted)
b6f19000-b6f1a000 rw-s 00000000 00:08 35815458   /SYSVeca86427 (deleted)
b6f1a000-b6f1b000 rw-s 00000000 00:08 35782689   /SYSVeca86426 (deleted)
b6f1b000-b6f1c000 rw-s 00000000 00:08 35749920   /SYSVeca86425 (deleted)
b6f1c000-b6f1d000 rw-s 00000000 00:08 35717151   /SYSVeca86424 (deleted)
b6f1d000-b6f1e000 rw-s 00000000 00:08 35684382   /SYSVeca86423 (deleted)
b6f1e000-b6f46000 r-xp 00000000 03:02 6604330    /usr/lib/kde3/plugins/styles/polyester.so
b6f46000-b6f47000 rw-p 00028000 03:02 6604330    /usr/lib/kde3/plugins/styles/polyester.so
b6f47000-b6f5a000 r--p 00000000 03:02 11174878   /usr/share/locale-langpack/es/LC_MESSAGES/libc.mo
b6f5a000-b6f60000 r--s 00000000 03:02 5751113    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b6f60000-b6f61000 r--s 00000000 03:02 5751111    /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b6f61000-b6f64000 r--s 00000000 03:02 5751110    /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b6f64000-b6f65000 r--s 00000000 03:02 5751109    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b6f65000-b6f66000 r--s 00000000 03:02 5751108    /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b6f66000-b6f6a000 r--s 00000000 03:02 5751107    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b6f6a000-b6f6b000 r--s 00000000 03:02 5751105    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b6f6b000-b6f6d000 r--s 00000000 03:02 5751104    /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b6f6d000-b6f6f000 r--s 00000000 03:02 5751103    /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b6f6f000-b6f70000 r--s 00000000 03:02 5751102    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b6f70000-b6f72000 r--s 00000000 03:02 5751101    /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b6f72000-b6f78000 r--s 00000000 03:02 5751099    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b6f78000-b6f7a000 r--s 00000000 03:02 5750870    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b6f7a000-b6f7c000 r--s 00000000 03:02 5750869    /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b6f7c000-b6f84000 r--s 00000000 03:02 5750868    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b6f84000-b6f8a000 r--s 00000000 03:02 5750867    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b6f8a000-b6f8b000 r--s 00000000 03:02 5750866    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b6f8b000-b6fa2000 r--s 00000000 03:02 5750865    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b6fa2000-b6fa4000 r--s 00000000 03:02 5750864    /var/cache/fontconfig/2c5ba8142dffc8bf0377700342b8ca1a-x86.cache-2
b6fa4000-b6fa6000 r--s 00000000 03:02 5750863    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b6fa6000-b6fac000 r--s 00000000 03:02 5750862    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b6fac000-b6faf000 r--s 00000000 03:02 5750861    /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b6faf000-b6fb3000 r--s 00000000 03:02 5750860    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b6fb3000-b6fb5000 r--s 00000000 03:02 5750854    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b6fb5000-b6fb6000 r--s 00000000 03:02 5751150    /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b6fb6000-b6fb8000 r--s 00000000 03:02 5751149    /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b6fb8000-b6fb9000 r--s 00000000 03:02 5751148    /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
b6fb9000-b6fba000 r--s 00000000 03:02 5751147    /var/cache/fontconfig/e22b663d51a3e226824aa2afd6c591f7-x86.cache-2
b6fba000-b6fbb000 r--s 00000000 03:02 5751146    /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
b6fbb000-b6fbc000 r--s 00000000 03:02 5751145    /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86.cache-2
b6fbc000-b6fbf000 r--s 00000000 03:02 5751144    /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b6fbf000-b6fc2000 r--s 00000000 03:02 5751143    /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b6fc2000-b6fcb000 r--s 00000000 03:02 5751142    /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b6fcb000-b6fcd000 r--s 00000000 03:02 5751141    /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b6fcd000-b6fce000 r--s 00000000 03:02 5751140    /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b6fce000-b6fd0000 r--s 00000000 03:02 5751139    /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b6fd0000-b6fd1000 r--s 00000000 03:02 5751138    /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b6fd1000-b6fd6000 r--s 00000000 03:02 5751137    /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b6fd6000-b6fda000 r--s 00000000 03:02 5751136    /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b6fda000-b6fdc000 r--s 00000000 03:02 5751135    /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b6fdc000-b6fdf000 r--s 00000000 03:02 5751134    /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b6fdf000-b6fe0000 r--s 00000000 03:02 5751133    /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b6fe0000-b6fe1000 r--s 00000000 03:02 5751132    /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86.cache-2
b6fe1000-b6fe3000 r--s 00000000 03:02 5751131    /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b6fe3000-b6fe9000 r--s 00000000 03:02 5751130    /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b6fe9000-b6fef000 r--s 00000000 03:02 5751129    /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b6fef000-b6ff0000 r--s 00000000 03:02 5751128    /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b6ff0000-b6ff8000 r--s 00000000 03:02 5751127    /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b6ff8000-b6ffd000 r--s 00000000 03:02 5751126    /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b6ffd000-b7000000 r--s 00000000 03:02 5751125    /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b7000000-b7005000 r--s 00000000 03:02 5751124    /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b7005000-b7007000 r--s 00000000 03:02 5751117    /var/cache/fontconfig/beeeeb3dfe132a8a0633a017c99ce0c0-x86.cache-2
b7007000-b7008000 r--s 00000000 03:02 6867107    /home/julian/.fontconfig/98342ffb89608906d668973f1d753d96-x86.cache-2
b7008000-b7043000 r--p 00000000 03:02 10846211   /usr/lib/locale/es_ES.utf8/LC_CTYPE
b7043000-b711a000 r--p 00000000 03:02 10847556   /usr/lib/locale/es_ES.utf8/LC_COLLATE
b711a000-b711c000 rw-p b711a000 00:00 0 
b711c000-b7120000 r-xp 00000000 03:02 10798550   /usr/lib/libXfixes.so.3.1.0
b7120000-b7121000 rw-p 00003000 03:02 10798550   /usr/lib/libXfixes.so.3.1.0
b7121000-b713f000 r-xp 00000000 03:02 10797716   /usr/lib/libexpat.so.1.0.0
b713f000-b7141000 rw-p 0001d000 03:02 10797716   /usr/lib/libexpat.so.1.0.0
b7141000-b7145000 r-xp 00000000 03:02 10798080   /usr/lib/libXdmcp.so.6.0.0
b7145000-b7146000 rw-p 00003000 03:02 10798080   /usr/lib/libXdmcp.so.6.0.0
b7146000-b7148000 r-xp 00000000 03:02 10798074   /usr/lib/libXau.so.6.0.0
b7148000-b7149000 rw-p 00001000 03:02 10798074   /usr/lib/libXau.so.6.0.0
b7149000-b714a000 rw-p b7149000 00:00 0 
b714a000-b7229000 r-xp 00000000 03:02 10797397   /usr/lib/libstdc++.so.6.0.8
b7229000-b722c000 r--p 000de000 03:02 10797397   /usr/lib/libstdc++.so.6.0.8
b722c000-b722e000 rw-p 000e1000 03:02 10797397   /usr/lib/libstdc++.so.6.0.8
b722e000-b7234000 rw-p b722e000 00:00 0 
b7234000-b7236000 r-xp 00000000 03:02 6946865    /lib/tls/i686/cmov/libdl-2.5.so
b7236000-b7238000 rw-p 00001000 03:02 6946865    /lib/tls/i686/cmov/libdl-2.5.so
b7238000-b724d000 r-xp 00000000 03:02 10798344   /usr/lib/libICE.so.6.3.0
b724d000-b724f000 rw-p 00014000 03:02 10798344   /usr/lib/libICE.so.6.3.0
b724f000-b7250000 rw-p b724f000 00:00 0 
b7250000-b7258000 r-xp 00000000 03:02 10798509   /usr/lib/libSM.so.6.0.0
b7258000-b7259000 rw-p 00007000 03:02 10798509   /usr/lib/libSM.so.6.0.0
b7259000-b72c1000 r-xp 00000000 03:02 10797714   /usr/lib/libfreetype.so.6.3.10
b72c1000-b72c4000 rw-p 00068000 03:02 10797714   /usr/lib/libfreetype.so.6.3.10
b72c4000-b72c5000 rw-p b72c4000 00:00 0 
b72c5000-b72d6000 r-xp 00000000 03:02 10798314   /usr/lib/libXft.so.2.1.2
b72d6000-b72d7000 rw-p 00010000 03:02 10798314   /usr/lib/libXft.so.2.1.2
b72d7000-b72d9000 r-xp 00000000 03:02 10798333   /usr/lib/libXinerama.so.1.0.0
b72d9000-b72da000 rw-p 00001000 03:02 10798333   /usr/lib/libXinerama.so.1.0.0
b72da000-b72e2000 r-xp 00000000 03:02 10798324   /usr/lib/libXcursor.so.1.0.2
b72e2000-b72e3000 rw-p 00007000 03:02 10798324   /usr/lib/libXcursor.so.1.0.2
b72e3000-b72e8000 r-xp 00000000 03:02 10798309   /usr/lib/libXrandr.so.2.1.0
b72e8000-b72e9000 rw-p 00005000 03:02 10798309   /usr/lib/libXrandr.so.2.1.0
b72e9000-b72f0000 r-xp 00000000 03:02 10798137   /usr/lib/libXrender.so.1.3.0
b72f0000-b72f1000 rw-p 00006000 03:02 10798137   /usr/lib/libXrender.so.1.3.0
b72f1000-b72f8000 r-xp 00000000 03:02 10798328   /usr/lib/libXi.so.6.0.0
b72f8000-b72f9000 rw-p 00006000 03:02 10798328   /usr/lib/libXi.so.6.0.0
b72f9000-b72fa000 rw-p b72f9000 00:00 0 
b72fa000-b730d000 r-xp 00000000 03:02 9863855    /usr/lib/libz.so.1.2.3
b730d000-b730e000 rw-p 00012000 03:02 9863855    /usr/lib/libz.so.1.2.3
b730e000-b7330000 r-xp 00000000 03:02 10798040   /usr/lib/libpng12.so.0.15.0
b7330000-b7331000 rw-p 00021000 03:02 10798040   /usr/lib/libpng12.so.0.15.0
b7331000-b734f000 r-xp 00000000 03:02 9863409    /usr/lib/libjpeg.so.62.0.0
b734f000-b7350000 rw-p 0001d000 03:02 9863409    /usr/lib/libjpeg.so.62.0.0
b7350000-b739d000 r-xp 00000000 03:02 10798546   /usr/lib/libXt.so.6.0.0
b739d000-b73a1000 rw-p 0004c000 03:02 10798546   /usr/lib/libXt.so.6.0.0
b73a1000-b73b6000 r-xp 00000000 03:02 10798348   /usr/lib/libaudio.so.2.4
b73b6000-b73b7000 rw-p 00015000 03:02 10798348   /usr/lib/libaudio.so.2.4
b73b7000-b73da000 r-xp 00000000 03:02 10797139   /usr/lib/libfontconfig.so.1.2.0
b73da000-b73e2000 rw-p 00023000 03:02 10797139   /usr/lib/libfontconfig.so.1.2.0
b73e2000-b73e3000 rw-p b73e2000 00:00 0 
b73e3000-b751e000 r-xp 00000000 03:02 6946859    /lib/tls/i686/cmov/libc-2.5.so
b751e000-b751f000 r--p 0013b000 03:02 6946859    /lib/tls/i686/cmov/libc-2.5.so
b751f000-b7521000 rw-p 0013c000 03:02 6946859    /lib/tls/i686/cmov/libc-2.5.so
b7521000-b7524000 rw-p b7521000 00:00 0 
b7524000-b752f000 r-xp 00000000 03:02 9257082    /lib/libgcc_s.so.1
b752f000-b7530000 rw-p 0000a000 03:02 9257082    /lib/libgcc_s.so.1
b7530000-b7555000 r-xp 00000000 03:02 6946867    /lib/tls/i686/cmov/libm-2.5.so
b7555000-b7557000 rw-p 00024000 03:02 6946867    /lib/tls/i686/cmov/libm-2.5.so
b7557000-b7607000 r-xp 00000000 03:02 10797695   /usr/lib/libstdc++.so.5.0.7
b7607000-b760c000 rw-p 000af000 03:02 10797695   /usr/lib/libstdc++.so.5.0.7
b760c000-b7611000 rw-p b760c000 00:00 0 
b7611000-b76fe000 r-xp 00000000 03:02 10798090   /usr/lib/libX11.so.6.2.0
b76fe000-b7702000 rw-p 000ed000 03:02 10798090   /usr/lib/libX11.so.6.2.0
b7702000-b770f000 r-xp 00000000 03:02 10798134   /usr/lib/libXext.so.6.4.0
b770f000-b7710000 rw-p 0000d000 03:02 10798134   /usr/lib/libXext.so.6.4.0
b7710000-b7711000 rw-p b7710000 00:00 0 
b7711000-b7724000 r-xp 00000000 03:02 6946887    /lib/tls/i686/cmov/libpthread-2.5.so
b7724000-b7726000 rw-p 00013000 03:02 6946887    /lib/tls/i686/cmov/libpthread-2.5.so
b7726000-b7728000 rw-p b7726000 00:00 0 
b7728000-b7eee000 r-xp 00000000 03:02 10797443   /usr/lib/libqt-mt.so.3.3.7
b7eee000-b7f34000 rw-p 007c5000 03:02 10797443   /usr/lib/libqt-mt.so.3.3.7
b7f34000-b7f38000 rw-p b7f34000 00:00 0 
b7f38000-b7f39000 rw-s 00000000 00:08 35651613   /SYSVeca86422 (deleted)
b7f39000-b7f3a000 rw-s 00000000 00:08 35618841   /SYSVeca86421 (deleted)
b7f3a000-b7f3b000 rw-s 00000000 00:08 35586072   /SYSVeca86420 (deleted)
b7f3b000-b7f40000 r-xp 00000000 03:02 1328565    /usr/lib/qt3/plugins/imageformats/libqmng.so
b7f40000-b7f41000 rw-p 00004000 03:02 1328565    /usr/lib/qt3/plugins/imageformats/libqmng.so
b7f41000-b7f42000 r--p 00000000 03:02 10847573   /usr/lib/locale/es_ES.utf8/LC_NUMERIC
b7f42000-b7f43000 r--p 00000000 03:02 10847565   /usr/lib/locale/es_ES.utf8/LC_TIME
b7f43000-b7f44000 r--p 00000000 03:02 10847709   /usr/lib/locale/es_ES.utf8/LC_MONETARY
b7f44000-b7f45000 r--p 00000000 03:02 10862684   /usr/lib/locale/es_ES.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f45000-b7f46000 r--p 00000000 03:02 10847398   /usr/lib/locale/es_ES.utf8/LC_PAPER
b7f46000-b7f47000 r--p 00000000 03:02 10847396   /usr/lib/locale/es_ES.utf8/LC_NAME
b7f47000-b7f48000 r--p 00000000 03:02 10847710   /usr/lib/locale/es_ES.utf8/LC_ADDRESS
b7f48000-b7f49000 r--p 00000000 03:02 10847711   /usr/lib/locale/es_ES.utf8/LC_TELEPHONE
b7f49000-b7f4a000 r--p 00000000 03:02 10847394   /usr/lib/locale/es_ES.utf8/LC_MEASUREMENT
b7f4a000-b7f51000 r--s 00000000 03:02 10813823   /usr/lib/gconv/gconv-modules.cache
b7f51000-b7f52000 r--p 00000000 03:02 10847712   /usr/lib/locale/es_ES.utf8/LC_IDENTIFICATION
b7f52000-b7f54000 rw-p b7f52000 00:00 0 
b7f54000-b7f6d000 r-xp 00000000 03:02 9257902    /lib/ld-2.5.so
b7f6d000-b7f6f000 rw-p 00019000 03:02 9257902    /lib/ld-2.5.so
bfd4a000-bfd5d000 rwxp bfd4a000 00:00 0          [stack]
bfd5d000-bfd60000 rw-p bfd5d000 00:00 0 
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Cancelado

```

---

### Post by BoeBoe on 2008-02-25
Hi julian,

Samsung provides their linux driver which you can download from their website.

---

