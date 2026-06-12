---
title: "Samsung SCX-4521F - Scanner didnt Work"
date: 2008-07-02
forum: Hardware
---

### Post by faiper on 2008-07-02
Hi friends, 

Before asking for such help, I would like to emphasize that already have read every page of google referring to SCX-4521F in linux, including several post this excellent forum.

	
Do not use windows to more than 8 years and do not intend to re-use. However I did a good investment that's laser multifunctional Sansung and accurate than the scanner work.

I installed the most current drive available on the Samsung. I did all procedures outlined by the company and still not worked, not even turning the xsane as root.

	
We also tried the recommendations as a forum for editing and replace the libmfp.so.1.0.1. Nothing said.

The problem is that when the road xsane he simply closes. Following the following error message:

```


root@desktop:/home/thiago/source/fix-nopar/i386# xsane
*** glibc detected *** xsane: double free or corruption (!prev): 0x08236e78 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7633a85]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb76374f0]
/usr/lib/libstdc++-libc6.2-2.so.3(__builtin_delete+0x22)[0xb6cce276]
/usr/lib/libstdc++-libc6.2-2.so.3(__builtin_vec_delete+0x1b)[0xb6cce29f]
/usr/local/lib/sane/libsane-samsung_scx4x21.so.1(init_mfp_port_control__4port+0x7f)[0xb6d0462b]
/usr/local/lib/sane/libsane-samsung_scx4x21.so.1(init_mfp_port_control__6device+0x16)[0xb6d0511e]
/usr/local/lib/sane/libsane-samsung_scx4x21.so.1(init_mfp_port_control__6driver+0x16)[0xb6d0c002]
/usr/local/lib/sane/libsane-samsung_scx4x21.so.1(init__C7backendPiPFPCcPcPc_v+0x23)[0xb6d0d77b]
/usr/local/lib/sane/libsane-samsung_scx4x21.so.1(sane_samsung_scx4x21_init+0x31)[0xb6d0dfb1]
/usr/local/lib/libsane.so.1[0xb7fa1bbd]
/usr/local/lib/libsane.so.1(sane_dll_get_devices+0x8d)[0xb7fa1edd]
/usr/local/lib/libsane.so.1(sane_get_devices+0x24)[0xb7fa2444]
xsane[0x80bb282]
xsane[0x80c8a9b]
xsane[0x80c9d38]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb75de450]
xsane[0x804f511]
======= Memory map: ========
08048000-080e3000 r-xp 00000000 08:01 23463      /usr/bin/xsane
080e3000-080e9000 rw-p 0009a000 08:01 23463      /usr/bin/xsane
080e9000-0824f000 rw-p 080e9000 00:00 0          [heap]
b6a00000-b6a21000 rw-p b6a00000 00:00 0 
b6a21000-b6b00000 ---p b6a21000 00:00 0 
b6be0000-b6c90000 r-xp 00000000 08:01 158819     /usr/lib/libstdc++.so.5.0.7
b6c90000-b6c95000 rw-p 000af000 08:01 158819     /usr/lib/libstdc++.so.5.0.7
b6c95000-b6c9a000 rw-p b6c95000 00:00 0 
b6c9a000-b6cd1000 r-xp 00000000 08:01 10727      /usr/lib/libstdc++-3-libc6.2-2-2.10.0.so
b6cd1000-b6cda000 rw-p 00037000 08:01 10727      /usr/lib/libstdc++-3-libc6.2-2-2.10.0.so
b6cda000-b6cdc000 rw-p b6cda000 00:00 0 
b6cdc000-b6ce9000 r-xp 00000000 08:01 23583      /usr/lib/libmfp.so.1.0.1
b6ce9000-b6cea000 rw-p 0000c000 08:01 23583      /usr/lib/libmfp.so.1.0.1
b6ced000-b6cee000 rw-s 00000000 00:09 950298     /SYSVeca8642b (deleted)
b6cee000-b6cef000 rw-s 00000000 00:09 917529     /SYSVeca8642a (deleted)
b6cef000-b6cf0000 rw-s 00000000 00:09 884760     /SYSVeca86429 (deleted)
b6cf0000-b6cf1000 rw-s 00000000 00:09 851991     /SYSVeca86428 (deleted)
b6cf1000-b6cf2000 rw-s 00000000 00:09 819222     /SYSVeca86427 (deleted)
b6cf2000-b6cf3000 rw-s 00000000 00:09 786453     /SYSVeca86426 (deleted)
b6cf3000-b6cf4000 rw-s 00000000 00:09 753684     /SYSVeca86425 (deleted)
b6cf4000-b6cf5000 rw-s 00000000 00:09 720915     /SYSVeca86424 (deleted)
b6cf5000-b6cf6000 rw-s 00000000 00:09 688146     /SYSVeca86423 (deleted)
b6cf6000-b6cf7000 rw-s 00000000 00:09 655377     /SYSVeca86422 (deleted)
b6cf7000-b6cf8000 rw-s 00000000 00:09 622608     /SYSVeca86421 (deleted)
b6cf8000-b6d11000 r-xp 00000000 08:01 23679      /usr/local/lib/sane/libsane-samsung_scx4x21.so.1.0.1
b6d11000-b6d15000 rw-p 00018000 08:01 23679      /usr/local/lib/sane/libsane-samsung_scx4x21.so.1.0.1
b6d15000-b6e19000 rw-p b6d15000 00:00 0 
b6e19000-b6eaa000 r--p 00000000 08:01 39462      /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b6eaa000-b6eac000 r-xp 00000000 08:01 16971      /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b6eac000-b6ead000 rw-p 00001000 08:01 16971      /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b6ead000-b6eb3000 r--s 00000000 08:01 13427      /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b6eb3000-b6eb6000 r--s 00000000 08:01 13422      /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b6eb6000-b6eb7000 r--s 00000000 08:01 13291      /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b6eb7000-b6eb8000 r--s 00000000 08:01 13290      /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b6eb8000-b6ebb000 r--s 00000000 08:01 13289      /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b6ebb000-b6ebe000 r--s 00000000 08:01 13285      /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b6ebe000-b6ec1000 r--s 00000000 08:01 13267      /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b6ec1000-b6ec9000 r--s 00000000 08:01 11400      /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b6ec9000-b6ed1000 r--s 00000000 08:01 11398      /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b6ed1000-b6ed2000 r--s 00000000 08:01 10701      /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b6ed2000-b6ed5000 r--s 00000000 08:01 10700      /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b6ed5000-b6edc000 r--s 00000000 08:01 10698      /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b6edc000-b6ee2000 r--s 00000000 08:01 10688      /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b6ee2000-b6ee4000 r--s 00000000 08:01 10667      /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b6ee4000-b6f44000 rw-s 00000000 00:09 4948006    /SYSV00000000 (deleted)
b6f44000-b6f4a000 r-xp 00000000 08:01 47225      /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b6f4a000-b6f4b000 rw-p 00005000 08:01 47225      /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b6f4b000-b6f55000 r--p 00000000 08:01 72871      /usr/share/locale-langpack/pt_BR/LC_MESSAGES/glib20.mo
b6f55000-b6f6c000 r--p 00000000 08:01 49407      /usr/share/locale-langpack/pt/LC_MESSAGES/libc.mo
b6f6c000-b6f86000 r--p 00000000 08:01 134442     /usr/share/locale-langpack/pt_BR/LC_MESSAGES/libc.mo
b6f86000-b6f97000 r-xp 00000000 08:01 11627      /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b6f97000-b6f98000 rw-p 00011000 08:01 11627      /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b6f98000-b6fbc000 r--p 00000000 08:01 72608      /usr/share/locale-langpack/pt/LC_MESSAGES/gtk20-properties.mo
b6fbc000-b6fc8000 r--p 00000000 08:01 134241     /usr/share/locale-langpack/pt/LC_MESSAGES/xsane.mo
b6fc8000-b6feb000 r--p 00000000 08:01 72799      /usr/share/locale-langpack/pt_BR/LC_MESSAGES/gtk20-properties.mo
b6feb000-b6ff4000 r-xp 00000000 08:01 5950       /lib/tls/i686/cmov/libnss_files-2.7.so
b6ff4000-b6ff6000 rw-p 00008000 08:01 5950       /lib/tls/i686/cmov/libnss_files-2.7.so
b6ff6000-b6ffe000 r-xp 00000000 08:01 5954       /lib/tls/i686/cmov/libnss_nis-2.7.so
b6ffe000-b7000000 rw-p 00007000 08:01 5954       /lib/tls/i686/cmov/libnss_nis-2.7.so
b7000000-b7014000 r-xp 00000000 08:01 5944       /lib/tls/i686/cmov/libnsl-2.7.so
b7014000-b7016000 rw-p 00013000 08:01 5944       /lib/tls/i686/cmov/libnsl-2.7.so
b7016000-b7018000 rw-p b7016000 00:00 0 
b7018000-b701f000 r-xp 00000000 08:01 5946       /lib/tls/i686/cmov/libnss_compat-2.7.so
b701f000-b7021000 rw-p 00006000 08:01 5946       /lib/tls/i686/cmov/libnss_compat-2.7.so
b7021000-b7022000 rw-s 00000000 00:09 589839     /SYSVeca86420 (deleted)
b7022000-b702f000 r--p 00000000 08:01 134302     /usr/share/locale-langpack/pt_BR/LC_MESSAGES/xsane.mo
b702f000-b703f000 r--p 00000000 08:01 72690      /usr/share/locale-langpack/pt/LC_MESSAGES/gtk20.mo
b703f000-b704f000 r--p 00000000 08:01 72868      /usr/share/locale-langpack/pt_BR/LC_MESSAGES/gtk20.mo
b704f000-b708e000 r--p 00000000 08:01 12232      /usr/lib/locale/pt_BR.utf8/LC_CTYPE
b708e000-b708f000 r--p 00000000 08:01 12380      /usr/lib/locale/pt_BR.utf8/LC_NUMERIC
b708f000-b7090000 r--p 00000000 08:01 15048      /usr/lib/locale/pt_BR.utf8/LC_TIME
b7090000-b7171000 r--p 00000000 08:01 12231      /usr/lib/locale/pt_BR.utf8/LC_COLLATE
b7171000-b7172000 r--p 00000000 08:01 15049      /usr/lib/locale/pt_BR.utf8/LC_MONETARY
b7172000-b7175000 rw-p b7172000 00:00 0 
b7175000-b7179000 r-xp 00000000 08:01 8405       /usr/lib/libXdmcp.so.6.0.0
b7179000-b717a000 rw-p 00003000 08:01 8405       /usr/lib/libXdmcp.so.6.0.0
b717a000-b717c000 r-xp 00000000 08:01 8394       /usr/lib/libXau.so.6.0.0
b717c000-b717d000 rw-p 00001000 08:01 8394       /usr/lib/libXau.so.6.0.0
b717d000-b719c000 r-xp 00000000 08:01 8631       /usr/lib/libexpat.so.1.5.2
b719c000-b719e000 rw-p 0001e000 08:01 8631       /usr/lib/libexpat.so.1.5.2
b719e000-b719f000 rw-p b719e000 00:00 0 
b719f000-b71b6000 r-xp 00000000 08:01 183040     /usr/lib/libxcb.so.1.0.0
b71b6000-b71b7000 rw-p 00016000 08:01 183040     /usr/lib/libxcb.so.1.0.0
b71b7000-b71b8000 r-xp 00000000 08:01 9233       /usr/lib/libxcb-xlib.so.0.0.0
b71b8000-b71b9000 rw-p 00000000 08:01 9233       /usr/lib/libxcb-xlib.so.0.0.0
b71b9000-b71bf000 r-xp 00000000 08:01 8952       /usr/lib/libltdl.so.3.1.6
b71bf000-b71c0000 rw-p 00005000 08:01 8952       /usr/lib/libltdl.so.3.1.6
b71c0000-b71e6000 r-xp 00000000 08:01 9053       /usr/lib/libpcre.so.3.12.1
b71e6000-b71e7000 rw-p 00026000 08:01 9053       /usr/lib/libpcre.so.3.12.1
b71e7000-b71fe000 r-xp 00000000 08:01 2458       /lib/libselinux.so.1
b71fe000-b7200000 rw-p 00016000 08:01 2458       /lib/libselinux.so.1
b7200000-b7201000 rw-p b7200000 00:00 0 
b7201000-b720b000 r-xp 00000000 08:01 2397       /lib/libgcc_s.so.1
b720b000-b720c000 rw-p 0000a000 08:01 2397       /lib/libgcc_s.so.1
b720c000-b72f4000 r-xp 00000000 08:01 9172       /usr/lib/libstdc++.so.6.0.9
b72f4000-b72f7000 r--p 000e8000 08:01 9172       /usr/lib/libstdc++.so.6.0.9
b72f7000-b72f9000 rw-p 000eb000 08:01 9172       /usr/lib/libstdc++.so.6.0.9
b72f90Cancelado


```

