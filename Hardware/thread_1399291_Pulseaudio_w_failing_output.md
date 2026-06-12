---
title: "Pulseaudio w/ failing output"
date: 2010-02-05
forum: Hardware
---

### Post by afoglia on 2010-02-05
We recently upgraded our work computers from Intrepid to Karmic and now the audio only works sporadically.

These are Dell workstations with two audio outputs, one the onboard headphone jack, and one via the HDMI output.  The onboard device is the only one we use and often fails.

In Intrepid, only the onboard device was recognized, and killing and restarting pulseaudio lead to the audio working again.  Now with the second device recognized, restarting pulseaudio has no effect.

My guess is that pulseaudio tries multiple ways to get the devices working, and is now giving up on the onboard device after the first try because a device is working.  But I have no way of confirming this and see nothing under /var/log starting with the name pulseaudio.  (I am not root.)

Restarting is the only thing that seems to work.

Is my theory correct, and how do I restart my audio device?

---

### Post by tjodSK on 2010-02-05
as for restarting the audio, you might try "alsa force-reload", but you'll need at least sudo privileges.

---

