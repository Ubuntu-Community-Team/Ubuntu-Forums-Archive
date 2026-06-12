---
title: "[Intrepid] Sound but no microphone in etqw"
date: 2009-04-13
forum: Hardware
---

### Post by red_Marvin on 2009-04-13
This problem is partially solved, look at the third post.

This problem has bugged me for a while, and occurs when playing etqw, the symptoms are as follow:
[list][*]Sound output works fine in etqw, both sounds and music.
[*]Sound recording works fine outside etqw.
[*]If I unmute the microphone channel, I can hear it inside etqw.
[*]The sound does **not** get recorded in etqw.[/list]
I have tried different mixer settings, killing pulseaudio, running etqw prefixed with *pasuspender* or *aoss* and suffixed by *+set s_alsa_pcm "hw:0,0"* but no cigar.
The only change in behaviour is that if I do not disable pulse audio before running, etqw will crash when running the mic test function or using any key that is linked to activating mic input.

Across the board I get the following error that seems related.
```
--------------------------------------
------ Alsa Sound Initialization -----
dlopen(libasound.so.2)
asoundlib version: 1.0.17a
opened Alsa PCM device hw:0,0 for playback
device buffer size: 5472 frames (21888 bytes)
allocated a mix buffer of 16384 bytes
--------------------------------------
[b]-------- ALSA Microphone Init --------
error setting 1 channel / mono: Invalid argument
close mic pcm
WARNING: microphone is diabled
--------------------------------------[/b]
```
I know that the mic has worked previously on older versions of ubuntu.
Suggestions are welcome.

---

### Post by Sef on 2009-04-17
bump per op request.

---

### Post by red_Marvin on 2009-04-18
partially SOLVED
When I followed [this](http://ubuntuforums.org/showthread.php?t=789578) guide the second time around, combined with starting etqw by the method below it worked.
```
#!/bin/bash
#xmodmap -e "keycode 49 = quoteleft asciitilde"
export SDL_VIDEO_X11_DGAMOUSE=0
/usr/local/games/etqw/etqw-rthread +set s_alsa_pcm plughw:0 +set s_numberOfSpeakers2 "$@"
#xmodmap -e "keycode 49 = section onehalf"
```
(The commented stuff is not crucial to sound, but other things I use)

Further testing shows that this is not all, when the game starts, sound works, but upon joining a server the microphone dies again.
As soon I try to use voip in etqw the terminal starts putting out this error: *snd_pcm_readi failed: Broken pipe*

---

