---
title: "Error in modprobe.conf"
date: 2006-11-15
forum: Hardware &amp; Laptops
---

### Post by mstrat on 2006-11-15
Help!  I have a Toshiba Satellite laptop that dual boots with XP and Edgy (this problem started with Edgy over Dapper)  I like edgy, I actually have some sound and the screen resolution is fixed, but...When shutting down the system, I get an error message:

Modprobe: WARNING: /etc/modprobe.conf line 1: ignoring bad line starting with 'snd-18964'

My modprobe file looks like this:

snd-18964
# ALSA portion
          alias char-major-116 snd
          alias snd-card-0 snd-xxxx
        # OSS/Free portion
          alias char-major-14 soundcore
          alias sound-slot-0 snd-card-0
        # card #1
          alias sound-service-0-0 snd-mixer-oss
          alias sound-service-0-1 snd-seq-oss
          alias sound-service-0-3 snd-pcm-oss
          alias sound-service-0-8 snd-seq-oss
          alias sound-service-0-12-pcn-oss

The other problem I have on that system is that if I press the power button it simply powers off the computer, not going through a shutdown process or anything, no matter what setting I have it on.

---

