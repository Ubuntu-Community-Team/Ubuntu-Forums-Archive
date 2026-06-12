---
title: "soundcard prob"
date: 2005-07-20
forum: Hardware &amp; Laptops
---

### Post by kurisutofaa on 2005-07-20
At beginning, I installed ubuntu hoary, and everythink work fine. But, now my soundcard broke. So I removed broken soundcard from pci slot. But now I can't get my integrated soundcard work properly. I turned it on from bios settings. I can't get any sound out of my ubuntu (except terminal bell).
my /etc/asound.conf here:

> # Set default sound card
# Useful so that all settings can be changed to a different card here.
pcm.snd_card {
     type hw
     card 1
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

and when I "sudo /etc/inid.d/alsa restart":
> Shutting down ALSA.../etc/init.d/alsa: Warning: 'alsactl store' failed with error message 'alsactl: save_state:1163: No soundcards found...'. failed.
Setting up ALSA.../etc/init.d/alsa: Warning: 'alsactl restore' failed with error message 'alsactl: load_state:1236: No soundcards found...'. done.

When I for example start gedit from terminal, comes this:
> kuriken@ubuntu:~$ sudo gedit /etc/asound.conf
- using device duplex
- using device duplex
ALSA lib pcm_dmix.c:802:(snd_pcm_dmix_open) unable to open slave

gedit works thou...

alsamixer:
> alsamixer: function snd_ctl_open failed for default: No such device


oh mann... I don't want to turn back to windows, after my 7 month travel with ubuntu :(
any chances to get this work? I apperciate your help.

thanks

---

