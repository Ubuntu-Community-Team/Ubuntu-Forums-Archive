---
title: "sound stopped working (nforce)"
date: 2005-03-01
forum: Hardware &amp; Laptops
---

### Post by inz on 2005-03-01
Greetings.

After installing ubuntu everything worked rather perfectly, except for a messup with gnome not saving settings (got booted back to the default theme every time I started) which caused me green hairs, and eventually I decided to nuke my user account and start anew. After I booted up with my new account everything seemed to work perfectly well except I have no sound!

When I open up preferences by right clicking the speaker icon I have no devices, and I tried reinstalling alsa which didn't seem to do anything. Any hints on what I should do, or what information I should supply in order to find a solution?

The only other thing I can remember doing inbetween sound working and not is disabling gdm, which shouldn't really effect sound unless something's totally psychotic with this world. :p

---

### Post by inz on 2005-03-01
Well. Tried playing an mp3 with mpg123 in console and found that I didn't have permissions to access /dev/dsp so I chmodded it and now it works in console and X, but the gnome volume control still can't modify the volume.

---

