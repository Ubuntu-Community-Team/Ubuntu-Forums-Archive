---
title: "Songbird won't run"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by billdotson on 2009-08-05
I downloaded the latest songbird and ran the executable and all it did was output all this:

bill@bill-desktop:~/Songbird$ ./songbird
*** glibc detected *** ././songbird-bin: free(): invalid pointer: 0xb1550aa0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7e47604]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7e495b6]
/usr/lib/libvisual-0.4.so.0(visual_mem_free+0x21)[0xb1735141]
/usr/lib/libvisual-0.4.so.0[0xb172c407]
/usr/lib/libvisual-0.4.so.0(visual_plugin_get_list+0x73)[0xb172c5e3]
/usr/lib/libvisual-0.4.so.0(visual_init+0x291)[0xb173bec1]
/usr/lib/gstreamer-0.10/libgstlibvisual.so[0xb25ac273]
/home/bill/Songbird/lib/libgstreamer-0.10.so[0xb3456b2a]
/home/bill/Songbird/lib/libgstreamer-0.10.so(gst_plugin_load_file+0x93f)[0xb34576f1]
/home/bill/Songbird/lib/libgstreamer-0.10.so[0xb3463ab6]
/home/bill/Songbird/lib/libgstreamer-0.10.so(gst_registry_scan_path+0x135)[0xb3463c5b]
/home/bill/Songbird/lib/libgstreamer-0.10.so[0xb340f34f]
/home/bill/Songbird/lib/libgstreamer-0.10.so[0xb340f83b]
/home/bill/Songbird/lib/libgstreamer-0.10.so[0xb340fea6]
/home/bill/Songbird/lib/libgstreamer-0.10.so[0xb341046e]
/usr/lib/libglib-2.0.so.0(g_option_context_parse+0x5ab)[0xb6c33dcb]
/home/bill/Songbird/lib/libgstreamer-0.10.so(gst_init_check+0xf1)[0xb340e60b]
/home/bill/Songbird/lib/libgstreamer-0.10.so(gst_init+0x32)[0xb340e715]
/home/bill/Songbird/lib/sbGStreamerMediacore.so(_ZN18sbGStreamerService4InitEv+0x9ff)[0xb32da9e7]
/home/bill/Songbird/lib/sbGStreamerMediacore.so[0xb32e3a01]
/home/bill/Songbird/lib/sbGStreamerMediacore.so[0xb32f7a56]
/home/bill/Songbird/xulrunner/libxul.so[0xb7702b89]
/home/bill/Songbird/xulrunner/libxul.so[0xb770204b]
/home/bill/Songbird/lib/sbGStreamerMediacore.so[0xb32f4a3f]
/home/bill/Songbird/lib/sbGStreamerMediacore.so[0xb32f4a69]
/home/bill/Songbird/lib/sbGStreamerMediacore.so[0xb32f4215]
/home/bill/Songbird/lib/sbGStreamerMediacore.so[0xb32e2071]
/home/bill/Songbird/lib/sbGStreamerMediacore.so(_ZN27sbGStreamerMediacoreFactory4InitEv+0x46)[0xb32e28e0]
/home/bill/Songbird/lib/sbGStreamerMediacore.so[0xb32e3961]
/home/bill/Songbird/lib/sbGStreamerMediacore.so[0xb32f7a56]
/home/bill/Songbird/xulrunner/libxul.so[0xb7702b89]
/home/bill/Songbird/components/sbMediacoreManager.so[0xb44551c5]
/home/bill/Songbird/components/sbMediacoreManager.so[0xb44551f2]
/home/bill/Songbird/components/sbMediacoreManager.so[0xb4454a8d]
/home/bill/Songbird/components/sbMediacoreManager.so(_ZN8nsCOMPtrI19sbIMediacoreFactoryEC1ERK15nsCOMPtr_helper+0x2d)[0xb443c159]
/home/bill/Songbird/components/sbMediacoreManager.so(_ZN18sbMediacoreManager4InitEv+0x1b9)[0xb443915b]
/home/bill/Songbird/components/sbMediacoreManager.so[0xb44394f4]
/home/bill/Songbird/xulrunner/libxul.so[0xb76df877]
/home/bill/Songbird/xulrunner/libxul.so[0xb76dfe1c]
/home/bill/Songbird/xulrunner/libxul.so[0xb6f6f7a0]
/home/bill/Songbird/xulrunner/libxul.so(XRE_main+0x19af)[0xb6f6d481]
././songbird-bin[0x8048f40]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7dee775]
././songbird-bin[0x8048bb1]
======= Memory map: ========
08048000-0804e000 r-xp 00000000 08:21 169827     /home/bill/Songbird/songbird-bin
0804e000-0804f000 rw-p 00006000 08:21 169827     /home/bill/Songbird/songbird-bin
08be1000-08c02000 rw-p 08be1000 00:00 0          [heap]
b1500000-b1700000 rw-p b1500000 00:00 0 
b171b000-b1757000 r-xp 00000000 08:21 10296      /usr/lib/libvisual-0.4.so.0.0.0
b1757000-b1758000 r--p 0003b000 08:21 10296      /usr/lib/libvisual-0.4.so.0.0.0
b1758000-b1759000 rw-p 0003c000 08:21 10296      /usr/lib/libvisual-0.4.so.0.0.0
b1759000-b1768000 r-xp 00000000 08:21 2578       /lib/libbz2.so.1.0.4
b1768000-b1769000 r--p 0000f000 08:21 2578       /lib/libbz2.so.1.0.4
b1769000-b176a000 rw-p 00010000 08:21 2578       /lib/libbz2.so.1.0.4
b176a000-b1776000 r-xp 00000000 08:21 178823     /usr/lib/libmjpegutils-1.9.so.0.0.0
b1776000-b1777000 r--p 0000c000 08:21 178823     /usr/lib/libmjpegutils-1.9.so.0.0.0
b1777000-b1778000 rw-p 0000d000 08:21 178823     /usr/lib/libmjpegutils-1.9.so.0.0.0
b1778000-b17a4000 r-xp 00000000 08:21 178824     /usr/lib/libmpeg2encpp-1.9.so.0.0.0
b17a4000-b17a5000 r--p 0002c000 08:21 178824     /usr/lib/libmpeg2encpp-1.9.so.0.0.0
b17a5000-b17a6000 rw-p 0002d000 08:21 178824     /usr/lib/libmpeg2encpp-1.9.so.0.0.0
b17a6000-b17a7000 rw-p b17a6000 00:00 0 
b17b9000-b180e000 r-xp 00000000 08:21 10066      /usr/lib/liboil-0.3.so.0.3.0
b180e000-b180f000 r--p 00054000 08:21 10066      /usr/lib/liboil-0.3.so.0.3.0
b180f000-b1826000 rw-p 00055000 08:21 10066      /usr/lib/liboil-0.3.so.0.3.0
b1826000-b1828000 rw-p b1826000 00:00 0 
b1828000-b18cc000 r-xp 00000000 08:21 176258     /usr/lib/libxvidcore.so.4.1
b18cc000-b18cd000 rw-p 000a3000 08:21 176258     /usr/lib/libxvidcore.so.4.1
b18cd000-b1940000 rw-p b18cd000 00:00 0 
b1940000-b19d3000 r-xp 00000000 08:21 113503     /usr/lib/libx264.so.65
b19d3000-b19d4000 r--p 00093000 08:21 113503     /usr/lib/libx264.so.65
b19d4000-b19d5000 rw-p 00094000 08:21 113503     /usr/lib/libx264.so.65
b19d5000-b19d7000 rw-p b19d5000 00:00 0 
b19d7000-b1a44000 r-xp 00000000 08:21 10192      /usr/lib/libschroedinger-1.0.so.0.1.0
b1a44000-b1a45000 r--p 0006d000 08:21 10192      /usr/lib/libschroedinger-1.0.so.0.1.0
b1a45000-b1a46000 rw-p 0006e000 08:21 10192      /usr/lib/libschroedinger-1.0.so.0.1.0
b1a46000-b1a47000 rw-p b1a46000 00:00 0 
b1a47000-b1a89000 r-xp 00000000 08:21 110566     /usr/lib/libmp3lame.so.0.0.0
b1a89000-b1a8a000 r--p 00042000 08:21 110566     /usr/lib/libmp3lame.so.0.0.0
b1a8a000-b1a8c000 rw-p 00043000 08:21 110566     /usr/lib/libmp3lame.so.0.0.0
b1a8c000-b1abc000 rw-p b1a8c000 00:00 0 
b1abc000-b1af7000 r-xp 00000000 08:21 76789      /usr/lib/libfaad.so.0.0.0
b1af7000-b1af8000 ---p 0003b000 08:21 76789      /usr/lib/libfaad.so.0.0.0
b1af8000-b1af9000 r--p 0003b000 08:21 76789      /usr/lib/libfaad.so.0.0.0
b1af9000-b1afc000 rw-p 0003c000 08:21 

Why is it doing this?

---

### Post by ubunoobie on 2009-08-05
Hi, are you running an nvidia graphics card?

If you are, you may try removing the libvisual-0.4-plugins package in synaptic.

---

### Post by LuisGMarine on 2009-11-08
Don't know if this thread has been dead for a while, but all I can recommend is for you to download that tar.gz from here:

[http://www.getsongbird.com/]("http://www.getsongbird.com/")

and follow the instructions in my signature to help you get songbird running on your computer.  Let me know if you need anymore help, I would deff try songbird out and mess with all the options that it has to offer, very close to replacing iTunes for me.

---

