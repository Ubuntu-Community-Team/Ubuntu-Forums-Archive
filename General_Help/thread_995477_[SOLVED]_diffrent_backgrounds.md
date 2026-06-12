---
title: "[SOLVED] diffrent backgrounds"
date: 2008-11-27
forum: General Help
---

### Post by jmacx81 on 2008-11-27
I used to have diffrent backgrounds on my cube when I had Ubuntu 7 but can't remember how to do it. I remember doing something with gcomf config but not sure what else

mac

---

### Post by James M on 2008-11-27
> **jmacx81 said:**
> I used to have diffrent backgrounds on my cube when I had Ubuntu 7 but can't remember how to do it. I remember doing something with gcomf config but not sure what else

mac

Backgrounds? Like behind the cube? Or do you mean different wallpapers for each desktop on the cube.

---

### Post by jrharvey on 2008-11-27
Just download the compiz manager. Theres a setting for the background under the cube setting.

---

### Post by binbash on 2008-11-28
you gonna open gconf-editor and go to apps > nautilus, you will disable show desktop there and you gonna enable wallpaper plugin at compiz-fusion.

---

### Post by blazemore on 2008-11-28
> **binbash said:**
> you gonna open gconf-editor and go to apps > nautilus, you will disable show desktop there and you gonna enable wallpaper plugin at compiz-fusion.

Problem with that is it disables desktop icons.

---

### Post by jmacx81 on 2008-11-28
> **James M said:**
> Backgrounds? Like behind the cube? Or do you mean different wallpapers for each desktop on the cube.

Different wall papers for each desktop on the cube, I've got the cube caps on and know how to change them but not sure how to do the wall papers.

---

### Post by jmacx81 on 2008-11-28
> **blazemore said:**
> Problem with that is it disables desktop icons.

Ah yes I remember that. I don't think it bothered me to much but I think it might now. Any way to have different wallpapers and keep my icons?

---

### Post by jmacx81 on 2008-11-30
> **binbash said:**
> you gonna open gconf-editor and go to apps > nautilus, you will disable show desktop there and you gonna enable wallpaper plugin at compiz-fusion.

Ok I've unclicked show desktop in nautilus and I have enabled wall papers in compiz-fusion and put 4 images in, When I reboot it shows the image for desktop one but once ubuntu starts up it goes back to the default background.

---

### Post by binbash on 2008-11-30
First of all this method works %100, i tested it.Try disabling wallpaper plugin and enable it again.Also be sure after restart, compiz is enabled .If it still does not work, start compiz fusion at terminal and write the output here

---

### Post by jmacx81 on 2008-11-30
and bad things happed

