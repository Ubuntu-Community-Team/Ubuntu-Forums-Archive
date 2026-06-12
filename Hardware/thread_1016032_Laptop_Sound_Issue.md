---
title: "Laptop Sound Issue"
date: 2008-12-19
forum: Hardware
---

### Post by Verris on 2008-12-19
I followed many guides to fix this and checked many threads about similar problems and can't figure out why my sound stopped working today.

I'm on a Gateway MX7525 and this is what I get in the log file

Dec 19 00:08:33 ross-laptop-linux pulseaudio[16595]: ltdl-bind-now.c: Failed to find original dlopen loader.
Dec 19 00:08:33 ross-laptop-linux pulseaudio[16600]: pid.c: Stale PID file, overwriting.
Dec 19 00:08:33 ross-laptop-linux pulseaudio[16600]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Dec 19 00:08:33 ross-laptop-linux pulseaudio[16600]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Dec 19 00:08:34 ross-laptop-linux pulseaudio[16600]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Dec 19 00:08:34 ross-laptop-linux pulseaudio[16600]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Dec 19 00:08:44 ross-laptop-linux pulseaudio[16600]: alsa-util.c: Unable to determine current swparams: Operation not permitted
Dec 19 00:08:45 ross-laptop-linux pulseaudio[16600]: alsa-util.c: Unable to load mixer: Invalid argument
Dec 19 00:08:45 ross-laptop-linux pulseaudio[16600]: module-alsa-sink.c: Got POLLERR from ALSA
Dec 19 00:08:45 ross-laptop-linux pulseaudio[16600]: module-alsa-sink.c: Could not recover from POLLERR|POLLNVAL|POLLHUP with snd_pcm_prepare(): Input/output error
Dec 19 00:08:50 ross-laptop-linux pulseaudio[16600]: alsa-util.c: Unable to determine current swparams: Operation not permitted
Dec 19 00:08:51 ross-laptop-linux pulseaudio[16600]: alsa-util.c: Unable to load mixer: Invalid argument
Dec 19 00:08:51 ross-laptop-linux pulseaudio[16600]: module-alsa-source.c: Got POLLERR from ALSA
Dec 19 00:08:51 ross-laptop-linux pulseaudio[16600]: module-alsa-source.c: Could not recover from POLLERR|POLLNVAL|POLLHUP with snd_pcm_prepare(): Input/output error


Dec 19 12:37:28 ross-laptop-linux pulseaudio[5779]: ltdl-bind-now.c: Failed to find original dlopen loader.
Dec 19 12:37:28 ross-laptop-linux pulseaudio[5781]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Dec 19 12:37:28 ross-laptop-linux pulseaudio[5781]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Dec 19 12:37:28 ross-laptop-linux pulseaudio[5781]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Dec 19 12:37:28 ross-laptop-linux pulseaudio[5781]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Dec 19 12:37:29 ross-laptop-linux pulseaudio[5781]: alsa-util.c: Unable to load mixer: Invalid argument
Dec 19 12:37:34 ross-laptop-linux pulseaudio[5781]: alsa-util.c: Unable to determine current swparams: Operation not permitted
Dec 19 12:37:35 ross-laptop-linux pulseaudio[5781]: alsa-util.c: Unable to load mixer: Invalid argument
Dec 19 12:37:35 ross-laptop-linux pulseaudio[5781]: module-alsa-source.c: Got POLLERR from ALSA
Dec 19 12:37:35 ross-laptop-linux pulseaudio[5781]: module-alsa-source.c: Could not recover from POLLERR|POLLNVAL|POLLHUP with snd_pcm_prepare(): Input/output error
Dec 19 12:37:40 ross-laptop-linux pulseaudio[5854]: ltdl-bind-now.c: Failed to find original dlopen loader.



After trying some fixes it's down to this after a restart.

Dec 19 13:07:56 ross-laptop-linux pulseaudio[6322]: ltdl-bind-now.c: Failed to find original dlopen loader.
Dec 19 13:07:56 ross-laptop-linux pulseaudio[6322]: main.c: This program is not intended to be run as root (unless --system is specified).
Dec 19 13:07:56 ross-laptop-linux pulseaudio[6322]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.

Dec 19 13:22:52 ross-laptop-linux pulseaudio[5692]: ltdl-bind-now.c: Failed to find original dlopen loader.
Dec 19 13:22:52 ross-laptop-linux pulseaudio[5694]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Dec 19 13:22:52 ross-laptop-linux pulseaudio[5694]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Dec 19 13:22:52 ross-laptop-linux pulseaudio[5694]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Dec 19 13:22:52 ross-laptop-linux pulseaudio[5694]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.

My sound was working fine until this morning when I booted. Last night all I did was install eclipse.

---

### Post by 73ckn797 on 2008-12-19
I am not familiar with eclipse but if the problem began after that install then I would un-install to see if that is the issue.

---

### Post by Verris on 2008-12-19
Eclipse is just a java development environment. I fixed the problem by purging and reinstalling linux-sound-base, alsa-base and alsa-utils.

---

