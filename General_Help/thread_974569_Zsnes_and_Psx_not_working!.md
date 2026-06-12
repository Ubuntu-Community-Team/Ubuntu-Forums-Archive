---
title: "Zsnes and Psx not working!"
date: 2008-11-07
forum: General Help
---

### Post by rick08 on 2008-11-07
I recently upgraded to 8.10 a day before it's release and I just decided now would be a great time to play some playstation or super nintendo games.  I tried to open zsnes and nothing at all happens.  I tried to open Psx and it just flashes and thats all I see of it.  I looked in the zsnes folder to see if the link was bad, but I found only the zsnes config files and thats all.  I hope all I need to do is reinstall the program.  If anyone can help me fix these two emulator that would really be great.  I'm getting tired of OpenArena since i've been playing it for 5 hours straight lol.

---

### Post by Yellow Pasque on 2008-11-07
Try starting the programs from the terminal and see if they produce errors/output.
For zsnes, try starting it without audio to see if that's the issue
```
zsnes -ad null
```

---

### Post by rick08 on 2008-11-07
This is what it spit back.```
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event9. Make sure you have read permissions to it.
Unable to poll /dev/input/event8. Make sure you have read permissions to it.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
*** buffer overflow detected ***: zsnes terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7d1c558]
/lib/tls/i686/cmov/libc.so.6[0xb7d1a680]
zsnes[0x8056c1b]
======= Memory map: ========
08048000-08303000 r-xp 00000000 08:01 4531338    /usr/bin/zsnes
08303000-08304000 r--p 002ba000 08:01 4531338    /usr/bin/zsnes
08304000-08343000 rw-p 002bb000 08:01 4531338    /usr/bin/zsnes
08343000-088f7000 rw-p 08343000 00:00 0 
09ed4000-09f1f000 rw-p 09ed4000 00:00 0          [heap]
b6be2000-b7711000 rw-p b6be2000 00:00 0 
b7711000-b7714000 r-xp 00000000 08:01 5013546    /lib/libcap.so.1.10
b7714000-b7715000 rw-p 00002000 08:01 5013546    /lib/libcap.so.1.10
b7715000-b7763000 r-xp 00000000 08:01 4533724    /usr/lib/libpulse.so.0.4.1
b7763000-b7764000 r--p 0004d000 08:01 4533724    /usr/lib/libpulse.so.0.4.1
b7764000-b7765000 rw-p 0004e000 08:01 4533724    /usr/lib/libpulse.so.0.4.1
b7765000-b7771000 r-xp 00000000 08:01 4533726    /usr/lib/libpulse-simple.so.0.0.1
b7771000-b7772000 r--p 0000b000 08:01 4533726    /usr/lib/libpulse-simple.so.0.0.1
b7772000-b7773000 rw-p 0000c000 08:01 4533726    /usr/lib/libpulse-simple.so.0.0.1
b7773000-b7788000 r-xp 00000000 08:01 4531468    /usr/lib/libICE.so.6.3.0
b7788000-b7789000 rw-p 00014000 08:01 4531468    /usr/lib/libICE.so.6.3.0
b7789000-b778b000 rw-p b7789000 00:00 0 
b778b000-b7792000 r-xp 00000000 08:01 4531522    /usr/lib/libSM.so.6.0.0
b7792000-b7793000 r--p 00006000 08:01 4531522    /usr/lib/libSM.so.6.0.0
b7793000-b7794000 rw-p 00007000 08:01 4531522    /usr/lib/libSM.so.6.0.0
b7794000-b77e1000 r-xp 00000000 08:01 4531545    /usr/lib/libXt.so.6.0.0
b77e1000-b77e5000 rw-p 0004c000 08:01 4531545    /usr/lib/libXt.so.6.0.0
b77e5000-b77fb000 r-xp 00000000 08:01 4531575    /usr/lib/libaudio.so.2.4
b77fb000-b77fc000 r--p 00015000 08:01 4531575    /usr/lib/libaudio.so.2.4
b77fc000-b77fd000 rw-p 00016000 08:01 4531575    /usr/lib/libaudio.so.2.4
b77fd000-b781f000 r-xp 00000000 08:01 4531586    /usr/lib/libaudiofile.so.0.0.2
b781f000-b7822000 rw-p 00021000 08:01 4531586    /usr/lib/libaudiofile.so.0.0.2
b7835000-b785d000 r-xp 00000000 08:01 3702857    /lib/libpcre.so.3.12.1
b785d000-b785e000 r--p 00027000 08:01 3702857    /lib/libpcre.so.3.12.1
b785e000-b785f000 rw-p 00028000 08:01 3702857    /lib/libpcre.so.3.12.1
b785f000-b7914000 r-xp 00000000 08:01 4531237    /usr/lib/libglib-2.0.so.0.1800.2
b7914000-b7915000 r--p 000b4000 08:01 4531237    /usr/lib/libglib-2.0.so.0.1800.2
b7915000-b7916000 rw-p 000b5000 08:01 4531237    /usr/lib/libglib-2.0.so.0.1800.2
b7916000-b791a000 r-xp 00000000 08:01 4531256    /usr/lib/libgthread-2.0.so.0.1800.2
b791a000-b791b000 r--p 00003000 08:01 4531256    /usr/lib/libgthread-2.0.so.0.1800.2
b791b000-b791c000 rw-p 00004000 08:01 4531256    /usr/lib/libgthread-2.0.so.0.1800.2
b791d000-b791f000 r-xp 00000000 08:01 4546639    /usr/lib/ao/plugins-2/libpulse.so
b791f000-b7921000 rw-p 00001000 08:01 4546639    /usr/lib/ao/plugins-2/libpulse.so
b7921000-b792a000 r-xp 00000000 08:01 4530280    /usr/lib/libesd.so.0.2.39
b792a000-b792b000 r--p 00008000 08:01 4530280    /usr/lib/libesd.so.0.2.39
b792b000-b792c000 rw-p 00009000 08:01 4530280    /usr/lib/libesd.so.0.2.39
b792c000-b792d000 r-xp 00000000 08:01 4546636    /usr/lib/ao/plugins-2/libesd.so
b792d000-b792f000 rw-p 00000000 08:01 4546636    /usr/lib/ao/plugins-2/libesd.so
b792f000-b79f2000 r-xp 00000000 08:01 4531801    /usr/lib/libasound.so.2.0.0
b79f2000-b79f4000 r--p 000c2000 08:01 4531801    /usr/lib/libasound.so.2.0.0
b79f4000-b79f7000 rw-p 000c4000 08:01 4531801    /usr/lib/libasound.so.2.0.0
b79f8000-b79f9000 r-xp 00000000 08:01 4546637    /usr/lib/ao/plugins-2/libnas.so
b79f9000-b79fb000 rw-p 00000000 08:01 4546637    /usr/lib/ao/plugins-2/libnas.so
b79fb000-b79fe000 r-xp 00000000 08:01 4531249    /usr/lib/libgmodule-2.0.so.0.1800.2
b79fe000-b79ff000 r--p 00002000 08:01 4531249    /usr/lib/libgmodule-2.0.so.0.1800.2
b79ff000-b7a00000 rw-p 00003000 08:01 4531249    /usr/lib/libgmodule-2.0.so.0.1800.2
b7a00000-b7a05000 r-xp 00000000 08:01 4531573    /usr/lib/libartsc.so.0.0.0
b7a05000-b7a06000 r--p 00004000 08:01 4531573    /usr/lib/libartsc.so.0.0.0
b7a06000-b7a07000 rw-p 00005000 08:01 4531573    /usr/lib/libartsc.so.0.0.0
b7a07000-b7a08000 r-xp 00000000 08:01 4546635    /usr/lib/ao/plugins-2/libarts.so
b7a08000-b7a0a000 rw-p 00000000 08:01 4546635    /usr/lib/ao/plugins-2/libarts.so
b7a0a000-b7a14000 r-xp 00000000 08:01 2596955    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7a14000-b7a15000 r--p 00009000 08:01 2596955    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7a15000-b7a16000 rw-p 0000a000 08:01 2596955    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7a16000-b7a1f000 r-xp 00000000 08:01 2596957    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b7a1f000-b7a20000 r--p 00008000 08:01 2596957    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b7a20000-b7a21000 rw-p 00009000 08:01 2596957    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b7a21000-b7a36000 r-xp 00000000 08:01 2596952    /lib/tls/i686/cmov/libnsl-2.8.90.so
b7a36000-b7a37000 r--p 00014000 08:01 2596952    /lib/tls/i686/cmov/libnsl-2.8.90.so
b7a37000-b7a38000 rw-p 00015000 08:01 2596952    /lib/tls/i686/cmov/libnsl-2.8.90.so
b7a38000-b7a3a000 rw-p b7a38000 00:00 0 
b7a3a000-b7a41000 r-xp 00000000 08:01 2596953    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b7a41000-b7a42000 r--p 00006000 08:01 2596953    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b7a42000-b7a43000 rw-p 00007000 08:01 2596953    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b7a43000-b7a46000 rw-p b7a43000 00:00 0 
b7a46000-b7a4a000 r-xp 00000000 08:01 4531162    /usr/lib/libXdmcp.so.6.0.0
b7a4a000-b7a4b000 rw-p 00003000 08:01 4531162    /usr/lib/libXdmcp.so.6.0.0
b7a4b000-b7a4d000 r-xp 00000000 08:01 4531141    /usr/lib/libXau.so.6.0.0
b7a4d000-b7a4e000 rw-p 00001000 08:01 4531141    /usr/lib/libXau.so.6.0.0
b7a4e000-b7a65000 r-xp 00000000 08:01 4531180    /usr/lib/libxcb.so.1.0.0
b7a65000-b7a66000 r--p 00016000 08:01 4531180    /usr/lib/libxcb.so.1.0.0
b7a66000-b7a67000 rw-p 00017000 08:01 4531180    /usr/lib/libxcb.so.1.0.0
b7a67000-b7a68000 r-xp 00000000 08:01 4531194    /usr/lib/libxcb-xlib.so.0.0.0
b7a68000-b7a69000 r--p 00000000 08:01 4531194    /usr/lib/libxcb-xlib.so.0.0.0
b7a69000-b7a6a000 rw-p 00001000 08:01 4531194    /usr/lib/libxcb-xlib.so.0.0.0
b7a6a000-b7a71000 r-xp 00000000 08:01 4532306    /usr/lib/libdrm.so.2.3.1
b7a71000-b7a72000 r--p 00006000 08:01 4532306    /usr/lib/libdrm.so.2.3.1
b7a72000-b7a73000 rw-p 00007000 08:01 4532306    /usr/lib/libdrm.so.2.3.1
b7a73000-b7a74000 rw-p b7a73000 00:00 0 
b7a74000-b7a78000 r-xp 00000000 08:01 4531521    /usr/lib/libXfixes.so.3.1.0
b7a78000-b7a79000 rw-p 00003000 08:01 4531521    /usr/lib/libXfixes.so.3.1.0
b7a79000-b7a7b000 r-xp 00000000 08:01 4530896    /usr/lib/libXdamage.so.1.1.0
b7a7b000-b7a7c000 rw-p 00001000 08:01 4530896    /usr/lib/libXdamage.so.1.1.0
b7a7c000-b7a80000 r-xp 00000000 08:01 4531323    /usr/lib/libXxf86vm.so.1.0.0
b7a80000-b7a81000 r--p 00003000 08:01 4531323    /usr/lib/libXxf86vm.so.1.0.0
b7a81000-b7a82000 rw-p 00004000 08:01 4531323    /usr/lib/libXxf86vm.so.1.0.0
b7a82000-b7a8f000 r-xp 00000000 08:01 4531491    /usr/lib/libXext.so.6.4.0
b7a8f000-b7a91000 rw-p 0000c000 08:01 4531491    /usr/lib/libXext.so.6.4.0
b7a91000-b7b7c000 r-xp 00000000 08:01 4531199    /usr/lib/libX11.so.6.2.0
b7b7c000-b7b7d000 r--p 000ea000 08:01 4531199    /usr/lib/libX11.so.6.2.0
b7b7d000-b7b7f000 rw-p 000eb000 08:01 4531199    /usr/lib/libX11.so.6.2.0
b7b7f000-b7b80000 rw-p b7b7f000 00:00 0 
b7b80000-b7b93000 r-xp 00000000 08:01 4532636    /usr/lib/libdirect-1.0.so.0.1.0
b7b93000-b7b94000 r--p 00012000 08:01 4532636    /usr/lib/libdirect-1.0.so.0.1.0
b7b94000-b7b95000 rw-p 00013000 08:01 4532636    /usr/lib/libdirect-1.0.so.0.1.0
b7b95000-b7b96000 rw-p b7b95000 00:00 0 
b7b96000-b7b9d000 r-xp 00000000 08:01 4532638    /usr/lib/libfusion-1.0.so.0.1.0
b7b9d000-b7b9e000 r--p 00006000 08:01 4532638    /usr/lib/libfusion-1.0.so.0.1.0
b7b9e000-b7b9f000 rw-p 00007000 08:01 4532638    /usr/lib/libfusion-1.0.so.0.1.0
b7b9f000-b7c03000 r-xp 00000000 08:01 4532637    /usr/lib/libdirectfb-1.0.so.0.1.0
b7c03000-b7c04000 r--p 00063000 08:01 4532637    /usr/lib/libdirectfb-1.0.so.0.1.0
b7c04000-b7c05000 rw-p 00064000 08:01 4532637    /usr/lib/libdirectfb-1.0.so.0.1.0
b7c05000-b7c07000 r-xp 00000000 08:01 2Aborted
```

---

### Post by rick08 on 2008-11-07
ANY help would be great.

---

### Post by quazi on 2008-11-07
The zsnes in the repositories is broken in Intrepid.  I'm not sure why that version is still listed seeing as it's been known for awhile that it doesn't work (so it just breaks older versions which would work fine, great idea!).  Anyway, you can use the binary compiled for Hardy and it'll run.  There are some links on the forums, but I'm in a hurry and don't have time to find them for you.

---

### Post by rick08 on 2008-11-07
Thanks.  Now I just need to find out why pSX isn't working.

---

