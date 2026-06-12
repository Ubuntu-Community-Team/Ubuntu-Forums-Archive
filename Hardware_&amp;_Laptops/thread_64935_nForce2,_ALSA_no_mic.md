---
title: "nForce2, ALSA: no mic"
date: 2005-09-12
forum: Hardware &amp; Laptops
---

### Post by bdash on 2005-09-12
Hello.

I have an nForce2 sound chip, and I use ALSA for both input and output. Output works fine, using the "happy" howto I could even mix different sources, but input (the microphone) does not work.
- If I launch gnome-sound-recorder as normal user, press the "rec" button just has no effect
- If I launch it as root (e.g. using sudo), it seems to work but it only records silence. I checked my mixer settings, so I think the problem comes from my Alsa configuration. Here is my asound.conf (barely a copy/paste from the howto):


Thank you!
----
# Set default sound card
# Useful so that all settings can be changed to a different card here.
pcm.snd_card {
     type hw
     card 0
}

# Allow mixing of multiple output streams to this device
pcm.dmixer {
     type dmix
     ipc_key 1024
     slave.pcm "snd_card"
     slave {
          # This stuff provides some fixes for latency issues.
          # buffer_size should be set for your audio chipset.
          period_time 0
          period_size 1024
          buffer_size 4096
          # rate 44100
     }

     bindings {
          0 0
          1 1
     }
}

# Allow reading from the default device.
# Also known as record or capture.
pcm.dsnooper {
     type dsnoop
     ipc_key 2048
     slave.pcm "snd_card"

     bindings {
          0 0
          1 1
     }
}

# This is what we want as our default device
# a fully duplex (read/write) audio device.
pcm.duplex {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}

###################
# CONVERSION PLUG #
###################
# Setting the default pcm device allows the conversion
# rate to be selected on the fly.
# duplex mode allows any alsa enabled app to read/write
# to the dmix plug (Fixes a problem with wine).

pcm.!default {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}

########
# AOSS #
########
# OSS dsp0 device (OSS needs only output support, duplex will break some stuff)
pcm.dsp0 {
     type plug
     slave.pcm "dmixer"
}

# OSS control for dsp0 (needed?...this might not be useful)
ctl.dsp0 {
     type plug
     slave.pcm "snd_card"
}

# OSS control for dsp0 (default old OSS is mixer0)
ctl.mixer0 {
     type plug
     slave.pcm "snd_card"
}

---

### Post by bdash on 2005-09-13
Well, no it works with nvsound (proprietary OSS driver). However since it is OSS I can't mix sound.

Did anyone manage to use the microphone with an nForce2 chipset and the free ALSA drivers ?

---

