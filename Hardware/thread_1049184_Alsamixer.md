---
title: "Alsamixer"
date: 2009-01-24
forum: Hardware
---

### Post by addyyy on 2009-01-24
I have a dell mini inspiron with factory installed 8.04.1 I cannot get the internal microphone to work.  Whne i type alsamixer in terminal i get a screen that says 
card HDA Intel
Chip Realtek ALC268
View [playback] Capture all
Item Master [db gain=-11.00]

All the bars have volume levels
master 83
headphone 75
pcm 95
mic boost 100
Internal is at 0 and i cant find anywhere to increase it etc
Speaker 92
Can any one help
Thanks

---

### Post by linux_tech on 2009-01-24
install gnome-alsamixer, its easier to use

```

sudo apt-get install gnome-alsamixer

```
open gnome-alsamixer

```

gnome-alsamixer

```

---

### Post by linux_tech on 2009-01-24
then adjust capture slider, make sure rec is checked

---

### Post by addyyy on 2009-01-24
That didnt work command not recognized by system gnome-alsamixer

---

### Post by linux_tech on 2009-01-24
You have to install it first

---

### Post by linux_tech on 2009-01-24
what is output of :
```

cat /proc/asound/card0/codec#* | grep Codec


```

---

### Post by Lunx on 2009-01-27
> **addyyy said:**
> That didnt work command not recognized by system gnome-alsamixer

Have you tried installing using Synaptic? Open Synaptic and type alsamixer or gnome-alsamixer into it and you should see it there. I only just found and installed it a few minutes ago 'coz I couldn't get enough volume out of this box. Once Synaptic does its magic you'll be able to find it in the menu Applications >Sound and Video 

(I'm running 8.10, and I'm a complete Ubuntu/Linux noob of three weeks standing, so haven't yet looked at other versions to see if above method works in earlier distros)

---

### Post by macabro22 on 2009-02-11
This worked for me:
> create a ~/.asoundrc file in your home directory such as this one:

    pcm.loudmic {
        type asym
        capture.pcm {
            type softvol
            slave.pcm "hw:0,0"
            control {
                name "Mic Boost"
                card 0
            }
            max_dB 20.0
        }
    }

You will get a shiny new "Mic Boost" control in the mixer preferences, and if
you select "loudmic" as your input source in Skype, the sound will be
accordingly amplified.. And check the threads on launchpad for other fun tricks

ALSA and Pulse are buggy buggy... please someone acknowledge that ALSA and
PulseAudio have too many _severe_ bugs :) And please let us know how we can
help the ALSA and Pulse teams to fix all these problems :) Thank you

I got it from here: [https://bugzilla.redhat.com/show_bug.cgi?id=474477](https://bugzilla.redhat.com/show_bug.cgi?id=474477)

---

