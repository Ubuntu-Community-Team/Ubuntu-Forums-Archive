---
title: "Asus G1S SPDIF output"
date: 2009-05-20
forum: Hardware
---

### Post by xianthax on 2009-05-20
Hey all, having a bit of trouble getting the optical out to work (or even appear) on my laptop under 8.10.

The laptop has an Intel HDA chipset, version 660-VD, an HDMI port and a SPDIF port which is part of the headphone jack, all analog audio in's / out's work and i have not tried the HDMI connection as i have no audio equipment that can process it.  I do however need the SPDIF port to connect to my home theater setup.

aplay -L shows only analog devices, and an HDMI output.  and alsa mixer only shows the analog output with no options pertaining to the spdif output (or hdmi actually).

cat /proc/asound/devices shows 2 digital playback devices, i've tried forcing mplayer to use both, both playback through the laptop speakers..

i've tried forcing several models by adding:

options snd-hda-intel model=xxx

to /etc/modprobe.d/alsa-base

none of which have managed to make a device for the spdif connector appear in aplay or /proc/asound/devices

my thoughts are that this has something to do with the combo jack, it makes sense (to me) that one device appears on the system if the options are mutually exclusive (speakers, headphones, SPDIF) which appears to be the case.  there is a note in the ALC880 section of ALSA-Configuration.txt for a shared SPDIF but no model in the 660-VD section with such a note, left to auto the system chooses stack-660-digout as its model which has the description of "3-jack with SPDIF OUT (for ALC660VD)" which sounds correct.

any idea on where to turn next with this?

cheers,

xian

---

