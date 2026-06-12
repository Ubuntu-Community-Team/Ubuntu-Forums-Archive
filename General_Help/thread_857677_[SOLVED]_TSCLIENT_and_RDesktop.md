---
title: "[SOLVED] TSCLIENT and RDesktop"
date: 2008-07-12
forum: General Help
---

### Post by Plasma_NZ on 2008-07-12
Ok... here's the problem

I'm trying to use rdesktop and tsclient

with a winxp machine...

it works great apart from playing audio locally..

tsclient reports device busy /dev/dsp

rdesktop reports 

WARNING: Remote desktop does not support colour depth 24; falling back to 16
/dev/dsp: Device or resource busy
WARNING: no working audio-driver found

Any ideas on how i can fix this.?

---

### Post by Plasma_NZ on 2008-07-12
Have installed alsa-oss to try and fix the issue, hasn't helped...

And yes i know the sound works, when speakers are plugged into the winxp cd, there's sound etc..

---

### Post by Plasma_NZ on 2008-07-13
Problem solved..

I compiled and install the newer version .160

Also, there was a conflict with the dv4lstart - had made a folde r/usr/local/share/man/ with a file man1 - so had to remove that..

But now sound works "local"

---

