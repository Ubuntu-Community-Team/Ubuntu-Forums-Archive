---
title: "Sound does not work on HP elitebook 8540w"
date: 2011-03-25
forum: Hardware
---

### Post by Botteraar on 2011-03-25
Hi,

I'm running ubuntu 10.04 on an HP elitbook 8540w. 
Here's my problem: Sometimes the sound system will just fail. Never in the midst of a song but allways in between. It could be related to internet videos. I have no idea how to reproduce it. Here is the feedback that mpg123 gives when trying to play a song when it does not work.
> johan@johan-laptop:~$ mpg123 nacht.mp3 
High Performance MPEG 1.0/2.0/2.5 Audio Player for Layers 1, 2 and 3
    version 1.12.1; written and copyright by Michael Hipp and others
    free software (LGPL/GPL) without any warranty but with best wishes

Playing MPEG stream 1 of 1: nacht.mp3 ...
Title:   Gute nacht, freunde             Artist: Reinhard Mey
Album:   Top 2000 (Radio 2)
Genre:   Unknown
MPEG 1.0 layer III, 160 kbit/s, 44100 Hz joint-stereo
*** glibc detected *** mpg123: double free or corruption (out): 0xb82783f8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(+0x6b591)[0xb762e591]
/lib/tls/i686/cmov/libc.so.6(+0x6cde8)[0xb762fde8]
/lib/tls/i686/cmov/libc.so.6(cfree+0x6d)[0xb7632ecd]
/usr/lib/libpulse.so.0(pa_xfree+0x35)[0xb74c0b35]
/usr/lib/libpulsecommon-0.9.21.so(pa_packet_unref+0x6b)[0xb7325a6b]
/usr/lib/libpulsecommon-0.9.21.so(+0x2c228)[0xb732b228]
/usr/lib/libpulsecommon-0.9.21.so(+0x2c7a0)[0xb732b7a0]
/usr/lib/libpulsecommon-0.9.21.so(+0x17cfe)[0xb7316cfe]
/usr/lib/libpulse.so.0(pa_mainloop_dispatch+0x10b)[0xb74a850b]
/usr/lib/libpulse.so.0(pa_mainloop_iterate+0x51)[0xb74a8a21]
/usr/lib/libpulse.so.0(pa_mainloop_run+0x34)[0xb74a8ae4]
/usr/lib/libpulse.so.0(+0x312a3)[0xb74ba2a3]
/usr/lib/libpulsecommon-0.9.21.so(+0x3ce02)[0xb733be02]
/lib/tls/i686/cmov/libpthread.so.0(+0x596e)[0xb74d096e]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0xb7690a4e]
======= Memory map: ========
b2700000-b2721000 rw-p 00000000 00:00 0 
b2721000-b2800000 ---p 00000000 00:00 0 
b2822000-b283f000 r-xp 00000000 08:05 1962323    /lib/libgcc_s.so.1
b283f000-b2840000 r--p 0001c000 08:05 1962323    /lib/libgcc_s.so.1
b2840000-b2841000 rw-p 0001d000 08:05 1962323    /lib/libgcc_s.so.1
b2857000-b287c000 rw-p 00000000 00:00 0 
b287c000-b287d000 ---p 00000000 00:00 0 
b287d000-b307d000 rw-p 00000000 00:00 0 
b307d000-b707e000 rw-s 00000000 00:10 10736      /dev/shm/pulse-shm-4068705015
b707e000-b7083000 r-xp 00000000 08:05 1311742    /usr/lib/libogg.so.0.6.0
b7083000-b7084000 r--p 00004000 08:05 1311742    /usr/lib/libogg.so.0.6.0
b7084000-b7085000 rw-p 00005000 08:05 1311742    /usr/lib/libogg.so.0.6.0
b7085000-b70ac000 r-xp 00000000 08:05 1311984    /usr/lib/libvorbis.so.0.4.3
b70ac000-b70ad000 r--p 00026000 08:05 1311984    /usr/lib/libvorbis.so.0.4.3
b70ad000-b70ae000 rw-p 00027000 08:05 1311984    /usr/lib/libvorbis.so.0.4.3
b70ae000-b719a000 r-xp 00000000 08:05 1311986    /usr/lib/libvorbisenc.so.2.0.6
b719a000-b719b000 ---p 000ec000 08:05 1311986    /usr/lib/libvorbisenc.so.2.0.6
b719b000-b71a9000 r--p 000ec000 08:05 1311986    /usr/lib/libvorbisenc.so.2.0.6
b71a9000-b71aa000 rw-p 000fa000 08:05 1311986    /usr/lib/libvorbisenc.so.2.0.6
b71aa000-b71f5000 r-xp 00000000 08:05 1310968    /usr/lib/libFLAC.so.8.2.0
b71f5000-b71f6000 r--p 0004a000 08:05 1310968    /usr/lib/libFLAC.so.8.2.0
b71f6000-b71f7000 rw-p 0004b000 08:05 1310968    /usr/lib/libFLAC.so.8.2.0
b71f7000-b720a000 r-xp 00000000 08:05 2101084    /lib/tls/i686/cmov/libnsl-2.11.1.so
b720a000-b720b000 r--p 00012000 08:05 2101084    /lib/tls/i686/cmov/libnsl-2.11.1.so
b720b000-b720c000 rw-p 00013000 08:05 2101084    /lib/tls/i686/cmov/libnsl-2.11.1.so
b720c000-b720e000 rw-p 00000000 00:00 0 
b720e000-b7212000 r-xp 00000000 08:05 1311029    /usr/lib/libXdmcp.so.6.0.0
b7212000-b7213000 r--p 00003000 08:05 1311029    /usr/lib/libXdmcp.so.6.0.0
b7213000-b7214000 rw-p 00004000 08:05 1311029    /usr/lib/libXdmcp.so.6.0.0
b7214000-b7216000 r-xp 00000000 08:05 1311018    /usr/lib/libXau.so.6.0.0
b7216000-b7217000 r--p 00001000 08:05 1311018    /usr/lib/libXau.so.6.0.0
b7217000-b7218000 rw-p 00002000 08:05 1311018    /usr/lib/libXau.so.6.0.0
b7218000-b724f000 r-xp 00000000 08:05 1962299    /lib/libdbus-1.so.3.4.0
b724f000-b7250000 r--p 00036000 08:05 1962299    /lib/libdbus-1.so.3.4.0
b7250000-b7251000 rw-p 00037000 08:05 1962299    /lib/libdbus-1.so.3.4.0
b7251000-b72b2000 r-xp 00000000 08:05 1311896    /usr/lib/libsndfile.so.1.0.21
b72b2000-b72b3000 ---p 00061000 08:05 1311896    /usr/lib/libsndfile.so.1.0.21
b72b3000-b72b4000 r--p 00061000 08:05 1311896    /usr/lib/libsndfile.so.1.0.21
b72b4000-b72b5000 rw-p 00062000 08:05 1311896    /usr/lib/libsndfile.so.1.0.21
b72b5000-b72b9000 rw-p 00000000 00:00 0 
b72b9000-b72c0000 r-xp 00000000 08:05 1962433    /lib/libwrap.so.0.7.6
b72c0000-b72c1000 r--p 00006000 08:05 1962433    /lib/libwrap.so.0.7.6
b72c1000-b72c2000 rw-p 00007000 08:05 1962433    /lib/libwrap.so.0.7.6
b72c2000-b72ce000 r-xp 00000000 08:05 1311039    /usr/lib/libXi.so.6.1.0
b72ce000-b72cf000 r--p 0000c000 08:05 1311039    /usr/lib/libXi.so.6.1.0
b72cf000-b72d0000 rw-p 0000d000 08:05 1311039    /usr/lib/libXi.so.6.1.0
b72d0000-b72de000 r-xp 00000000 08:05 1311031    /usr/lib/libXext.so.6.4.0
b72de000-b72df000 r--p 0000d000 08:05 1311031    /usr/lib/libXext.so.6.4.0
b72df000-b72e0000 rw-p 0000e000 08:05 1311031    /usr/lib/libXext.so.6.4.0
b72e0000-b72e3000 r-xp 00000000 08:05 1964616    /lib/libuuid.so.1.3.0
b72e3000-b72e4000 r--p 00002000 08:05 1964616    /lib/libuuid.so.1.3.0
b72e4000-b72e5000 rw-p 00003000 08:05 1964616    /lib/libuuid.so.1.3.0
b72e5000-b72fd000 r-xp 00000000 08:05 1312025    /usr/lib/libxcb.so.1.1.0
b72fd000-b72fe000 r--p 00017000 08:05 1312025    /usr/lib/libxcb.so.1.1.0
b72fe000-b72ff000 rw-p 00018000 08:05 1312025    /usr/lib/libxcb.so.1.1.0
b72ff000-b7348000 r-xp 00000000 08:05 1311837    /usr/lib/libpulsecommon-0.9.21.so
b7348000-b7349000 r--p 00048000 08:05 1311837    /usr/lib/libpulsecommon-0.9.21.so
b7349000-b734a000 rw-p 00049000 08:05 1311837    /usr/lib/libpulsecommon-0.9.21.so
b734a000-b7351000 r-xp 00000000 08:05 1311012    /usr/lib/libSM.so.6.0.1
b7351000-b7352000 r--p 00006000 08:05 1311012    /usr/lib/libSM.so.6.0.1
b7352000-b7353000 rw-p 00007000 08:05 1311012    /usr/lib/libSM.so.6.0.1
b7353000-b7368000 r-xp 00000000 08:05 1310983    /usr/lib/libICE.so.6.3.0
b7368000-b7369000 r--p 00014000 08:05 1310983    /usr/lib/libICE.so.6.3.0
b7369000-b736a000 rw-p 00015000 08:05 1310983    /usr/lib/libICE.so.6.3.0
b736a000-b736c000 rw-p 00000000 00:00 0 
b736c000-b7485000 r-xp 00000000 08:05 1311014    /usr/lib/libX11.so.6.3.0
b7485000-b7486000 r--p 00118000 08:05 1311014    /usr/lib/libX11.so.6.3.0
b7486000-b7488000 rw-p 00119000 08:05 1311014    /usr/lib/libX11.so.6.3.0
b7488000-b7489000 rw-p 00000000 00:00 0 
b7489000-b74c9000 r-xp 00000000 08:05 1311836    /usr/lib/libpulse.so.0.12.2
b74c9000-b74ca000 r--p 00040000 08:05 1311836    /usr/lib/libpulse.so.0.12.2
b74ca000-b74cb000 rw-p 00041000 08:05 1311836    /usr/lib/libpulse.so.0.12.2
b74cb000-b74e0000 r-xp 00000000 08:05 2101942    /lib/tls/i686/cmov/libpthread-2.11.1.so
b74e0000-b74e1000 r--p 00014000 08:05 2101942    /lib/tls/i686/cmov/libpthread-2.11.1.so
b74e1000-b74e2000 rw-p 00015000 08:05 2101942    /lib/tls/i686/cmov/libpthread-2.11.1.so
b74e2000-b74e4000 rw-p 00000000 00:00 0 
b74e4000-b75a7000 r-xp 00000000 08:05 1311098    /usr/lib/libasound.so.2.0.0
b75a7000-b75ab000 r--p 000c2000 08:05 1311098    /usr/lib/libasound.so.2.0.0
b75ab000-b75ac000 rw-p 000c6000 08:05 1311098    /usr/lib/libasound.so.2.0.0
b75b4000-b75b9000 r-xp 00000000 08:05 1312363    /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
b75b9000-b75ba000 r--p 00004000 08:05 1312363    /usr/lib/alsa-lib/libasound_module_pcm_pulse.soAborted
or
> johan@johan-laptop:~$ mpg123 nacht.mp3 
High Performance MPEG 1.0/2.0/2.5 Audio Player for Layers 1, 2 and 3
    version 1.12.1; written and copyright by Michael Hipp and others
    free software (LGPL/GPL) without any warranty but with best wishes

