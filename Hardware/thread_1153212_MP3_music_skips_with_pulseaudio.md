---
title: "MP3 music skips with pulseaudio"
date: 2009-05-08
forum: Hardware
---

### Post by rwalkerIII on 2009-05-08
Was on Intrepid with no audio problems.  Upgraded to Jaunty and the following now occurs:

The default audio device set to HDA Nvidia ALC1200 analog.  However, this audio device will not share between Amarok and video audio (Firefox 3 with 64-bit flashplayer).  Which ever app gets the audio device first works, but the second fails to initialize the audio.

So, made pulseaudio the preferred device instead of ALC1200.  Sharing is no longer an issue, however Amarok playbacks have frequent skips in the music.  Additionally, Amarok will now sometimes play a second of the last song played during last session when restarted and a new song is played.  It's as if some buffered part of the song is sitting around that is released when I take an action on Amarok.  This did not happen with ALC1200 as the preferred device.

Can't find my problem listed elsewhere but looked into other pulseaudio suggestions.  None applied.  Here's hardware and pulseaudio settings:

This is on a desktop Intel Core2 Quad with 6GB RAM 1333Mhz integrated sound board (Realtek ALC1200) on NVidia SLI 790i motherboard

```

Linux walkubu 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

Sound board is integrated on Nvidia Motherboard NVIDIA® nForce® 790i Ultra SLI  (I believe is a Realtek ALC1200)

 This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values a commented out.  Use either ; or # for
## commenting.

; daemonize = no
; fail = yes
; disallow-module-loading = no
; disallow-exit = no
; use-pid-file = yes
; system-instance = no
; disable-shm = no
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB

high-priority = yes
nice-level = -15

; realtime-scheduling = no
; realtime-priority = 5

; exit-idle-time = 20
; module-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; load-default-script-file = yes
; default-script-file = 

; log-target = auto
; log-level = notice

resample-method = src-linear
; disable-remixing = no
; disable-lfe-remixing = yes

; no-cpu-limit = no

; rlimit-fsize = -1
; rlimit-data = -1
; rlimit-stack = -1
; rlimit-core = -1
; rlimit-as = -1
; rlimit-rss = -1
; rlimit-nproc = -1
; rlimit-nofile = 256
; rlimit-memlock = -1
; rlimit-locks = -1
; rlimit-sigpending = -1
; rlimit-msgqueue = -1
; rlimit-nice = 31
; rlimit-rtprio = 9
; rlimit-rtttime = 1000000

; default-sample-format = s16le
default-sample-rate = 48000
; default-sample-channels = 2

default-fragments = 8
default-fragment-size-msec = 10

rwalk@walkubu:~$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Quad  CPU   Q9550  @ 2.83GHz
stepping	: 7
cpu MHz		: 2833.190
cache size	: 6144 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 4
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority
bogomips	: 5666.38
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Quad  CPU   Q9550  @ 2.83GHz
stepping	: 7
cpu MHz		: 2833.190
cache size	: 6144 KB
physical id	: 0
siblings	: 4
core id		: 3
cpu cores	: 4
apicid		: 3
initial apicid	: 3
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority
bogomips	: 5666.68
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 2
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Quad  CPU   Q9550  @ 2.83GHz
stepping	: 7
cpu MHz		: 2833.190
cache size	: 6144 KB
physical id	: 0
siblings	: 4
core id		: 1
cpu cores	: 4
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority
bogomips	: 5666.63
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 3
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Quad  CPU   Q9550  @ 2.83GHz
stepping	: 7
cpu MHz		: 2833.190
cache size	: 6144 KB
physical id	: 0
siblings	: 4
core id		: 2
cpu cores	: 4
apicid		: 2
initial apicid	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority
bogomips	: 5666.65
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

```

---

### Post by DJYoshaBYD on 2009-05-08
this is exactly why i NEVER recommend "just upgrading" to the newest version, as there is no point to do it... it tends to break alot of stuff, and on top of that, most cats dont even know WHY they want to upgrade.. Microsoft, and a few other unnamed companies, have done this for years to make more money.. NEW NEW NEW!!! ALLL NEWWWWW!! BUY IT, CAUSE, UMMM, ITS NEWWWWW!!! lol

have you tried using a different program to see if its just the audio engine? try running your music on VLC and see if that does it.. maybe even download and try Amarok again and see if it skips in there with a different engine.. you can go into the preferences to change the audio engine.. this may help.. I was having similar issues on a clients pc with ubuntu hardy... it was simply a matter of changing the audio engine used for playing...

hope this helps

---

### Post by neu2buntu on 2009-05-08
im by no ways any expert on this but 1 thing i have noticed in your /etc/pulse/daemon.conf file is your default sample rate is higher than mine... 
> ; default-sample-format = s16le
default-sample-rate = 48000
; default-sample-channels = 2  did you change this yourself from 44100... maybe this has something to do with the problem....

---

### Post by DJYoshaBYD on 2009-05-08
the sample wouldnt cause that.. at least not that small of a difference.. it usually will make your music speed up and sound like a fast record.. lol.. try turning it down, as suggested, but I doubt it will work.. 44.1 is pretty much the standard for basic audio recording..

---

### Post by logos34 on 2009-05-08
you might try changing the 'default-fragments=' setting in /etc/pulse/daemon.conf

See [Appendix B here]("http://ubuntuforums.org/showthread.php?t=789578") (-->search 'stuttering')

---

### Post by rwalkerIII on 2009-05-13
Yes, I changed that sample rate.  That was from a solution to another post where someone was having a similar issue.  The problem was already occurring before I changed it, and still aftwards.  Thanks for looking though.

---