To try to discover the error executed the following command:

gdb 

file xsane 

run xsane

bt 

```

(gdb) bt
#0  0xb7f92410 in __kernel_vsyscall ()
#1  0xb75d0085 in raise () from /lib/tls/i686/cmov/libc.so.6
#2  0xb75d1a01 in abort () from /lib/tls/i686/cmov/libc.so.6
#3  0xb7608b7c in ?? () from /lib/tls/i686/cmov/libc.so.6
#4  0xb7610a85 in ?? () from /lib/tls/i686/cmov/libc.so.6
#5  0xb76144f0 in free () from /lib/tls/i686/cmov/libc.so.6
#6  0xb6cab276 in __builtin_delete (ptr=0x823a0d0) from /usr/lib/libstdc++-libc6.2-2.so.3
#7  0xb6cab29f in __builtin_vec_delete (ptr=0x823a0d0) from /usr/lib/libstdc++-libc6.2-2.so.3
#8  0xb6ce162b in port::init_mfp_port_control () from /usr/local/lib/sane/libsane-samsung_scx4x21.so.1
#9  0xb6ce211e in device::init_mfp_port_control () from /usr/local/lib/sane/libsane-samsung_scx4x21.so.1
#10 0xb6ce9002 in driver::init_mfp_port_control () from /usr/local/lib/sane/libsane-samsung_scx4x21.so.1
#11 0xb6cea77b in backend::init () from /usr/local/lib/sane/libsane-samsung_scx4x21.so.1
#12 0xb6ceafb1 in sane_samsung_scx4x21_init () from /usr/local/lib/sane/libsane-samsung_scx4x21.so.1
#13 0xb7f7ebbd in init (be=0x822ca98) at dll.c:613
#14 0xb7f7eedd in sane_dll_get_devices (device_list=0x80e87c8, local_only=0) at dll.c:1034
#15 0xb7f7f444 in sane_get_devices (dl=0x80e87c8, local=0) at dll-s.c:15
#16 0x080bb282 in ?? ()
#17 0x080c8a9b in ?? ()
#18 0x080c9d38 in ?? ()
#19 0xb75bb450 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#20 0x0804f511 in ?? ()
(gdb) 

```

