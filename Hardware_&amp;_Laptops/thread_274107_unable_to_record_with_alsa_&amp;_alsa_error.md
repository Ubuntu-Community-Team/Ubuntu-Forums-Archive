---
title: "unable to record with alsa &amp; alsa error"
date: 2006-10-09
forum: Hardware &amp; Laptops
---

### Post by KhaaL on 2006-10-09
when I run gstreamer-properties and select alsa for input and press test, i get this messages:

ALSA - Advanced Linux Sound Architecture: Could not open resource for writing.


In console, the following shows:

gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4l2src'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesrc'
gstreamer-properties-Message: Error running pipeline 'ALSA - Advanced Linux Sound Architecture': Could not open resource for writing. [gstalsasrc.c(612): gst_alsasrc_open (): /pipeline0/alsasrc1:
Recording open error on device 'default': Invalid argument]



I got Nforce2 soundcard and I haven't touched any drivers, but am using the one that came along with the install. Help would be *very* appriciated

---

### Post by Megatog615 on 2006-10-25
Bump.
I have this problem.

---

### Post by Blender on 2006-11-09
Sorry, but...
...bump, I have the same problem (nForce4 though, amd64)

---

### Post by Blender on 2006-11-09
Hi!

After searching the net and playing with my .asoundrc for several hours, I found a solution.
Here it is (I have 5.1):

~/.asoundrc (create if it does not exist)
```

pcm.snd_card {
    type hw
    card 0
    device 0
}

# Allow reading from the default device. Also known as record or capture.
pcm.input {
    type dsnoop
    ipc_key 2048
    ipc_key_add_uid yes
    slave.pcm "snd_card"
## Possible artsd full duplex fix:
    slave {
         period_time 0
         period_size 1024
         buffer_size 8192
         rate 48000
    }
    bindings {
         0 0
         1 1
    }
}

pcm.dmixs51 {
    type dmix
    ipc_key 1024
    slave {
        pcm "hw:0,0"
        rate 44100
        channels 6
        period_time 0
        period_size 1024
        buffer_time 0
        buffer_size 4096
    }
}

pcm.duplex {
    type asym
    playback.pcm "dmixs51"
#	slave.pcm "dmixs51"
#	route_policy duplicate
    capture.pcm "input"
}

pcm.!default {
    type plug
    slave.pcm "duplex"
#    slave.channels 6
    route_policy duplicate
}



# OSS dsp0 device (OSS needs only output support, duplex will 
# break some stuff)
pcm.dsp0 {
    type plug
    slave.pcm "output"
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

```

I got the config from [HOWTO ALSA Complete (includes dmix)]("http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix#intel8x0_audio_card_integrated_on_nforce2_motherboards"), section " intel8x0 audio card integrated on nforce2 motherboards"
If you are not using 5.1, then simply using the config from the above site should work.

I have tested it with Skype (Skype being the reason for using mic at all), gnome-sound-recorder and Audacity, which IIRC uses OSS.

I also don't know if this is the best solution (probably not), it's just what works for me!
Hope this helps!

PS: Here's my config in gnome-volume-control (could not attach the files to the thread)
[[IMG]http://img214.imageshack.us/img214/5472/alsamixerscreen1iw2.th.png[/IMG]](http://img214.imageshack.us/my.php?image=alsamixerscreen1iw2.png)
[[IMG]http://img214.imageshack.us/img214/3717/alsamixerscreen2uz8.th.png[/IMG]](http://img214.imageshack.us/my.php?image=alsamixerscreen2uz8.png)
[[IMG]http://img154.imageshack.us/img154/9223/alsamixerscreen3rg5.th.png[/IMG]](http://img154.imageshack.us/my.php?image=alsamixerscreen3rg5.png)
[[IMG]http://img81.imageshack.us/img81/2708/alsamixerscreen4nk6.th.png[/IMG]](http://img81.imageshack.us/my.php?image=alsamixerscreen4nk6.png)

---

