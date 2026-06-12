---
title: "Sound Crackling"
date: 2008-12-01
forum: General Help
---

### Post by benander on 2008-12-01
I am running 8.1 on an Acer Aspire. When I log on the sound crackles, even when volume is muted.  The sound will then crackle whenever I run something  (volume muted) that requires sound.  If I do the following.

sudo /sbin/alsa force-reload 

it fixes the problem. Is there a way to have it do this on startup or just fix the problem altogether.

I installed "sysv-rc-conf" to manage startup and found "alsa-utils" and enabled it for on startup for levels 2-5 but this did not fix the problem.

---

