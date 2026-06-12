---
title: "Google Earth Crashes and becomes unusable on close"
date: 2008-09-02
forum: General Help
---

### Post by Martin_sensei on 2008-09-02
Hello,

I have just re-installed Ubuntu 8.04 from scratch and have put the ATI catelyst 8.8 drivers on the machine.  I then wanted to use google earth:  It installed fine, and was working OK, until I closed the application.

I got the following error:

```

Google Earth has caught signal 11.

Stacktrace from glibc:
  ./googleearth-bin [0x804f403]
  ./googleearth-bin [0x804f916]
  [0xb7f1f420]
  /lib/tls/i686/cmov/libdl.so.2 [0xb6bb8cb4]
  /lib/ld-linux.so.2 [0xb7f2d5d6]
  /lib/tls/i686/cmov/libdl.so.2 [0xb6bb92bc]
  /lib/tls/i686/cmov/libdl.so.2(dlclose+0x2a) [0xb6bb8cea]
  /usr/lib/libGL.so.1 [0xb664e79d]
  /usr/lib/libGL.so.1 [0xb662ec2a]
  /usr/lib/libX11.so.6(_XFreeExtData+0x25) [0xb6a25975]
  /usr/lib/libX11.so.6(_XFreeDisplayStructure+0x2f3) [0xb6a31e53]
  /usr/lib/libX11.so.6(XCloseDisplay+0xf6) [0xb6a1efc6]
  ./libQtGui.so.4 [0xb779d1cb]
  ./libQtGui.so.4(_ZN12QApplicationD1Ev+0x41a) [0xb775693e]
  ./libgoogleearth_lib.so(_ZN5earth6client11ApplicationD1Ev+0x3d5) [0xb7281d55]
  ./googleearth-bin(main+0x2c4) [0x8050bf4]
  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb70b6450]
  ./googleearth-bin [0x804f231]

We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /root/.googleearth/crashlogs/crashlog-FDF1F3D0.txt

This bug report will be sent to Google automatically next time you run
 Google Earth. Its data, which contains no personal information, will help
 us correct problems without bothering you further. If you would rather
 this info not be transmitted, please delete the above file before running
 the program again. If you want bug reports to NEVER be sent, remove the
 above 'crashlogs' directory's read/write permissions.


```

The log shows the following:

