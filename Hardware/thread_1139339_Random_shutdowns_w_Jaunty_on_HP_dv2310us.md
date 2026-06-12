---
title: "Random shutdowns w/ Jaunty on HP dv2310us"
date: 2009-04-26
forum: Hardware
---

### Post by jayteef on 2009-04-26
I just upgraded my HP laptop dv2310us to jaunty from 8.10 and am getting random shutdowns. I've turned off power management and and the power deamon and it hasn't helped. The logs don't show anything particularly interesting but there is a power management log each time:

j@j-laptop:/var/log$ cat pm-powersave.log
/usr/lib/pm-utils/power.d/anacron false: success.
/usr/lib/pm-utils/power.d/laptop-mode false: success.
/usr/lib/pm-utils/power.d/sched-powersave false: **sched policy powersave OFF
success.


I wasn't getting these shutdowns in 8.10.

---

### Post by jayteef on 2009-04-27
This looks like the same thing as this bug:

             **[SIZE=3][Bug 13190] New: TZ Trip points are unreasonably high on N600c[/SIZE]**

             bugzilla-daemon
            Sun, 26 Apr 2009 03:56:01 -0700
         
        [http://bugzilla.kernel.org/show_bug.cgi?id=13190](http://bugzilla.kernel.org/show_bug.cgi?id=13190)

---

### Post by CapnBoost on 2009-05-07
My dv1430us does the same thing:

May  6 05:44:37 ubuntu kernel: [41445.124668] [drm:i915_getparam] *ERROR* Unknown parameter 6
May  6 05:44:37 ubuntu kernel: [41445.311184] [drm:i915_getparam] *ERROR* Unknown parameter 6
May  6 05:44:42 ubuntu kernel: [41449.404888] ACPI: Critical trip point
May  6 05:44:42 ubuntu kernel: [41449.404900] Critical temperature reached (98 C), shutting down.
May  6 05:44:42 ubuntu init: tty4 main process (2751) killed by TERM signal
May  6 05:44:42 ubuntu init: tty5 main process (2754) killed by TERM signal
May  6 05:44:42 ubuntu init: tty2 main process (2763) killed by TERM signal
May  6 05:44:42 ubuntu init: tty3 main process (2766) killed by TERM signal
May  6 05:44:42 ubuntu init: tty6 main process (2767) killed by TERM signal
May  6 05:44:42 ubuntu init: tty1 main process (3483) killed by TERM signal
May  6 05:44:44 ubuntu kernel: [41451.407831] Critical temperature reached (83 C), shutting down.
May  6 05:44:45 ubuntu NetworkManager: <info>  (eth1): device state change: 8 -> 3 
May  6 05:44:45 ubuntu NetworkManager: <info>  (eth1): deactivating device (reason: 38). 
May  6 05:44:46 ubuntu x-session-manager[3518]: WARNING: Running '/usr/bin/gconftool-2 --shutdown' at logout returned an exit status of '15' 

I was also not having these shutdowns in 8.10

---

