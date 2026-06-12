---
title: "Problem with external audio interface"
date: 2019-12-04
forum: Hardware
---

### Post by nzfs on 2019-12-04
hi, i recently installed ubuntu 19.10 and i have a problem with my audio interface focusrite scarlett 2i2. the problem is that when switching  audio sources (for example a video player and the  browser, or even going from youtube to vimeo or when receiving a  notification from a website) the interface disconnects and  reconnects. is there a way to avoid it? other than that it works perfectly. thanks

---

### Post by CatKiller on 2019-12-04
I've got one of those, and haven't experienced the issue you describe.

I did find that I needed to edit **/etc/pulse/daemon.conf** so that it had

```
default-sample-format = s32le
default-sample-rate = 48000
```

for Proton games to work properly all the time; native applications worked perfectly, but the signal going over the wire is 32-bit even though the audio itself is 16/24-bit and that confused the Windows applications. Possibly something similar would help you.

---

### Post by nzfs on 2019-12-05
i still have the same problem, everytime i play audio on a different application, the sound card seems to restart.

---

### Post by nzfs on 2019-12-05
> **CatKiller said:**
> I've got one of those, and haven't experienced the issue you describe.

I did find that I needed to edit **/etc/pulse/daemon.conf** so that it had

```
default-sample-format = s32le
default-sample-rate = 48000
```

for Proton games to work properly all the time; native applications worked perfectly, but the signal going over the wire is 32-bit even though the audio itself is 16/24-bit and that confused the Windows applications. Possibly something similar would help you.

 			i still have the same problem, everytime i play audio on a different application, the sound card seems to restart.

---

### Post by CatKiller on 2019-12-05
Do you have resampling enabled?

---

### Post by nzfs on 2019-12-05
> **CatKiller said:**
> Do you have resampling enabled?

i don't know

---

### Post by CatKiller on 2019-12-05
> **nzfs said:**
> i don't know

Have a look at that file. It sets options for PulseAudio.

Lines that start with a ; are commented out, meaning they have no effect, and the default values are listed. **man pulse-daemon.conf** explains what all the options do. This is mine, in case you find it useful.

```

# This file is part of PulseAudio.
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
# along with PulseAudio; if not, see <http://www.gnu.org/licenses/>.

## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values are commented out.  Use either ; or # for
## commenting.

; daemonize = no
; fail = yes
; allow-module-loading = yes
; allow-exit = yes
; use-pid-file = yes
; system-instance = no
; local-server-type = user
; enable-shm = yes
; enable-memfd = yes
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB
; lock-memory = no
; cpu-limit = no

; high-priority = yes
; nice-level = -11

; realtime-scheduling = yes
; realtime-priority = 5

; exit-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; load-default-script-file = yes
; default-script-file = /etc/pulse/default.pa

; log-target = auto
; log-level = notice
; log-meta = no
; log-time = no
; log-backtrace = 0

resample-method = speex-float-10
avoid-resampling = true
; enable-remixing = yes
; remixing-use-all-sink-channels = yes
; enable-lfe-remixing = no
; lfe-crossover-freq = 0

flat-volumes = no

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
; rlimit-rttime = 200000

default-sample-format = s32le
default-sample-rate = 48000
alternate-sample-rate = 44100
; default-sample-channels = 2
; default-channel-map = front-left,front-right

; default-fragments = 4
; default-fragment-size-msec = 25

; enable-deferred-volume = yes
deferred-volume-safety-margin-usec = 1
; deferred-volume-extra-delay-usec = 0

```

---

### Post by nzfs on 2019-12-05
> **CatKiller said:**
> Have a look at that file. It sets options for PulseAudio.

Lines that start with a ; are commented out, meaning they have no effect, and the default values are listed. **man pulse-daemon.conf** explains what all the options do. This is mine, in case you find it useful.

```

# This file is part of PulseAudio.
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
# along with PulseAudio; if not, see <http://www.gnu.org/licenses/>.

## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values are commented out.  Use either ; or # for
## commenting.

; daemonize = no
; fail = yes
; allow-module-loading = yes
; allow-exit = yes
; use-pid-file = yes
; system-instance = no
; local-server-type = user
; enable-shm = yes
; enable-memfd = yes
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB
; lock-memory = no
; cpu-limit = no

; high-priority = yes
; nice-level = -11

; realtime-scheduling = yes
; realtime-priority = 5

; exit-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; load-default-script-file = yes
; default-script-file = /etc/pulse/default.pa

; log-target = auto
; log-level = notice
; log-meta = no
; log-time = no
; log-backtrace = 0

resample-method = speex-float-10
avoid-resampling = true
; enable-remixing = yes
; remixing-use-all-sink-channels = yes
; enable-lfe-remixing = no
; lfe-crossover-freq = 0

flat-volumes = no

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
; rlimit-rttime = 200000

default-sample-format = s32le
default-sample-rate = 48000
alternate-sample-rate = 44100
; default-sample-channels = 2
; default-channel-map = front-left,front-right

; default-fragments = 4
; default-fragment-size-msec = 25

; enable-deferred-volume = yes
deferred-volume-safety-margin-usec = 1
; deferred-volume-extra-delay-usec = 0

```

thank you, ill check that out.

---

