---
title: "Jaunty Upgrade - volume muted"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by denham2010 on 2009-04-21
Hi, wondering if anyone else is still having this issue?

I upgraded from 8.10 to 9.04 beta, and encountered the "volume always muted on boot" problem.

I haven't thought too much about it, as it is beta, and the issue is known.

I have just had the upgrades for RC come through, and I am still experiencing this issue.

I am interested to know if anyone else is still having this problem with RC.

Of course, I am quite happy to wait until the final release updates in a few days to see if that fixes the issue.

If anyone knows of a workaround, please let me know. I believe it is a permissions issue from the following entries in my messages.log

```
Apr 21 14:57:26 douglas pulseaudio[4917]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 48000 Hz.
Apr 21 14:57:26 douglas pulseaudio[4917]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
Apr 21 14:57:26 douglas pulseaudio[4940]: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
Apr 21 14:57:26 douglas pulseaudio[4940]: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
Apr 21 14:57:26 douglas pulseaudio[4940]: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
```

Cheers.

---

### Post by denham2010 on 2009-04-25
Bump

---

### Post by valadil on 2009-04-26
I had that for the first day of Jaunty and then it went away.  No clue why.  Have you tried alsactl to store the audio settings?  Or maybe running amixer unmute when your session starts?

---

### Post by denham2010 on 2009-04-27
Thanks valadil.....I should have marked this thread as solved.

The problem never went away for me but I ended up taking the following steps to fix it...in case anyone else has the same issue:

1. added myself to the group pulse-rt, this removed the permissions problem in the first post.

2. unmuted my volume and set it to the desired level, then ran the following command to store it:

```
alsactl -f ~/.asound.state store
```

3. adding the following command to /etc/rc.local did not work for me, so I added the following command to my session start up:

```
alsactl -f ~/.asound.state restore
```

ensure that command runs in a terminal for it to work.

Cheers!

---

### Post by shadow_code on 2009-06-19
Another way is to simply remove the "pulseaudio" package. It doesn't seem to be needed. Worked for me anyway.

---

