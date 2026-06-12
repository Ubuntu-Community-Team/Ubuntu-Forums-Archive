---
title: "Thunderbird randomly crashes after 9.10 upgrade"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by dkarnows on 2009-11-04
After upgrading to Ubuntu 9.10 my Thunderbird randomly crashes. Happens every hour or so and usually I'm not using it at the time. I'm connected to an IMAP server. I have lightning & Google Calendar addons installed, which I've since disabled but it still crashes.

I don't get any error, just a crash. I'm not sure where to look for a log file or anything. I'll try start it on a command line to see if I get any stderr/stdout associated with the crash.

---

### Post by dkarnows on 2009-11-04
Here's my stderr/stdout output associated with the crash:

 *** glibc detected *** /usr/lib/thunderbird/thunderbird-bin: corrupted double-linked list: 0xb1439ec8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xa0dff1]
/lib/tls/i686/cmov/libc.so.6[0xa1136f]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x58)[0xa12868]
/usr/lib/thunderbird/libnspr4.so(PR_Malloc+0x38)[0x1e6378]
/usr/lib/thunderbird/libplds4.so(PL_ArenaAllocate+0xb9)[0x970f49]
/usr/lib/thunderbird/components/libgklayout.so[0x257f3f3]
/usr/lib/thunderbird/libxpcom_core.so(_ZN15nsSupportsArray17EnumerateForwardsEPFiP11nsISupportsPvES2_+0x30)[0x1471b0]
/usr/lib/thunderbird/components/libgklayout.so[0x2579c7a]
/usr/lib/thunderbird/components/libgklayout.so[0x2579c4c]
/usr/lib/thunderbird/libxpcom_core.so(_ZN11nsVoidArray17EnumerateForwardsEPFiPvS0_ES0_+0x48)[0x150608]
/usr/lib/thunderbird/components/libgklayout.so[0x257e6aa]
/usr/lib/thunderbird/components/libgklayout.so[0x257ea3b]
/usr/lib/thunderbird/components/libgklayout.so[0x25a91b8]
/usr/lib/thunderbird/components/libgklayout.so[0x25a9671]
/usr/lib/thunderbird/components/libgklayout.so[0x25a9c01]
/usr/lib/thunderbird/components/libgklayout.so[0x247d82c]
/usr/lib/thunderbird/components/libgklayout.so[0x24b5ed6]
/usr/lib/thunderbird/components/libgklayout.so[0x263a01c]
/usr/lib/thunderbird/components/libgklayout.so[0x2727882]
/usr/lib/thunderbird/components/libgklayout.so[0x272b556]
/usr/lib/thunderbird/components/libhtmlpars.so[0x80eb92a]
/usr/lib/thunderbird/components/libhtmlpars.so[0x80ef346]
/usr/lib/thunderbird/components/libhtmlpars.so[0x80efdd4]
/usr/lib/thunderbird/components/libhtmlpars.so[0x80f05e7]
/usr/lib/thunderbird/components/libhtmlpars.so[0x80ec5be]
/usr/lib/thunderbird/components/libhtmlpars.so[0x81015a1]
/usr/lib/thunderbird/components/libhtmlpars.so[0x8104611]
/usr/lib/thunderbird/components/libhtmlpars.so[0x8101b1b]
/usr/lib/thunderbird/components/libdocshell.so[0x350e2fd]
/usr/lib/thunderbird/components/libmail.so[0x7a35be1]
/usr/lib/thunderbird/components/libmail.so[0x7a2a107]
/usr/lib/thunderbird/components/libdocshell.so[0x350fc4c]
/usr/lib/thunderbird/components/libnecko.so[0x8ac3448]
/usr/lib/thunderbird/components/libnecko.so[0x8a9e1b3]
/usr/lib/thunderbird/components/libnecko.so[0x8a9e116]
/usr/lib/thunderbird/libxpcom_core.so(PL_HandleEvent+0x27)[0x17e657]
/usr/lib/thunderbird/libxpcom_core.so(PL_ProcessPendingEvents+0x5d)[0x17e96d]
/usr/lib/thunderbird/libxpcom_core.so[0x180547]
/usr/lib/thunderbird/components/libwidget_gtk2.so[0x21c0725]
/lib/libglib-2.0.so.0[0x609d5b]
/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1f8)[0x5d2e78]
/lib/libglib-2.0.so.0[0x5d6720]
/lib/libglib-2.0.so.0(g_main_loop_run+0x1bf)[0x5d6b8f]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9)[0xfb0419]
/usr/lib/thunderbird/components/libwidget_gtk2.so[0x21c0d96]
/usr/lib/thunderbird/components/libtoolkitcomps.so[0x5e2f397]
/usr/lib/thunderbird/thunderbird-bin[0x8050270]
/usr/lib/thunderbird/thunderbird-bin[0x804ad31]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x9b9b56]
/usr/lib/thunderbird/thunderbird-bin[0x804ac61]
======= Memory map: ========
00110000-001cc000 r-xp 00000000 08:01 8235489    /usr/lib/thunderbird/libxpcom_core.so
001cc000-001d3000 r--p 000bb000 08:01 8235489    /usr/lib/thunderbird/libxpcom_core.so
001d3000-001d4000 rw-p 000c2000 08:01 8235489    /usr/lib/thunderbird/libxpcom_core.so
001d4000-0020b000 r-xp 00000000 08:01 8233012    /usr/lib/libnspr4.so
0020b000-0020c000 r--p 00036000 08:01 8233012    /usr/lib/libnspr4.so
0020c000-0020d000 rw-p 00037000 08:01 8233012    /usr/lib/libnspr4.so
0020d000-0020f000 rw-p 00000000 00:00 0 
0020f000-00236000 r-xp 00000000 08:01 8236662    /usr/lib/libpangoft2-1.0.so.0.2600.0
00236000-00237000 r--p 00027000 08:01 8236662    /usr/lib/libpangoft2-1.0.so.0.2600.0
00237000-00238000 rw-p 00028000 08:01 8236662    /usr/lib/libpangoft2-1.0.so.0.2600.0
00238000-00250000 r-xp 00000000 08:01 8237170    /usr/lib/libgdk_pixbuf-2.0.so.0.1800.3
00250000-00251000 r--p 00017000 08:01 8237170    /usr/lib/libgdk_pixbuf-2.0.so.0.1800.3
00251000-00252000 rw-p 00018000 08:01 8237170    /usr/lib/libgdk_pixbuf-2.0.so.0.1800.3
00254000-00256000 r-xp 00000000 08:01 354519     /lib/tls/i686/cmov/libdl-2.10.1.so
00256000-00257000 r--p 00001000 08:01 354519     /lib/tls/i686/cmov/libdl-2.10.1.so
00257000-00258000 rw-p 00002000 08:01 354519     /lib/tls/i686/cmov/libdl-2.10.1.so
00258000-00283000 r-xp 00000000 08:01 8236230    /usr/lib/libfontconfig.so.1.3.0
00283000-00284000 r--p 0002a000 08:01 8236230    /usr/lib/libfontconfig.so.1.3.0
00284000-00285000 rw-p 0002b000 08:01 8236230    /usr/lib/libfontconfig.so.1.3.0
00285000-00288000 r-xp 00000000 08:01 1900652    /usr/lib/libgmodule-2.0.so.0.2200.2
00288000-00289000 r--p 00002000 08:01 1900652    /usr/lib/libgmodule-2.0.so.0.2200.2
00289000-0028a000 rw-p 00003000 08:01 1900652    /usr/lib/libgmodule-2.0.so.0.2200.2
0028a000-0028e000 r-xp 00000000 08:01 1900654    /usr/lib/libgthread-2.0.so.0.2200.2
0028e000-0028f000 r--p 00003000 08:01 1900654    /usr/lib/libgthread-2.0.so.0.2200.2
0028f000-00290000 rw-p 00004000 08:01 1900654    /usr/lib/libgthread-2.0.so.0.2200.2
00290000-002ac000 r-xp 00000000 08:01 335877     /lib/libgcc_s.so.1
002ac000-002ad000 r--p 0001b000 08:01 335877     /lib/libgcc_s.so.1
002ad000-002ae000 rw-p 0001c000 08:01 335877     /lib/libgcc_s.so.1
002ae000-002b0000 r-xp 00000000 08:01 1900563    /usr/lib/libXinerama.so.1.0.0
002b0000-002b1000 rw-p 00001000 08:01 1900563    /usr/lib/libXinerama.so.1.0.0
002b1000-002b4000 r-xp 00000000 08:01 8235486    /usr/lib/thunderbird/libxpcom.so
002b4000-002b5000 r--p 00002000 08:01 8235486    /usr/lib/thunderbird/libxpcom.so
002b5000-002b6000 rw-p 00003000 08:01 8235486    /usr/lib/thunderbird/libxpcom.so
002b6000-00348000 r-xp 00000000 08:01 8237169    /usr/lib/libgdk-x11-2.0.so.0.1800.3
00348000-0034a000 r--p 00092000 08:01 8237169    /usr/lib/libgdk-x11-2.0.so.0.1800.3
0034a000-0034b000 rw-p 00094000 08:01 8237169    /usr/lib/libgdk-x11-2.0.so.0.1800.3
0034b000-0036f000 r-xp 00000000 08:01 354520     /lib/tls/i686/cmov/libm-2.10.1.so
0036f000-00370000 r--p 00023000 08:01 354520     /lib/tls/i686/cmov/libm-2.10.1.so
00370000-00371000 rw-p 00024000 08:01 354520     /lib/tls/i686/cmov/libm-2.10.1.so
00371000-00373000 r-xp 00000000 08:01 8236900    /usr/lib/libXcomposite.so.1.0.0
00373000-00374000 r--p 00001000 08:01 8236900    /usr/lib/libXcomposite.so.1.0.0
00374000-00375000 rw-p 00002000 08:01 8236900    /usr/lib/libXcomposite.so.1.0.0
00375000-00379000 r-xp 00000000 08:01 8236889    /usr/lib/libXfixes.so.3.1.0
00379000-0037a000 r--p 00003000 08:01 8236889    /usr/lib/libXfixes.so.3.1.0
0037a000-0037b000 rw-p 00004000 08:01 8236889    /usr/lib/libXfixes.so.3.1.0
0037b000-00383000 r-xp 00000000 08:01 8235843    /usr/lib/libXrender.so.1.3.0
00383000-00384000 r--p 00007000 08:01 8235843    /usr/lib/libXrender.so.1.3.0
00384000-00385000 rw-p 00008000 08:01 8235843    /usr/lib/libXrender.so.1.3.0
00385000-0038c000 r-xp 00000000 08:01 8233408    /usr/lib/libXrandr.so.2.2.0
0038c000-0038d000 r--p 00006000 08:01 8233408    /usr/lib/libXrandr.so.2.2.0
0038d000-0038e000 rw-p 00007000 08:01 8233408    /usr/lib/libXrandr.so.2.2.0
0038e000-00397000 r-xp 00000000 08:01 8236895    /usr/lib/libXcursor.so.1.0.2Aborted

---

### Post by Ozdemon on 2009-11-15
> **dkarnows said:**
> After upgrading to Ubuntu 9.10 my Thunderbird randomly crashes. Happens every hour or so and usually I'm not using it at the time. I'm connected to an IMAP server. I have lightning & Google Calendar addons installed, which I've since disabled but it still crashes.

I don't get any error, just a crash. I'm not sure where to look for a log file or anything. I'll try start it on a command line to see if I get any stderr/stdout associated with the crash.

I am having complete system crashes and reboot.  I also have Thunderbird with lightning, and Google calendar addons.  So far I have not been able to work out the cause, but in every case Thunderbird would have been open.

---

### Post by m.j.e on 2009-11-16
Thunderbird is crashing for me too since I upgraded to 9.10. It barely lasts 10 seconds most of the time even if I do nothing:

$ time thunderbird -safe-mode
Segmentation fault

real    0m10.793s
user    0m1.076s
sys    0m0.112s

---

### Post by m.j.e on 2009-11-16
I can make it stay up so long as I avoid moving the mouse anywhere near the menu bar but as soon as I do (or hit alt letter, e.g., alt-f) it crashes.

---

### Post by m.j.e on 2009-11-17
I reported my issue via apport at [https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/484087](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/484087)

---

