---
title: "pidgin disappears"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by karolsenk on 2009-01-12
Hi, this is my first post, so be gentle please.

I had Kadu for my gadu gadu protocol, but since I found out that facebook is possible with pidgin, where I can also have GG. 

About half a year ago i had some problems with pidgin, but fixed them. Now however, when I run pidgin with both GG and facebook, it randomly swithes off. I run it in terminal for the output, and it is never the same. Sometimes there is nothing, just a second ago i got:

karol@karol-desktop:~$ pidgin
process 16688: arguments to dbus_pending_call_free_data_slot() were incorrect, assertion "*slot_p >= 0" failed in file dbus-pending-call.c line 749.
This is normally a bug in some application using the D-Bus library.
*** glibc detected *** pidgin: free(): invalid pointer: 0xb3e0f6e0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb75c7a85]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb75cb4f0]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb77f1b51]
/usr/lib/libgstreamer-0.10.so.0[0xb7e6f2ee]
/usr/lib/libgstreamer-0.10.so.0[0xb7ea2e73]
/usr/lib/libgstreamer-0.10.so.0[0xb7e8e794]
/usr/lib/libgobject-2.0.so.0(g_object_unref+0x16b)[0xb786f8cb]
/usr/lib/libgstreamer-0.10.so.0(gst_object_unref+0x3e)[0xb7e6d68e]
/usr/lib/libgstreamer-0.10.so.0(gst_object_replace+0xa7)[0xb7e6eb77]
/usr/lib/libgstreamer-0.10.so.0[0xb7e8e802]
/usr/lib/libgstreamer-0.10.so.0[0xb7e90276]
/usr/lib/libgobject-2.0.so.0(g_object_unref+0xcc)[0xb786f82c]
/usr/lib/libgstreamer-0.10.so.0(gst_object_unref+0x3e)[0xb7e6d68e]
/usr/lib/libgstreamer-0.10.so.0(gst_object_unparent+0xbc)[0xb7e6dd2c]
/usr/lib/libgstreamer-0.10.so.0(gst_element_remove_pad+0x1a4)[0xb7e86be4]
/usr/lib/libgstreamer-0.10.so.0[0xb7e89372]
/usr/lib/libgstreamer-0.10.so.0[0xb7e778d3]
/usr/lib/libgobject-2.0.so.0(g_object_unref+0xcc)[0xb786f82c]
/usr/lib/libgstreamer-0.10.so.0(gst_object_unref+0x3e)[0xb7e6d68e]
/usr/lib/libgstreamer-0.10.so.0(gst_object_replace+0xa7)[0xb7e6eb77]
/usr/lib/libgstreamer-0.10.so.0[0xb7e77879]
/usr/lib/gstreamer-0.10/libgstgconfelements.so[0xb4168ed2]
/usr/lib/gstreamer-0.10/libgstgconfelements.so[0xb41660b7]
/usr/lib/libgobject-2.0.so.0(g_object_unref+0xcc)[0xb786f82c]
/usr/lib/libgstreamer-0.10.so.0(gst_object_unref+0x3e)[0xb7e6d68e]
/usr/lib/libgstreamer-0.10.so.0[0xb7e7387f]
/usr/lib/libgstreamer-0.10.so.0(gst_bin_remove+0x8c)[0xb7e7101c]
/usr/lib/libgstreamer-0.10.so.0[0xb7e77891]
/usr/lib/libgobject-2.0.so.0(g_object_unref+0xcc)[0xb786f82c]
/usr/lib/libgstreamer-0.10.so.0(gst_object_unref+0x3e)[0xb7e6d68e]
/usr/lib/libgstreamer-0.10.so.0(gst_object_replace+0xa7)[0xb7e6eb77]
/usr/lib/libgstreamer-0.10.so.0[0xb7e77879]
/usr/lib/libgstreamer-0.10.so.0[0xb7ea49fd]
/usr/lib/gstreamer-0.10/libgstplaybin.so[0xb4061960]
/usr/lib/gstreamer-0.10/libgstplaybin.so[0xb405522b]
/usr/lib/libgobject-2.0.so.0(g_object_unref+0xcc)[0xb786f82c]
/usr/lib/libgstreamer-0.10.so.0(gst_object_unref+0x3e)[0xb7e6d68e]
/usr/lib/libgstreamer-0.10.so.0[0xb7e97072]
/usr/lib/libgstreamer-0.10.so.0(gst_mini_object_unref+0xe4)[0xb7e97784]
/usr/lib/libgstreamer-0.10.so.0[0xb7e7a0eb]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x176)[0xb77e9cc6]
/usr/lib/libglib-2.0.so.0[0xb77ed083]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1e7)[0xb77ed467]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7aff264]
pidgin(main+0xc61)[0x80ca9ea]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7572450]
pidgin[0x806d8c1]
======= Memory map: ========
08048000-0811d000 r-xp 00000000 08:02 4147847    /usr/bin/pidgin
0811d000-08120000 rw-p 000d5000 08:02 4147847    /usr/bin/pidgin
08120000-08706000 rw-p 08120000 00:00 0          [heap]
b0194000-b0195000 ---p b0194000 00:00 0 
b0195000-b0995000 rw-p b0195000 00:00 0 
b0995000-b0996000 ---p b0995000 00:00 0 
b0996000-b1196000 rw-p b0996000 00:00 0 
b1196000-b1197000 ---p b1196000 00:00 0 
b1197000-b1997000 rw-p b1197000 00:00 0 
b1b98000-b1b99000 ---p b1b98000 00:00 0 
b1b99000-b2399000 rw-p b1b99000 00:00 0 
b2399000-b239a000 ---p b2399000 00:00 0 
b239a000-b2b9a000 rw-p b239a000 00:00 0 
b2d9b000-b2d9c000 ---p b2d9b000 00:00 0 
b2d9c000-b359c000 rw-p b2d9c000 00:00 0 
b359c000-b35e9000 r-xp 00000000 08:02 4145964    /usr/lib/libpulse.so.0.4.1
b35e9000-b35ea000 rw-p 0004c000 08:02 4145964    /usr/lib/libpulse.so.0.4.1
b35ff000-b3600000 ---p b35ff000 00:00 0 
b3600000-b3e75000 rw-p b3600000 00:00 0 
b3e75000-b3f00000 ---p b3e75000 00:00 0 
b3f0c000-b3f1b000 r-xp 00000000 08:02 4145442    /usr/lib/libhal.so.1.0.0
b3f1b000-b3f1c000 rw-p 0000e000 08:02 4145442    /usr/lib/libhal.so.1.0.0
b3f23000-b3f30000 r-xp 00000000 08:02 4161804    /usr/lib/gstreamer-0.10/libgstpulse.so
b3f30000-b3f31000 rw-p 0000d000 08:02 4161804    /usr/lib/gstreamer-0.10/libgstpulse.so
b3f31000-b3f54000 r-xp 00000000 08:02 1179880    /usr/lib/libgstcontroller-0.10.so.0.16.0
b3f54000-b3f55000 rw-p 00023000 08:02 1179880    /usr/lib/libgstcontroller-0.10.so.0.16.0
b3f55000-b3fa7000 r-xp 00000000 08:02 4146866    /usr/lib/liboil-0.3.so.0.2.0
b3fa7000-b3fbe000 rw-p 00052000 08:02 4146866    /usr/lib/liboil-0.3.so.0.2.0
b3fbe000-b3fc0000 rw-p b3fbe000 00:00 0 
b3fc9000-b3fce000 r-xp 00000000 08:02 4162612    /usr/lib/gstreamer-0.10/libgstautodetect.so
b3fce000-b3fcf000 rw-p 00004000 08:02 4162612    /usr/lib/gstreamer-0.10/libgstautodetect.so
b3fcf000-b3fd4000 r-xp 00000000 08:02 4162646    /usr/lib/gstreamer-0.10/libgsthalelements.so
b3fd4000-b3fd5000 rw-p 00004000 08:02 4162646    /usr/lib/gstreamer-0.10/libgsthalelements.so
b3fd5000-b3fde000 r-xp 00000000 08:02 13926406   /usr/lib/gstreamer-0.10/libgstaudioresample.so
b3fde000-b3fdf000 rw-p 00008000 08:02 13926406   /usr/lib/gstreamer-0.10/libgstaudioresample.so
b3fdf000-b3fec000 r-xp 00000000 08:02 4147060    /usr/lib/libgsttag-0.10.so.0.13.0
b3fec000-b3fed000 rw-p 0000c000 08:02 4147060    /usr/lib/libgsttag-0.10.so.0.13.0
b3fed000-b4007000 r-xp 00000000 08:02 4146023    /usr/lib/libgstaudio-0.10.so.0.13.0
b4007000-b4008000 rw-p 0001a000 08:02 4146023    /usr/lib/libgstaudio-0.10.so.0.13.0
b4008000-b4012000 r-xp 00000000 08:02 4146779    /usr/lib/libgstriff-0.10.so.0.13.0
b4012000-b4013000 rw-p 00009000 08:02 4146779    /usr/lib/libgstriff-0.10.so.0.13.0
b4016000-b401a000 r-xp 00000000 08:02 13926441   /usr/lib/gstreamer-0.10/libgstvolume.so
b401a000-b401b000 rw-p 00003000 08:02 13926441   /usr/lib/gstreamer-0.10/libgstvolume.so
b401b000-b4027000 r-xp 00000000 08:02 13926404   /usr/lib/gstreamer-0.10/libgstaudioconvert.so
b4027000-b4028000 rw-p 0000b000 08:02 13926404   /usr/lib/gstreamer-0.10/libgstaudioconvert.so
b4028000-b4033000 r-xp 00000000 08:02 4162676    /usr/lib/gstreamer-0.10/libgstwavparse.so
b4033000-b4034000 rw-p 0000a000 08:02 4162676    /usr/lib/gstreamer-0.10/libgstwavparse.so
b4034000-b403f000 r-xp 00000000 08:02 13926432   /usr/lib/gstreamer-0.10/libgsttypefindfunctions.so
b403f000-b4041000 rw-p 0000b000 08:02 13926432   /usr/lib/gstreamer-0.10/libgsttypefindfunctions.so
b4041000-b404b000 r-xp 00000000 08:02 4146595    /usr/lib/libgstpbutils-0.10.so.0.13.0
b404b000-b404c000 rw-p 0000a000 08:02 4146595    /usr/lib/libgstpbutils-0.10.so.0.13.0
b404c000-b406e000 r-xp 00000000 08:02 13926425   /usr/lib/gstreamer-0.10/libgstplaybin.so
b406e000-b406f000 rw-p 00022000 08:02 13926425   /usr/lib/gstreamer-0.10/libgstplaybin.so
b406f000-b4098000 r-xp 00000000 08:02 1179844    /usr/lib/libgstbase-0.10.so.0.16.0
b4098000-b4099000 rw-p 00029000 08:02 1179844    /usr/lib/libgstbase-0.10.so.0.16.0
b4099000-b40c1000 r-xp 00000000 08:02 4162005    /usr/lib/gstreamer-0.10/libgstcoreelements.so
b40c1000-b40c2000 rw-p 00028000 08:02 4162005    /usr/lib/gstreamer-0.10/libgstcoreelements.so
b40c2000-b4122000 rw-s 00000000 00:09 25886783   /SYSV00000000 (deleted)
b4122000-b4141000 r-xp 00000000 08:02 4146960    /usr/lib/libjpeg.so.62.0.0
b4141000-b4142000 rw-p 0001e000 08:02 4146960    /usr/lib/libjpeg.so.62.0.0
b4142000-b414c000 r-xp 00000000 08:02 4146641    /usr/lib/libgstinterfaces-0.10.so.0.13.0
b414c000-b414d000 rw-p 00009000 08:02 4146641    /usr/lib/libgstinterfaces-0.10.so.0.13.0
b414d000-b4156000 r-xp 00000000 08:02 13926411   /usr/lib/gstreamer-0.10/libgstdecodebin.so
b4156000-b4157000 rw-p 00008000 08:02 13926411   /usr/lib/gstreamer-0.10/libgstdecodebin.so
b4157000-b415b000 r-xp 00000000 08:02 12877891   /lib/tls/i686/cmov/libnss_dns-2.7.so
b415b000-b415d000 rw-p 00003000 08:02 12877891   /lib/tls/i686/cmov/libnss_dns-2.7.so
b415d000-b415f000 r-xp 00000000 08:02 8011962    /lib/libnss_mdns4_minimal.so.2
b415f000-b4160000 rw-p 00001000 08:02 8011962    /lib/libnss_mdns4_minimal.so.2
b4160000-b4163000 r-xp 00000000 08:02 8011819    /lib/libcap.so.1.10
b4163000-b4164000 rw-p 00002000 08:02 8011819    /lib/libcap.so.1.10
b4164000-b416b000 r-xp 00000000 08:02 4162634    /usr/lib/gstreamer-0.10/libgstgconfelements.so
b416b000-b416c000 rw-p 00006000 08:02 4162634    /usr/lib/gstreamer-0.10/libgstgconfelements.so
b416c000-b4170000 r-xp 00000000 08:02 8536620    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-jpeg.so
b4170000-b4171000 rw-p 00003000 08:02 8536620    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-jpeg.so
b4171000-b4173000 r-xp 00000000 08:02 4162465    /usr/lib/gconv/CP1250.so
b4173000-b4175000 rw-p 00001000 08:02 4162465    /usr/lib/gconv/CP1250.so
b4175000-b4176000 ---p b4175000 00:00 0 
b4176000-b4976000 rw-p b4176000 00:00 0 
b4976000-b49d6000 rw-s 00000000 00:09 25755691   /SYSV00000000 (deleted)
b49d6000-b4ada000 rw-p b49d6000 00:00 0 
b4ada000-b4b61000 r--p 00000000 08:02 12189698   /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttfAborted
karol@karol-desktop:~$ 

at other time it was:
 Segmentation fault

Help!

What is wrong?

---

### Post by karolsenk on 2009-01-12
Anyone?

---

### Post by edog76 on 2009-01-22
Same issue, I have not yet solved it. I'm waiting to see what develops in [*this thread*](http://code.google.com/p/pidgin-facebookchat/issues/detail?id=319&colspec=ID%20Type%20Status%20Summary%20Stars%20Opened%20Modified) at google-code

---

### Post by Ng Oon-Ee on 2009-01-22
I do get occasional crashes with Pidgin. What helped a bit was disabling 'Nautilus Integration'. Its more than that, though, it sometimes crashes in Windows as well so it can't just be Nautilus.

I've never been able to pin down exactly why it happens. Most days my Pidgin just sits there morning to night with no complaints, so I'll leave the bug-hunting to others, or myself when I have the time.

---