Playing MPEG stream 1 of 1: nacht.mp3 ...
Title:   Gute nacht, freunde             Artist: Reinhard Mey
Album:   Top 2000 (Radio 2)
Genre:   Unknown
MPEG 1.0 layer III, 160 kbit/s, 44100 Hz joint-stereo
mpg123: malloc.c:3096: sYSMALLOc: Assertion `(old_top == (((mbinptr) (((char *) &((av)->bins[((1) - 1) * 2])) - __builtin_offsetof (struct malloc_chunk, fd)))) && old_size == 0) || ((unsigned long) (old_size) >= (unsigned long)((((__builtin_offsetof (struct malloc_chunk, fd_nextsize))+((2 * (sizeof(size_t))) - 1)) & ~((2 * (sizeof(size_t))) - 1))) && ((old_top)->size & 0x1) && ((unsigned long)old_end & pagemask) == 0)' failed.
Aborted


Mostly rebooting will fix the problem. sometimes not at the first time.

Has anybody got any idea what might be going on?

---

### Post by zaq.hack on 2011-06-28
I'm having this same issue on an 8540w ... anyone fix it? At this point, I don't even have an audio control in gnome. The whole audio system seems to decay with each update and now doesn't work at all. I can boot from USB or re-install, but that's very ... Windows?

Any help on this topic?

---

### Post by zaq.hack on 2011-07-02
Update: I did a complete reinstall of Ubuntu 11.04 and still have no sound. I've tried live CD's and have the same issue. I cleared 60G of hard drive space and put Windows on it - I get sound. It doesn't seem to work in any distro of Linux I try and it was working just fine a couple of weeks ago. What the heck?

---