```

CRASHLOGVER 1
CRASHLOGID 0xFDF1F3D0
APPVERMAJOR 4
APPVERMINOR 3
APPVERBUILD 7284
APPBUILDDATE Jul  8 2008
APPBUILDTIME 18:49:53
OSTYPE 11
OSVERMAJOR 2
OSVERMINOR 6
OSVERBUILD 24
OSVERPATCH 0
PID 6623
CRASHSIGNAL 11
CRASHTIME 1220334531
PROGRAMUPTIME 52

STACK 0x804f403
STACK 0x804f916
STACK 0xb7f1f420
STACK 0xb6bb8cb4
STACK 0xb7f2d5d6
STACK 0xb6bb92bc
STACK 0xb6bb8cea
STACK 0xb664e79d
STACK 0xb662ec2a
STACK 0xb6a25975
STACK 0xb6a31e53
STACK 0xb6a1efc6
STACK 0xb779d1cb
STACK 0xb775693e
STACK 0xb7281d55
STACK 0x8050bf4
STACK 0xb70b6450
STACK 0x804f231

DSO googleearth-bin/0x8048000/45848
DSO googleearth-bin/0xb7f1f000/1600
DSO libgcc_s.so.1/0xb7f12000/39096
DSO libstdc++.so.6/0xb7e38000/849472
DSO libQtCore.so.4/0xb7c79000/1791040
DSO libQtGui.so.4/0xb7649000/6344640
DSO libQt3Support.so.4/0xb7411000/2257108
DSO libQtNetwork.so.4/0xb738c000/532172
DSO libQtXml.so.4/0xb733d000/314624
DSO libQtSql.so.4/0xb7314000/157044
DSO libgoogleearth_lib.so/0xb7221000/958689
DSO libm.so.6/0xb71ef000/143140
DSO libc.so.6/0xb70a0000/1346856
DSO libpthread.so.0/0xb7088000/80644
DSO libbase.so/0xb6ffd000/544372
DSO libge_net.so/0xb6fc9000/203856
DSO libgeobase.so/0xb6c93000/3261661
DSO libz.so.1/0xb6c7c000/86972
DSO libgthread-2.0.so.0/0xb6c77000/12476
DSO librt.so.1/0xb6c6d000/27472
DSO libglib-2.0.so.0/0xb6bbc000/719948
DSO libdl.so.2/0xb6bb8000/7420
DSO libfreetype.so.6/0xb6b48000/438628
DSO libSM.so.6/0xb6b40000/26384
DSO libICE.so.6/0xb6b27000/83208
DSO libXi.so.6/0xb6b1f000/27668
DSO libXrender.so.1/0xb6b17000/28152
DSO libXrandr.so.2/0xb6b11000/20100
DSO libXfixes.so.3/0xb6b0c000/12628
DSO libXcursor.so.1/0xb6b03000/31268
DSO libXinerama.so.1/0xb6aff000/4752
DSO libXext.so.6/0xb6af1000/51440
DSO libX11.so.6/0xb6a0a000/933472
DSO libIGCore.so/0xb691a000/925528
DSO libapiloader.so/0xb6915000/9288
DSO libauth.so/0xb68c3000/322188
DSO libport.so/0xb68bf000/11612
DSO libcommon.so/0xb67f9000/779640
DSO libcomponentframework.so/0xb67f3000/19224
DSO libmath.so/0xb67d1000/128372
DSO libmoduleframework.so/0xb67c7000/35636
DSO librender.so/0xb678c000/231213
DSO ld-linux.so.2/0xb7f20000/104528
DSO libIGUtils.so/0xb6766000/140876
DSO libIGMath.so/0xb671d000/271892
DSO libminizip.so/0xb6716000/21784
DSO libfusioncommon.so/0xb6712000/11220
DSO libcurl.so.4/0xb66df000/201204
DSO libselinux.so.1/0xb66c6000/91800
DSO libpcre.so.3/0xb669e000/155300
DSO libXau.so.6/0xb669b000/5460
DSO libxcb-xlib.so.0/0xb6699000/2636
DSO libxcb.so.1/0xb6681000/91992
DSO libGL.so.1/0xb6606000/478868
DSO libGLU.so.1/0xb6587000/507779
DSO libfreeimage.so.3/0xb64c4000/770245
DSO libjpeg.so.62/0xb64a0000/139688
DSO libmng.so.1/0xb6443000/364312
DSO libpng12.so.0/0xb641b000/156964
DSO libtiff.so.3/0xb63be000/364328
DSO libXdmcp.so.6/0xb63b9000/15076
DSO libnss_compat.so.2/0xb567b000/25532
DSO libnsl.so.1/0xb5663000/79840
DSO libnss_nis.so.2/0xb5659000/32200
DSO libnss_files.so.2/0xb564e000/35744
DSO libqgif.so/0xb568a000/17104
DSO libqjpeg.so/0xb4643000/29240
DSO libnss_mdns4_minimal.so.2/0xb4569000/5908
DSO libnss_dns.so.2/0xb4563000/15000
DSO libresolv.so.2/0xb075e000/60744

```

Any ideas what has happened?

If I try and start google earth again, the container loads, but I never get back to the earth.  The only way I can use it again is to completely re-install it.

Cheers

Martin

---

### Post by Martin_sensei on 2008-09-03
Hello again all,

I have discovered that the previous release of Google Earth (4.2) does not crash in this manner, it seems only the beta 4.3 does.  

Is anyone else experiencing problems with Google Earth beta 4.3?

Cheers

Martin

---

### Post by 7raTEYdCql on 2008-09-03
I have a similar problem. google earth just shows me a dark sky and nothing more, No matter how much i zoom in.

---

### Post by Martin_sensei on 2008-09-03
Is that the beta or the last release?

Have you tried waiting for ages?  I just had the sky, and I left it for an hour, and on my return I had the world.  However it crashed again when I closed it.

---

