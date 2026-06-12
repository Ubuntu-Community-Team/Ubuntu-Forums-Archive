---
title: "[SOLVED] ZSNES dependency problem"
date: 2008-11-20
forum: General Help
---

### Post by RonB123123 on 2008-11-20
I didn't have this problem before with ZSNES. I must have installed or uninstalled an important library. I've tried uninstall ZSNES and reinstalling with and without using synaptic but no luck.

Is there a way to automatically reinstall all of ZSNES's dependencies? I tried to reinstall all the files I saw in the below output, but again to no avail.

When I run it through the command line, this is my output:
> 
user@user-laptop:~$ zsnes
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event10. Make sure you have read permissions to it.
Unable to poll /dev/input/event8. Make sure you have read permissions to it.
Unable to poll /dev/input/event9. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
*** buffer overflow detected ***: zsnes terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7d1a558]
/lib/tls/i686/cmov/libc.so.6[0xb7d18680]
zsnes[0x8056c1b]
======= Memory map: ========
08048000-08303000 r-xp 00000000 08:05 6147161    /usr/bin/zsnes
08303000-08304000 r--p 002ba000 08:05 6147161    /usr/bin/zsnes
08304000-08343000 rw-p 002bb000 08:05 6147161    /usr/bin/zsnes
08343000-088f7000 rw-p 08343000 00:00 0 
09427000-09471000 rw-p 09427000 00:00 0          [heap]
b6bda000-b7709000 rw-p b6bda000 00:00 0 
b7709000-b7757000 r-xp 00000000 08:05 6146024    /usr/lib/libpulse.so.0.4.1
b7757000-b7758000 r--p 0004d000 08:05 6146024    /usr/lib/libpulse.so.0.4.1
b7758000-b7759000 rw-p 0004e000 08:05 6146024    /usr/lib/libpulse.so.0.4.1
b7759000-b7765000 r-xp 00000000 08:05 6146026    /usr/lib/libpulse-simple.so.0.0.1
b7765000-b7766000 r--p 0000b000 08:05 6146026    /usr/lib/libpulse-simple.so.0.0.1
b7766000-b7767000 rw-p 0000c000 08:05 6146026    /usr/lib/libpulse-simple.so.0.0.1
b7778000-b77a0000 r-xp 00000000 08:05 4948043    /lib/libpcre.so.3.12.1
b77a0000-b77a1000 r--p 00027000 08:05 4948043    /lib/libpcre.so.3.12.1
b77a1000-b77a2000 rw-p 00028000 08:05 4948043    /lib/libpcre.so.3.12.1
b77a2000-b7857000 r-xp 00000000 08:05 6145105    /usr/lib/libglib-2.0.so.0.1800.2
b7857000-b7858000 r--p 000b4000 08:05 6145105    /usr/lib/libglib-2.0.so.0.1800.2
b7858000-b7859000 rw-p 000b5000 08:05 6145105    /usr/lib/libglib-2.0.so.0.1800.2
b7859000-b785d000 r-xp 00000000 08:05 6145696    /usr/lib/libgthread-2.0.so.0.1800.2
b785d000-b785e000 r--p 00003000 08:05 6145696    /usr/lib/libgthread-2.0.so.0.1800.2
b785e000-b785f000 rw-p 00004000 08:05 6145696    /usr/lib/libgthread-2.0.so.0.1800.2
b785f000-b7864000 r-xp 00000000 08:05 6146608    /usr/lib/libartsc.so.0.0.0
b7864000-b7865000 r--p 00004000 08:05 6146608    /usr/lib/libartsc.so.0.0.0
b7865000-b7866000 rw-p 00005000 08:05 6146608    /usr/lib/libartsc.so.0.0.0
b7866000-b787b000 r-xp 00000000 08:05 6145574    /usr/lib/libICE.so.6.3.0
b787b000-b787c000 rw-p 00014000 08:05 6145574    /usr/lib/libICE.so.6.3.0
b787c000-b787e000 rw-p b787c000 00:00 0 
b787e000-b7885000 r-xp 00000000 08:05 6144147    /usr/lib/libSM.so.6.0.0
b7885000-b7886000 r--p 00006000 08:05 6144147    /usr/lib/libSM.so.6.0.0
b7886000-b7887000 rw-p 00007000 08:05 6144147    /usr/lib/libSM.so.6.0.0
b7887000-b78d4000 r-xp 00000000 08:05 6145651    /usr/lib/libXt.so.6.0.0
b78d4000-b78d8000 rw-p 0004c000 08:05 6145651    /usr/lib/libXt.so.6.0.0
b78d8000-b78ee000 r-xp 00000000 08:05 6146610    /usr/lib/libaudio.so.2.4
b78ee000-b78ef000 r--p 00015000 08:05 6146610    /usr/lib/libaudio.so.2.4
b78ef000-b78f0000 rw-p 00016000 08:05 6146610    /usr/lib/libaudio.so.2.4
b78f8000-b78f9000 rw-p b78f8000 00:00 0 
b78f9000-b78fc000 r-xp 00000000 08:05 4948010    /lib/libcap.so.1.10
b78fc000-b78fd000 rw-p 00002000 08:05 4948010    /lib/libcap.so.1.10
b78fd000-b78ff000 r-xp 00000000 08:05 6169476    /usr/lib/ao/plugins-2/libpulse.so
b78ff000-b7901000 rw-p 00001000 08:05 6169476    /usr/lib/ao/plugins-2/libpulse.so
b7901000-b7923000 r-xp 00000000 08:05 6145692    /usr/lib/libaudiofile.so.0.0.2
b7923000-b7926000 rw-p 00021000 08:05 6145692    /usr/lib/libaudiofile.so.0.0.2
b7926000-b7929000 r-xp 00000000 08:05 6145688    /usr/lib/libgmodule-2.0.so.0.1800.2
b7929000-b792a000 r--p 00002000 08:05 6145688    /usr/lib/libgmodule-2.0.so.0.1800.2
b792a000-b792b000 rw-p 00003000 08:05 6145688    /usr/lib/libgmodule-2.0.so.0.1800.2
b792b000-b792c000 r-xp 00000000 08:05 6169107    /usr/lib/ao/plugins-2/libarts.so
b792c000-b792e000 rw-p 00000000 08:05 6169107    /usr/lib/ao/plugins-2/libarts.so
b792e000-b7931000 r-xp 00000000 08:05 6169095    /usr/lib/ao/plugins-2/libalsa09.so
b7931000-b7933000 rw-p 00002000 08:05 6169095    /usr/lib/ao/plugins-2/libalsa09.so
b7933000-b7935000 r-xp 00000000 08:05 6169137    /usr/lib/ao/plugins-2/liboss.so
b7935000-b7937000 rw-p 00001000 08:05 6169137    /usr/lib/ao/plugins-2/liboss.so
b7937000-b7941000 r-xp 00000000Aborted


Should I reinstall all of those libraries or what?

---

### Post by undadecor on 2008-11-20
In the following link a user has what seems to be a similar problem to you and mentions what he did to fix it.  I'd give that a try.

[http://sudan.ubuntuforums.com/showthread.php?t=983735]("http://sudan.ubuntuforums.com/showthread.php?t=983735")

---

### Post by DirtDawg on 2008-11-20
Also, try [snes9x-gtk]("http://www.happypenguin.org/show?snes9x-gtk"). There's binaries and .debs available [here.]("http://www.snes9x.com/phpbb2/viewtopic.php?p=22874") It's quite nice.

---

### Post by RonB123123 on 2008-11-22
Ahh I see. It's an intrepid bug. Thanks for the topic link.

I am going to try snes 9x instead. Thank you.

---

