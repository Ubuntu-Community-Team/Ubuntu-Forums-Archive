---
title: "no sound"
date: 2005-10-11
forum: Hardware &amp; Laptops
---

### Post by rgrig on 2005-10-11
After doing some progress by following [these steps]("http://www.ubuntuforums.org/showthread.php?t=19307") I have reached a dead-end. My situation is: no error and no sound. The tool alsamixer says everything is unmuted and with the volume at 71%. Here is some other info:

```

rg@rg-ucd:/home/rg # uname -a
Linux rg-ucd 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686 GNU/Linux
rg@rg-ucd:~$ lspci | grep -i audio
0000:04:02.0 Multimedia audio controller: Creative Labs SB Audigy LS
rg@rg-ucd:~$ lsmod | grep snd
snd_ca0106             26532  3
snd_ac97_codec         67320  1 snd_ca0106
snd_pcm_oss            55712  1
snd_mixer_oss          18048  2 snd_pcm_oss
snd_pcm                91016  3 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_timer              24580  1 snd_pcm
snd                    59780  8 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
snd_page_alloc         10116  2 snd_ca0106,snd_pcm
rg@rg-ucd:~$ cat /dev/urandom > /dev/dsp
bash: /dev/dsp: Device or resource busy
rg@rg-ucd:~$ killall esd
rg@rg-ucd:~$ cat /dev/urandom > /dev/dsp

[1]+  Done                    esd
rg@rg-ucd:~$ aplay /dev/urandom
Playing raw data '/dev/urandom' : Unsigned 8 bit, Rate 8000 Hz, Mono
Aborted by signal Interrupt...

```

No sound at all even thou the headphones are OK and I've tried to plug them in every possible place (just to make sure).

What should I try next?

---

### Post by lifeperfecti0n on 2005-10-11
hi,
I assume u use ubuntu...go to System...Preferences...Multimedia Systems Selector...test the default audio sink...try changing it to alsa if its esd (esd doesn't work on my system) or try changing it to various sinks...try if dis works...btw i THINK u vil hv to killall the default output previously configured b4 changing to some other sink
btw for my system, even though I hv selected alsa as da default source I hv to 'killall esd' on bash to play audio.
another thing is dat u should try changing the vols (chek EVERY knob...I experienced a nearly similar problem in FC2 n it was bcoz PCM-2 vol was down)
Good luck!

---

### Post by rgrig on 2005-10-11
Yes. I forgot to mention that I've tried different output sinks as well. It doesn't work.

---

### Post by j0eb0b on 2005-10-11
After tearing my hair out over the last rainy weekend trying to get sound working on a new unbuntu  build here is what worked for me.  First read and perform the steps in this "how to" found in the "unofficial 5.0.4 guide" on this forum.  It seems that associating the additional repositories in the initial steps is very important.

[http://ubuntuguide.org/#xmms](http://ubuntuguide.org/#xmms)

Although this references XMMS I couldn't get it working.  I then downloaded and installed the beep-player package and after playing with Sink and Source finally got sound from both the CD player and MP3 internet streams.  In my case ESD finally made it play.

Good luck, sound seems to be a real problem on these builds.  The rest works pretty well.

---

### Post by rgrig on 2005-10-12
Now playback works. What I had to do is to switch off -- i.e. mute -- (!!!) "SPDIF Out".

Recording doesn't seem to work yet. It does not work in Skype and Sound Recorder crashes.

---

