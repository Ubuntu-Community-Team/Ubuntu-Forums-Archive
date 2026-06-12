---
title: "ubuntu-server + xorg + fluxbox + alsa-base + pulseaudio = no sound"
date: 2008-07-16
forum: Hardware
---

### Post by thespinesplitter on 2008-07-16
hello guys, i am really hoping someone can help me out here with this problem.

i was going for a really lean linux install so i installed the ubuntu hardy server image and i followed by installing xorg, fluxbox, alsa and pulseaudio, the outcome is i cant get any audio out of my PC even if my life depended on it.

all hte packages needed are there except they may not be configured correctly and without alsaconf i dont know how to deal with that.

---

### Post by forger on 2008-07-16
You had sound before or in any Ubuntu release (or with any other kernel image)?
Why did you use the server kernel image?
Is it ubuntu hardy heron? :)

post the output of this:
```
lsb_release -a
uname -a
```

---

### Post by thespinesplitter on 2008-07-16
it is hardy, i said so in my post and sound wasnt an issue with the ubuntu-desktop package installed which i chose not to install for this last linux install i did.
i chose the server image because i need to have the leanest install possible on this laptop with 256MB of ram but if i install the ubuntu-desktop package and its dependencies i might as well do a full install anyway, it is a configuration issue that i dont know how to deal with.


BTW: id like to paste the output but i dont know how to copy&paste with xterm

---

### Post by thespinesplitter on 2008-07-16
~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04
Release:        8.04
Codename:       hardy
~$ uname -a
Linux dahlapt 2.6.24-16-server #1 SMP Thu Apr 10 13:58:00 UTC 2008 i686 GNU/Linux

---

### Post by thespinesplitter on 2008-07-16
this what i get when i try to run #speaker-test

```
speaker-test 1.0.15

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 256 to 2097152
Period size range from 128 to 524288
Using max buffer size 2097152
Periods = 4
was set period_size = 524288
was set buffer_size = 2097152
*** PULSEAUDIO: Unable to create stream.
Unable to set hw params for playback: Input/output error
Setting of hwparams failed: Input/output error
speaker-test: pcm_pulse.c:115: pulse_stop: Assertion `pcm->stream' failed.
Aborted

```

---

### Post by thespinesplitter on 2008-07-16
i guess il just install ALSA from source. that does come with alsaconf still and it should fix my problem.

il let everyone know as soon as i fix the problem so if anyone wants to do the same they can get their sound going  as well

---

### Post by thespinesplitter on 2008-07-16
here is some more info

```
lspci:

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 3091
        Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 16
        Memory at d0003400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
```


```
modprobe -l

snd      56868  16
snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_seq_device,snd_atiixp_modem,snd_pcm_oss,snd_mixer_oss,snd_atiixp,snd_ac97_codec,snd_pcm,snd_timer
soundcore               8800  1 
sndatiixp                  5648  0 [permanent]

```

---

### Post by thespinesplitter on 2008-07-16
so far i think it is a pulseaudio issue since i can play a file with #aplay without it outputting any sound but it still runs and when i try to play a file with #paplay (the pulseaudio version of aplay) it says that the file cannot be opened.

---

### Post by thespinesplitter on 2008-07-16
i think i may just uninstall pulse audio and alsa, do an alsa install from source and go back to using ESD when needed.

---