mac@mac-laptop:~$ sudo compiz fusion
[sudo] password for mac: 
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'fusion'
/usr/bin/compiz.real (core) - Warn: Plugin 'core' already active
*** glibc detected *** /usr/bin/compiz.real: corrupted double-linked list: 0x0000000000fc1d80 ***
======= Backtrace: =========
/lib/libc.so.6[0x7f7806bbd938]
/lib/libc.so.6[0x7f7806bbfd58]
/lib/libc.so.6(cfree+0x76)[0x7f7806bbff86]
/usr/lib/libGL.so.1[0x7f78090f5aca]
======= Memory map: ========
00400000-0043b000 r-xp 00000000 08:01 1409196                            /usr/bin/compiz.real
0063a000-0063b000 r--p 0003a000 08:01 1409196                            /usr/bin/compiz.real
0063b000-0063c000 rw-p 0003b000 08:01 1409196                            /usr/bin/compiz.real
00e2b000-010f2000 rw-p 00e2b000 00:00 0                                  [heap]
7f77ffde8000-7f77ffdfe000 r-xp 00000000 08:01 4399215                    /lib/libgcc_s.so.1
7f77ffdfe000-7f77ffffe000 ---p 00016000 08:01 4399215                    /lib/libgcc_s.so.1
7f77ffffe000-7f77fffff000 r--p 00016000 08:01 4399215                    /lib/libgcc_s.so.1
7f77fffff000-7f7800000000 rw-p 00017000 08:01 4399215                    /lib/libgcc_s.so.1
7f7800000000-7f7800021000 rw-p 7f7800000000 00:00 0 
7f7800021000-7f7804000000 ---p 7f7800021000 00:00 0 
7f78040a8000-7f78040ac000 r-xp 00000000 08:01 2400620                    /usr/lib/compizconfig/backends/libini.so
7f78040ac000-7f78042ab000 ---p 00004000 08:01 2400620                    /usr/lib/compizconfig/backends/libini.so
7f78042ab000-7f78042ac000 r--p 00003000 08:01 2400620                    /usr/lib/compizconfig/backends/libini.so
7f78042ac000-7f78042ad000 rw-p 00004000 08:01 2400620                    /usr/lib/compizconfig/backends/libini.so
7f78042ad000-7f78042c4000 r-xp 00000000 08:01 2375788                    /usr/lib/libcompizconfig.so.0.0.0
7f78042c4000-7f78044c3000 ---p 00017000 08:01 2375788                    /usr/lib/libcompizconfig.so.0.0.0
7f78044c3000-7f78044c4000 r--p 00016000 08:01 2375788                    /usr/lib/libcompizconfig.so.0.0.0
7f78044c4000-7f78044c5000 rw-p 00017000 08:01 2375788                    /usr/lib/libcompizconfig.so.0.0.0
7f78046ca000-7f78048ca000 rw-s 5446b000 00:0e 15835                      /dev/nvidia0
7f7804af6000-7f7804b2c000 rw-p 7f7804af6000 00:00 0 
7f7804b2c000-7f7804b4e000 rw-s 00000000 00:09 0                          /SYSV00000000 (deleted)
7f7804b4e000-7f7804b4f000 r-xp 00000000 08:01 3031249                    /usr/lib/tls/libnvidia-tls.so.177.80
7f7804b4f000-7f7804c4e000 ---p 00001000 08:01 3031249                    /usr/lib/tls/libnvidia-tls.so.177.80
7f7804c4e000-7f7804c4f000 rw-p 00000000 08:01 3031249                    /usr/lib/tls/libnvidia-tls.so.177.80
7f7804c4f000-7f7805865000 r-xp 00000000 08:01 2375836                    /usr/lib/libGLcore.so.177.80
7f7805865000-7f7805965000 ---p 00c16000 08:01 2375836                    /usr/lib/libGLcore.so.177.80
7f7805965000-7f7805cf3000 rwxp 00c16000 08:01 2375836                    /usr/lib/libGLcore.so.177.80
7f7805cf3000-7f7805d03000 rwxp 7f7805cf3000 00:00 0 
7f7805d03000-7f7805d1a000 r-xp 00000000 08:01 2376296                    /usr/lib/libz.so.1.2.3.3
7f7805d1a000-7f7805f19000 ---p 00017000 08:01 2376296                    /usr/lib/libz.so.1.2.3.3
7f7805f19000-7f7805f1b000 rw-p 00016000 08:01 2376296                    /usr/lib/libz.so.1.2.3.3
7f7805f1b000-7f7805f24000 r-xp 00000000 08:01 1433933                    /usr/lib/libXrender.so.1.3.0
7f7805f24000-7f7806123000 ---p 00009000 08:01 1433933                    /usr/lib/libXrender.so.1.3.0
7f7806123000-7f7806124000 r--p 00008000 08:01 1433933                    /usr/lib/libXrender.so.1.3.0
7f7806124000-7f7806125000 rw-p 00009000 08:01 1433933                    /usr/lib/libXrender.so.1.3.0
7f7806125000-7f780612a000 r-xp 00000000 08:01 2375967                    /usr/lib/libXdmcp.so.6.0.0
7f780612a000-7f7806329000 ---p 00005000 08:01 2375967                    /usr/lib/libXdmcp.so.6.0.0
7f7806329000-7f780632a000 rw-p 00004000 08:01 2375967                    /usr/lib/libXdmcp.so.6.0.0
7f780632a000-7f780632c000 r-xp 00000000 08:01 2375698                    /usr/lib/libXau.so.6.0.0
7f780632c000-7f780652b000 ---p 00002000 08:01 2375698                    /usr/lib/libXau.so.6.0.0
7f780652b000-7f780652c000 rw-p 00001000 08:01 2375698                    /usr/lib/libXau.so.6.0.0
7f780652c000-7f780652d000 r-xp 00000000 08:01 1433929                    /usr/lib/libxcb-xlib.so.0.0.0
7f780652d000-7f780672c000 ---p 00001000 08:01 1433929                    /usr/lib/libxcb-xlib.so.0.0.0
7f780672c000-7f780672d000 r--p 00000000 08:01 1433929                    /usr/lib/libxcb-xlib.so.0.0.0
7f780672d000-7f780672e000 rw-p 00001000 08:01 1433929                    /usr/lib/libxcb-xlib.so.0.0.0
7f780672e000-7f780673e000 r-xp 00000000 08:01 2376085                    /usr/lib/libXext.so.6.4.0
7f780673e000-7f780693e000 ---p 00010000 08:01 2376085                    /usr/lib/libXext.so.6.4.0
7f780693e000-7f7806940000 rw-p 00010000 08:01 2376085                    /usr/lib/libXext.so.6.4.0
7f7806940000-7f7806942000 r-xp 00000000 08:01 4399247                    /lib/libdl-2.8.90.so
7f7806942000-7f7806b42000 ---p 00002000 08:01 4399247                    /lib/libdl-2.8.90.so
7f7806b42000-7f7806b43000 r--p 00002000 08:01 4399247                    /lib/libdl-2.8.90.so
7f7806b43000-7f7806b44000 rw-p 00003000 08:01 4399247                    /lib/libdl-2.8.90.so
7f7806b44000-7f7806cad000 r-xp 00000000 08:01 4399224                    /lib/libc-2.8.90.so
7f7806cad000-7f7806eac000 ---p 00169000 08:01 4399224                    /lib/libc-2.8.90.so
7f7806eac000-7f7806eb0000 r--p 00168000 08:01 4399224                    /lib/libc-2.8.90.so
7f7806eb0000-7f7806eb1000 rw-p 0016c000 08:01 4399224                    /lib/libc-2.8.90.so
7f7806eb1000-7f7806eb6000 rw-p 7f7806eb1000 00:00 0 
7f7806eb6000-7f7806f3a000 r-xp 00000000 08:01 4399248                    /lib/libm-2.8.90.so
7f7806f3a000-7f7807139000 ---p 00084000 08:01 4399248                    /lib/libm-2.8.90.so
7f7807139000-7f780713a000 r--p 00083000 08:01 4399248                    /lib/libm-2.8.90.so
7f780713a000-7f780713b000 rw-p 00084000 08:01 4399248                    /lib/libm-2.8.90.so
7f780713b000-7f7807144000 r-xp 00000000 08:01 2377780                    /usr/lib/libstartup-notification-1.so.0.0.0
7f7807144000-7f7807343000 ---p 00009000 08:01 2377780                    /usr/lib/libstartup-notification-1.so.0.0.0
7f7807343000-7f7807344000 rw-p 00008000 08:01 2377780                    /usr/lib/libstartup-notification-1.so.0.0.0
7f7807344000-7f7807497000 r-xp 00000000 08:01 1433879                    /usr/lib/libxml2.so.2.6.32
7f7807497000-7f7807696000 ---p 00153000 08:01 1433879                    /usr/lib/libxml2.so.2.6.32
7f7807696000-7f780769e000 r--p 00152000 08:01 1433879                    /usr/lib/libxml2.so.2.6.32
7f780769e000-7f78076a0000 rw-p 0015a000 08:01 1433879                    /usr/lib/libxml2.so.2.6.32
7f78076a0000-7f78076a1000 rw-p 7f78076a0000 00:00 0 
7f78076a1000-7f78076d9000 r-xp 00000000 08:01 2377170                    /usr/lib/libxslt.so.1.1.24
7f78076d9000-7f78078d8000 ---p 00038000 08:01 2377170                    /usr/lib/libxslt.so.1.1.24
7f78078d8000-7f78078d9000 r--p 00037000 08:01 2377170                    /usr/lib/libxslt.so.1.1.24
7f78078d9000-7f78078da000 rw-p 00038000 08:01 2377170                    /usr/lib/libxslt.so.1.1.24
7f78078da000-7f78078f1000 r-xp 00000000 08:01 2376970                    /usr/lib/libICE.so.6.3.0
7f78078f1000-7f7807af0000 ---p 00017000 08:01 2376970                    /usr/lib/libICE.so.6.3.0
7f7807af0000-7f7807af2000 rw-p 00016000 08:01 2376970                    /usr/lib/libICE.so.6.3.0
7f7807af2000-7f7807af5000 rw-p 7f7807af2000 00:00 0 
7f7807af5000-7f7807afd000 r-xp 00000000 08:01 1434058                    /usr/lib/libSM.so.6.0.0
7f7807afd000-7f7807cfc000 ---p 00008000 08:01 1434058                    /usr/lib/libSM.so.6.0.0
7f7807cfc000-7f7807cfd000 r--p 00007000 08:01 1434058                    /usr/lib/libSM.so.6.0.0
7f7807cfd000-7f7807cfe000 rw-p 00008000 08:01 1434058                    /usr/lib/libSM.so.6.0.0
7f7807cfe000-7f7807d07000 r-xp 00000000 08:01 2377013                    /usr/lib/libXcursor.so.1.0.2
7f7807d07000-7f7807f07000 ---p 00009000 08:01 2377013                    /usr/lib/libXcursor.so.1.0.2
7f7807f07000-7f7807f08000 rw-p 00009000 08:01 2377013                    /usr/lib/libXcursor.so.1.0.2
7f7807f08000-7f7807f0a000 r-xp 00000000 08:01 2376395                    /usr/libAborted

---

### Post by binbash on 2008-11-30
dont run it sudo, enter compiz --replace

---