I use Ubuntu Linux, kernel 2.6.24-19-386. 

lsusb

```

root@desktop:/home/thiago/source/fix-nopar/i386# lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 04e8:3419 Samsung Electronics Co., Ltd 
Bus 001 Device 003: ID 045e:009d Microsoft Corp. 
Bus 001 Device 001: ID 0000:0000  
root@desktop:/home/thiago/source/fix-nopar/i386# 

``` 

```

root@desktop:/home/thiago/source/fix-nopar/i386# sane-find-scanner -q
found USB scanner (vendor=0x04e8 [Samsung], product=0x3419 [SCX-4x21 Series]) at libusb:001:006
root@desktop:/home/thiago/source/fix-nopar/i386# 

```

Run /opt/Samsung/mfp/bin/Configurator and click and Scanner

```

(gdb) bt
#0  0xb7f99410 in __kernel_vsyscall ()
#1  0xb73bf085 in raise () from /lib/tls/i686/cmov/libc.so.6
#2  0xb73c0a01 in abort () from /lib/tls/i686/cmov/libc.so.6
#3  0xb73f7b7c in ?? () from /lib/tls/i686/cmov/libc.so.6
#4  0xb73ffa85 in ?? () from /lib/tls/i686/cmov/libc.so.6
#5  0xb74034f0 in free () from /lib/tls/i686/cmov/libc.so.6
#6  0xb6ce2276 in __builtin_delete (ptr=0x8159e90) from /usr/lib/libstdc++-libc6.2-2.so.3
#7  0xb6ce229f in __builtin_vec_delete (ptr=0x8159e90) from /usr/lib/libstdc++-libc6.2-2.so.3
#8  0xb6d0a62b in port::init_mfp_port_control () from /usr/local/lib/sane/libsane-samsung_scx4x21.so.1
#9  0xb6d0b11e in device::init_mfp_port_control () from /usr/local/lib/sane/libsane-samsung_scx4x21.so.1
#10 0xb6d12002 in driver::init_mfp_port_control () from /usr/local/lib/sane/libsane-samsung_scx4x21.so.1
#11 0xb6d1377b in backend::init () from /usr/local/lib/sane/libsane-samsung_scx4x21.so.1
#12 0xb6d13fb1 in sane_samsung_scx4x21_init () from /usr/local/lib/sane/libsane-samsung_scx4x21.so.1
#13 0xb6ebebbd in init (be=0x8156880) at dll.c:613
#14 0xb6ebeedd in sane_dll_get_devices (device_list=0x8158cf8, local_only=1) at dll.c:1034
#15 0xb6ebf444 in sane_get_devices (dl=0x8158cf8, local=1) at dll-s.c:15
#16 0xb6ed51a3 in backend::refresh () from /opt/Samsung/mfp/lib/libScannerPlugin.so
#17 0xb6ed4235 in ScannerPlugin::RefreshScannersList () from /opt/Samsung/mfp/lib/libScannerPlugin.so
#18 0xb6ed40c2 in ScannerPlugin::OnActivate () from /opt/Samsung/mfp/lib/libScannerPlugin.so
#19 0x0804ed2d in ?? ()
#20 0x0804e96e in ?? ()
#21 0x08051bbd in ?? ()
#22 0xb795f2cb in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#23 0xb795f4a6 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#24 0xb7d3c6ab in QButtonGroup::clicked () from /usr/lib/libqt-mt.so.3
#25 0xb79f59dc in QButtonGroup::buttonClicked () from /usr/lib/libqt-mt.so.3
#26 0xb7d3c73b in QButtonGroup::qt_invoke () from /usr/lib/libqt-mt.so.3
#27 0xb795f357 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#28 0xb795f13b in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#29 0xb7d3cd28 in QButton::clicked () from /usr/lib/libqt-mt.so.3
#30 0xb79f77d6 in QButton::mouseReleaseEvent () from /usr/lib/libqt-mt.so.3
#31 0xb7997df2 in QWidget::event () from /usr/lib/libqt-mt.so.3
#32 0xb78ff983 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#33 0xb78ff0e5 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#34 0xb7898c6f in QETWidget::translateMouseEvent () from /usr/lib/libqt-mt.so.3
#35 0xb7896a49 in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#36 0xb78ab458 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#37 0xb791307f in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#38 0xb7912f24 in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#39 0xb78ffc00 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#40 0x0804f683 in ?? ()
#41 0xb73aa450 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#42 0x0804d481 in ?? ()

```

The big problem that drive owner is that it brings all the libraries you need it. But many are incompatible with the old and new systems, such as the libtiff3. In ubuntu are already using the libtiff4.

Do not just copy the works libtiff.so.3 in / usr / lib 


Thanks for all.

---

