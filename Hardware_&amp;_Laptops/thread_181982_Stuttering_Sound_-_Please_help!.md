---
title: "Stuttering Sound - Please help!"
date: 2006-05-25
forum: Hardware &amp; Laptops
---

### Post by johnnyc on 2006-05-25
Hey guys,

I followed the HOW TO laid out [here]("http://www.ubuntuforums.org/showthread.php?t=44753").
[QUOTE=intangible]I know it's been done before, but I don't think anybody has compiled all the settings into a single happy set of instructions.

This setup should work with most sound systems, it is from my Nforce2 setup at home, it makes everything work quite nicely together, OSS, ESD, ALSA and make your Mic work while sound is playing (great for UT2004!!).

These instructions assume you know how to edit config files on your system and add/remove packages on your own.

[list=1]
[*] Goto **System->Preferences->Sound** and disable "Enable Sound Server Startup"

[*] Install **libesd-alsa0** which will remove libesd0, but that's ok.

[*] Make **/etc/esound/esd.conf** look like this:
```
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
```

[*] Make **/etc/asound.conf** look like this:
```
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
```If you look, the first setting will let you select a different sound card as your primary if you have multiple sound cards.

[*] Make **/etc/libao.conf** look like this:
```
default_driver=alsa
```

[*] Reboot to make sure all the systems startup correctly.
[/list]
OSS stuff will still tie up the sound card, but they don't run all the time.  Just configure most things to use ALSA and you'll be good.

Side-Effect: The Ubuntu startup sounds will go away, but i think the trade-off is worth it.

**Note**: If stuff plays a little static through ESD, in **/etc/esound/esd.conf** try changing
*spawn_options=-terminate -nobeeps -as 2 -d default*
to
*spawn_options=-terminate -nobeeps -as 2 -d duplex*[/QUOTE]

I've noticed that Totem-Xine Player is able to play all matter of media, however, other applications like Soundjuicer/Banshee will produce a stuttering sound when attempting to play audio CDs.

Is there a way to fix this?

---

### Post by Sef on 2006-05-25
Have you installed the codecs?

[RestrictedFormats]("http://wiki.unbuntu.com/RestrictedFormats")

---

